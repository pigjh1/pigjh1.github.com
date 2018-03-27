---
bg: "tools.jpg"
layout: post
title: "css그리드로 Masonry 스타일 만들기"
date: 2018-03-27 16:56:00
categories: posts
tags: ['css', 'grid']
---

[Masonry](https://masonry.desandro.com/) 스크립트를 사용하기 싫어서 css만으로 할 수 있는 방법을 찾아 유형별로 특이사항을 정리해보았다.

### 방법1
- [Creating a CSS-only Responsive Masonry](http://w3bits.com/css-masonry/)
- css grid 속성으로 쉽게 할수 있지만 아이템 순서가 문제가 있다.
- 순서가 좌에서 우로 가는게 아니라 위에서 아래로 배치된다.
- [stackoverflow](https://stackoverflow.com/questions/44377343/css-only-masonry-layout-but-with-elements-ordered-horizontally/45200955)에 현상에 대한 질문이 올라와 있다.
- 결론적으로 순서 상관 없는 이미지 타입의 아이템을 배치할때는 좋다.
```css
.masonry { /* 부모 */
    column-count: 4;
    column-gap: 1em;
}
.item { /* 아이템 */
    display: inline-block;
}
```

### 방법2
- [Masonry style layout with CSS Grid](https://medium.com/@andybarefoot/a-masonry-style-layout-using-css-grid-8c663d355ebb)
- 스크립트 사용해서 정렬 맞추는 방법이다.
- grid-row에 span으로 높이값을 준다
- [jsfiddle 예제](https://jsfiddle.net/q5e20knd/15/)를 보면 원리(?)를 알수 있다.
```css
.item {
    grid-row: span 2;
}
```

### 정형 item 일때
- [True Masonry with Grid Layout](https://codepen.io/balazs_sziklai/pen/mOwoLg)
- 방법2와 같이 너비 높이를 지정해주는 방법으로 하면 된다.
