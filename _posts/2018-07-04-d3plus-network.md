---
bg: "tools.jpg"
layout: post
title: "D3plus Network Graph 개발 후기"
date: 2018-07-04 11:41:00
categories: posts
tags: ['d3']
---

오래전부터 좋아하던 일본소설 작가의 독특한 세계관이 있었는데 데이터 시각화를 해보고 싶었다.  
작품이 워낙 많고 연결점도 많아서 어떻게 그려야 할지 감이 잘 오지 않았다.  
쉽게 이야기하면 인물 관계도 같은 것인데 코드로는 표현의 제약이 있으니 PSD나 스케치, 키노트 같은 도구를 이용할까도 싶었지만, 수정/추가가 불편한 것 같아 작업을 해보게 되겠다.  

우선은 [D3의 Force Layout](https://bl.ocks.org/mbostock/1093130)를 이용해서 마인드맵과 같은 형태로 그리려고 [vue에서 D3를 사용한 예제](https://bl.ocks.org/ravi4j/0529296064dd32ba14e5907264f9e8f4)도 찾았다.  
svg로 그려진 원형 안에 text가 들어가는 형태가 되어야 하는데 그러기 위해서는
`<text>Hierarchical Cluster</text>`가
`<text><tspan>Hierarchical</tspan><tspan>Cluster</tspan></text>` 처럼 `<tspan>`로 감싸주어야 했다.  

그래서 검색하다 나온 것이 [D3plus의 SVG Text Wrapping 예제](https://d3plus.org/examples/utilities/a39f0c3fc52804ee859a/)였다.  
D3plus는 D3를 확장한 라이브러리다.  
예제를 살펴보다가 Network Graph가 내가 그리고 했던 것 표현할 수 있을 것 같아 적용해보았다.  

### 단계별
#### 1단계. 버전 확인하기
2.0 버전이 곧 나올 거라고 하고 예제도 2.0버전으로 제공되어 있었는데 svg가 그려질 컨테이너를 지정할수 없었다.  
그래서 1.9.8버전을 사용했고 d3의 경우는 3.5.15버전을 사용했다.  
d3의 경우도 버전이 다르면 사용하는 메소드가 달라서 애를 먹었던 기억이 난다.  

```javascript
<script src="https://cdn.bootcss.com/d3/3.5.15/d3.js"></script>
<script src="https://cdn.bootcss.com/d3plus/1.9.8/d3plus.js"></script>
```

그려지는 형태를 확인하기 위해서 일부 데이터만 포맷에 맞게 집어넣으니 꽤나 만족스러운 그래프가 나왔다.  

<img src="https://pigjh1.github.io//assets/images//2018-07-04/step1.png" alt="" width="500">

#### 2단계. 형식에 맞게 데이터 정리하기
d3의 Force Layout은 `nodes`를 그리는 변수와 노드들은 연결하는 `links`변수가 필요했다.  
노드들을 연결해주는 links값을 작성하는게 꽤 큰일이였다.  
데이터를 직관적으로 보이는 값으로 두고 가공해서 사용하는 처리도 필요했다.  

```json
{
    "nodes": [
        { "id": "Alice" },
        { "id": "Bob" },
        { "id": "Carol" }
    ],
    "links": [
        { "source": 0, "target": 1 },
        { "source": 1, "target": 2 }
    ]
}
```

d3plus의 경우도 nodes와 link가 기본적으로 필요했는데 연결되는 방식이 좀 더 편했다.  
아래 json에 sources와 targets를 `concat 메소드`로 합쳐서 nodes로 만들었다.  
links는 node들의 연결리스트를 나열했다.  

```json
{
    "sources": [
        { "id": "source1" ,"name": "Alice" },
        { "id": "source2" ,"name": "Bob" }
    ],
    "targets": [
        { "id": "target1", "name": "Food" },
        { "id": "target2", "name": "Beer" }
    ],
    "links": [
        { "target": "target1", "source": "source1", "label": "" },
        { "target": "target1", "source": "source3", "label": "" }
    ]
}
```

실제로 작업한 데이터를 예로 들면

- sources: 도서명 (e.g. 오듀본의 기도, 러시라이프)
- targets: 연결포인트 (e.g. 이토, 선술집 덴덴, 시장살인 사건 등 등장인물이나 장소, 사건)
- links: 연결점 (e.g. 이토는 오듀본의 기도에도 등장하고 러시라이프에도 등장한다.)

이 과정에서 힘들었던 건 데이터의 양이 많았고 최종 데이터가 아니라 추가 업데이트를 해야한 데이터라는 점이다.  
도서는 30여 개, 연결포인트는 40여 개, 연결점은 100가지 넘었다.  
<s>(이렇게 작품 연결점이 많고 세계관이 복잡한게 이 작가를 좋아하는 매력인데 그 세계관을 그리는 게 역시나 쉽지 않는 일이다.)</s>
연결포인트의 경우는 등장인물, 장소, 사건 등으로 또 분류가 될수 있는데 이것까지 분류해서 그리기는 힘들것 같아서 우선은 2가지 종류로 제한을 하였다.  

<img src="https://pigjh1.github.io//assets/images//2018-07-04/step2.png" alt="" width="500">

데이터를 정리하고 실행을 해보니 노드들 간의 간격이 너무 멀어서 보기 불편했다.  
새로고침을 할때마다 위치가 다르게 나오는데 특정 데이터만 멀게 떨어져서 보여서 데이터의 문제인가 싶어서 삭제해봤는데도 다른 데이터가 문제가 되었다.  
텍스트의 길이, 노드간의 연결들을 보고 위치를 자동으로 정해주는 것 같다.  
노드에 사이즈를 지정할수 있었는데 sources의 경우 2, targets를 1로 지정했다. 100, 1로 해도 원의 사이즈는 같았다.  

#### 3단계. 상세 설명 출력하기
원래의 의도는 도서명과 연결포인트가 라인으로 연결이 되고 그 위에 꾸밈말 형식으로 텍스트를 삽입하고 싶었다.  
`edges()` 메소드 `label`로 값을 넣어주면 됐는데 문장이 너무 길다보니 넣을 수가 없었다.  
그래서 원래하던 방식대로 텍스트를 전체 내용을 나열해주었다.  
이 부분도 추가 개발이 필요한데 텍스트의 나열이다보니 사용자가 보기 불편한게 사실이다.  
노드를 클릭하면 툴팁이 보여지고 해당 노드가 확대되어 보여지는게 이 그래프가 마음에 드는 점이었는데, 클릭할 때 콜백함수를 부를수 있으면 그때 해당하는 텍스트를 보여지게 처리할 수 있을 것 같다.  
툴팁의 경우 size나 Primary Connections같이 보이는 메세지는 보여주지 않거나 문구를 바꾸고 싶었는데 기능 없어서 css로 숨김처리 했다.  

<img src="https://pigjh1.github.io//assets/images//2018-07-04/step3.png" alt="" width="500">

#### 4단계. 위치값 지정하기
노드에 x,y 값을 붙여서 위치를 지정할수 있었다.  
처음에는 for문을 돌려서 일정한 간격만큼을 띄어서 배치될수 있게 했는데, 도서의 경우 시리즈물이나 비슷한 분위기의 작품끼리 배치 하고 싶었다.  
그래서 도서명의 경우 한땀한땀 x,y 값을 넣어주었다.  
위치값을 지정하지 않으면 links로 연결되지 않는 nodes는 보이지 않는데 값을 지정하니 보였다.  
연결점이 없는 도서의 경우 바닥쪽에 배치하였다.  
열에 맞춰서 요소들이 있는 느낌이라 뭔가 부자연스러운 느낌이 있어서 위치를 재지정할 필요가 있어 보인다.  

<img src="https://pigjh1.github.io//assets/images//2018-07-04/step4.png" alt="" width="500">
<img src="https://pigjh1.github.io//assets/images//2018-07-04/step-2.png" alt="" width="500">

#### 5단계. 색상 지정하기
이대로 공개를 해도 꽤 좋지 않을까 하고 마감을 했는데 홈페이지에 끼워넣으려고 하니 색상이 걸린다.  
그래서 도서의 경우는 호버 효과를 주기위해서 고유 색상을 지정해 둔게 있어서 그 색상값을 지정해두었다.  
<s>도서 유형을 분류한다고 순서를 바꿔두어서 한번에 촥 바꾼게 아니라 한땀한땀 값을 넣어두는 바보짓을 했다.</s>
<s>고유 색상값을 지정할때 대충 컬러픽커를 써서 값을 찍은거라 색상도 재확인을 해야한다.</s>
이것도 꽤 괜찮아서 이대로 정말 마감을 하였다.  
<s>그런데 글을 작성하다 보니 개선해야 할 부분이 더 필요해 보인다.</s>

<img src="https://pigjh1.github.io//assets/images//2018-07-04/step5.png" alt="" width="500">

### 구현하지 못해서 아쉬운 부분. 추가로 작업할 것
- 자연스러운 그래프가 될수 있게 요소들의 위치를 재지정
- 드래그 드롭으로 요소들은 컨트롤
- 연결포인트를 등장인물, 장소, 사건으로 추가 분류
- 작품과 작품사이의 연결점 표시
- IE와 모바일 디바이스에서 최적화 작업 (중요!)
- 인쇄용 버전에 대한 고민

결과적으로 완벽하게 원하는 형태는 아니었지만 투자한 시간대비 만족할 만한 결과가 나온 것 같다.  
d3plus의 Network Graph는 멋지고 필요에 따라 잘 활용하면 좋겠다.  

---

D3에 대해서 잘 알지도 못하고 설명도 잘 못해서 같아서 글쓰는 과정 매우 힘들었다.  
나만 알아볼수 있는 글이라 이 글이 누군가에 도움이 될지는 모르겠으나 일련의 과정을 정리해보고 싶었다.  
소스를 더 다듬고 추가로 작업할 부분도 있어서 전체소스나 링크 공개는 할수 없다.  
공개링크가 나오는대로 포스팅을 수정할 예정이다.  

---

### 참고링크
- [D3plus examples](http://d3plus.org/examples/)
- [Simple Network Graph](http://d3plus.org/examples/d3plus-network/getting-started/)
- [Automatic Node Positions in Network](http://d3plus.org/examples/advanced/9956648/)
- [Customize D3plus network style](https://codepen.io/choznerol/pen/evaYyv) : 🙌 도움이 많이 된 예제
- [SVG Text Wrapping](https://jsfiddle.net/IPWright83/22ahj15o/)
