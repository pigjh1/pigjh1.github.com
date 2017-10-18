---
bg: "tools.jpg"
layout: post
title: "CSS Flexbox"
date: 2017-01-23 12:00:00
categories: posts
tags: ['css', 'flexbox']
---

### Flexbox는 무엇인가요?
- flex란 유연성을 뜻하는데 유연한박스로 요소들을 자유자제로 위치시킬수 있는 css3에서 추가된 속성입니다.
- 과거 문법 display: box(old)와 같이 사용되다가 비공식적인 문법으로 `display: flexbox(hybrid)`와 같이 사용되었습니다.
- 근래에 명세에는 `display: flex(modern)`가 되었습니다.

### 핵심 단어
- Flex container : `display: flex`를 설정한 부모 요소
- Flex items : 플렉스 컨테이너 내 자식 요소

### Flex container 속성
- flex-direction : 수직, 수평 방향
	- value: row, row-reverse, column, column-reverse
	- https://www.w3.org/TR/css-flexbox-1/#propdef-flex-direction
- flex-wrap : 줄바꿈
	- value: nowrap, wrap, wrap-reverse
		- nowrap 한줄에 표현
	- https://www.w3.org/TR/css-flexbox-1/#propdef-flex-wrap
- flex-flow : flex-direction과 flex-wrap의 약식표현
	- example
		- div { flex-flow: row; }
		- div { flex-flow: column wrap; }
		- div { flex-flow: row-reverse wrap-reverse; }
	- https://www.w3.org/TR/css-flexbox-1/#propdef-flex-flow
- justify-content : 정렬 (text-align과 같은)
	- value: flex-start, flex-end, center, space-between, space-around
	- 시작점 주축, 마지막지점 주축, 주축을 따라 중심에
	- 아이템간 동일한 공간 유지, 항목간 같은 간역 유지
	- https://www.w3.org/TR/css-flexbox-1/#justify-content-property
- align-items : 정렬 (vertical-align과 같은)
	- value: flex-start, flex-end, center, baseline, stretch
		- stretch : 기본. 아이템을 늘려서 전체 높이를 채울 수 있도록
		- baseline : flex item들의 인라인요소(텍스트)들이 같은 라인으로 정렬
	- https://www.w3.org/TR/css-flexbox-1/#propdef-align-items
- align-content : 라인이 두줄 이상일 경우 라인들의 세로정렬 속성
	- value: flex-start, flex-end, center, space-between, space-around, stretch
	- https://www.w3.org/TR/css-flexbox-1/#propdef-align-content

### Flex items 속성
- order : 순서지정
	- https://www.w3.org/TR/css-flexbox-1/#propdef-order
- align-self : 정렬
	- align-items 와 유사
	- value: auto, flex-start, flex-end, center, baseline, stretch
	- https://www.w3.org/TR/css-flexbox-1/#propdef-align-self
- flex-grow : item들이 차지할 너비들에 대한 증가형 숫자를 지정
- flex-shrink : item들이 차지할 너비들에 대한 감소형 숫자를 지정
- flex-basis : item의 길이를 지정
- flex : flex-grow, flex-shrink, flex-basis 속기
	- .item { flex: flex-grow [flex-shrink] [flex-basis]; }
	- https://www.w3.org/TR/css-flexbox-1/#propdef-flex

### IE에서 어떻게 하나요?
- IE9에서는 지원하지 않습니다. http://caniuse.com/#feat=flexbox
- modernizr 사용 https://modernizr.com/download?setclasses&q=flex
```CSS
.no-flexboxlegacy .box { color: red; }
.flexboxlegacy .box { color: green; }
```
```javascript
if (Modernizr.flexboxlegacy) {
	// supported
} else {
	// not-supported
}
```
- [flexibility]( https://github.com/jonathantneal/flexibility) : Flexible Box 사용가능하게 해주는 스트립트

### Playground 👍
- Flexbox playground : http://codepen.io/enxaneta/pen/adLPwv
- flexboxfroggy : http://flexboxfroggy.com/
- flexyboxes : http://the-echoplex.net/flexyboxes/
- https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/
- http://bennettfeely.com/flexplorer/

### Reference
- http://www.w3.org/TR/css-flexbox-1/
- Understanding Flexbox: Everything you need to know 👍
    (medium)[https://medium.freecodecamp.com/understanding-flexbox-everything-you-need-to-know-b4013d4dc9af#.jxrbw619x]
    (github)[https://github.com/ohansemmanuel/Understanding-Flexbox]
    (PDF)[https://ohansemmanuel.github.io/uf_download.html]
- (A Complete Guide to Flexbox 👍)[https://css-tricks.com/snippets/css/a-guide-to-flexbox/]
- (A Visual Guide to CSS3 Flexbox Propertiesproperties)[https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties]
- (CSS Reference Flexbox)[https://tympanus.net/codrops/css_reference/flexbox/]
- (CSS Flexbox Examples)[https://umaar.github.io/css-flexbox-demo/]
- (CSS 레이아웃을 배웁시다 - flexbox)[http://ko.learnlayout.com/flexbox.html]
- (CSS Flex 속성)[http://webdir.tistory.com/349]
- (다룸 flexbox http://daumui.tistory.com/44]
- (IE10의 플렉스박스 레이아웃)[https://msdn.microsoft.com/library/hh673531(v=vs.85).aspx]
- (CSS Flexbox Layout105-minute CSS Course)[https://teamtreehouse.com/library/css-flexbox-layout]
- (align-item과 justify-content 속성)[http://astrap.tistory.com/54]
- (Solved by Flexbox 👍)[https://hyunseob.github.io/solved-by-flexbox-kr/]
- (Advanced Cross-Browser Flexbox)[https://dev.opera.com/articles/advanced-cross-browser-flexbox/]
- (Using Modernizr with Flexbox)[http://zomigi.com/blog/using-modernizr-with-flexbox/]
- (sass-flex-mixin)[https://github.com/mastastealth/sass-flex-mixin]
- (Flexbox SASS mixin w/ Browser List)[https://codepen.io/jreid/pen/jCrBv]
- (The Ultimate Guide to Flexbox — Learning Through Examples :https://medium.freecodecamp.org/the-ultimate-guide-to-flexbox-learning-through-examples-8c90248d4676]

