---
bg: "tools.jpg"
layout: post
title: "줄바꿈 처리와 말줄임 처리"
date: 2017-09-22 19:26:00
categories: posts
tags: ['css', 'text']
---

### 줄바꿈 처리
텍스트가 정해진 너비의 영역을 넘어가게 되면 이를 해결하기 위해 줄바꿈 처리를 해야합니다.
언어별 한/영 조합에서 가장 좋은 방법으로 아래 스타일을 사용하고 있습니다.

```css
.break-word {
    word-break: keep-all;
    word-wrap: break-word;
}
```

#### IOS에서의 줄바꿈 문제
위에 소개한 스타일을 적용을 해도 IOS에서 줄바꿈이 정상적으로 되지 않는 문제가 발견되었습니다.
[2013년에 올라온 글](https://coolestguidesontheplanet.com/stop-hyphens-css-ios-mobile-safari-iphones/)을 보면 `hyphens` 스타일을 사용하지 않고 `word-break`로 단어 단위의 줄바꿈을 할 수 있다고 기뻐하고 있습니다.
[애플공식사이트](https://www.apple.com/)에서는 한글도 줄바꿈이 잘되고 있습니다.
왜 공식사이트는 잘 되는데 내가 만든사이트는 안 되는 걸까요?

몇 가지 테스트 결과를 보면...
1. 문서의 언어설정(`<html lang="ko">`)이 한글이 아니면 줄바꿈이 된다.
2. 폰트에 따라 줄바꿈이 되는 경우가 있다. (주로 기본 폰트: Helvetica Neue, Helvetica, Arial)

정확한 원인을 파악하지 못하고 hyphens속성을 추가해 줄바꿈 처리를 해주었습니다.
```css
.break-word {
    -webkit-hyphens: auto;
}
```
(문제가 발생하는 원인과 다른 해결 방법을 알고 계신다면 공유 부탁드립니다.)

#### 그럼 hyphens 속성은 무엇인가요?
영어와 같이 대소문자 구문이 있는 언어에서 줄바꿈으로 인해 단어가 분리될 때 자동으로 하이픈(-)을 삽입하는 속성입니다.
[hyphens](http://caniuse.com/#search=hyphens)는 IE10이상 부터 사용할 수 있기 때문에 크로스 브라우징 이슈가 있습니다.
포토샵에서 Paragraph 패널에서 Hyphenate 체크 해제해주면 PSD에서도 하이픈이 표시 되지 않습니다.

![포토샵에서 Paragraph 패널에서 Hyphenate 체크 상태 일떄](https://trevellyan.biz/wp-content/uploads/2012/02/2.jpg)
(출처 : trevellyan)

##### hyphens 속성 참고
- [https://developer.mozilla.org/ko/docs/Web/CSS/hyphens](https://developer.mozilla.org/ko/docs/Web/CSS/hyphens)
- [https://css-tricks.com/almanac/properties/h/hyphenate/](https://css-tricks.com/almanac/properties/h/hyphenate/)

#### 단어별 줄바꿈 하는 다른 방법
##### 1. 단어 사이를 `<span>`으로 묶어서 스타일 제어
정확히 단어별 줄바꿈이 되지만, 불필요한 마크업이 생기게 됩니다. 수동으로 할수도 있지만 공백을 판단해서 스크립트로 자동으로 묶을 수도 있겠지요.
```css
.break-word sapn {display: inline-block;}
```

```html
<p class="break-word"><span>청춘에서만</span> <span>모래일뿐</span> <span>방지하는</span> <span>시들어</span> <span>있음으로써</span> <span>소금이라</span> <span>밝은</span> <span>쓸쓸하랴?</span></p>
```

##### 2. font-size를 vw 단위를 사용
폭이 좁아질수록 글씨가 작아지기 때문에 정해진 길이에만 적용하는게 좋습니다.
[브라우저지원](http://caniuse.com/#search=vw)도 확인해 주셔야 합니다.

```css
h1 { font-size: 5vw; }
p { font-size: 3vw; }
```
```html
<h1>청춘에서만 모래일뿐</h1>
<p>방지하는 시들어 있음으로써 소금이라 밝은 쓸쓸하랴?</p>
```

#### 테이블 글자가 밀려요
스페이스가 없이 텍스트가 입력되었을 때 텍스트가 밀리는 경험을 종종하곤 합니다.
테스트 데이터를 입력할때 무의미한 단어를 붙여 넣어 발생하기도 하지만, 엄청 긴 url을 입력하는 경우가 있어 스타일을 지정해주는게 좋습니다.

```css
table {width: 100%;}
table td {word-break: break-all;}
```

### 말줄임 처리
IE, 파이어폭스는 말줄임(…) 표시가 안됩니다.


### 테스트 소스 (codepen)
관련 테스트 파일은 아래에서 확인할 수 있습니다.  
[https://codepen.io/Diana-iropke/pen/GMZGqM?editors=1100](https://codepen.io/Diana-iropke/pen/GMZGqM?editors=1100)

### Reference
- [https://www.w3.org/TR/css-text-3/(https://www.w3.org/TR/css-text-3/)]
- [언어별 CSS 줄 바꿈 설정 테스트](https://codepen.io/naradesign/pen/Evadoy)
- [word-break 속성과 word-wrap 속성 알아보기](http://wit.nts-corp.com/2017/07/25/4675)
- [Responsive multiline ellipsis SASS mixin](http://codepen.io/sergeysemashko/pen/jFGJD)
- [CSS 말줄임 처리의 브라우저 호환성 문제](http://nuli.navercorp.com/sharing/blog/post/37677)
- [CSS String Truncation with Ellipsis](http://mattsnider.com/css-string-truncation-with-ellipsis/)
- [CSS3 text truncation and ellipses](http://sharonminsuk.com/blog/2010/07/22/css3-text-truncation-and-ellipses-even-in-firefox-and-without-the-styling-constraints/)
