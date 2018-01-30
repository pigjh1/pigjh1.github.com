---
bg: "tools.jpg"
layout: post
title: "잘 모를수도 있는 css"
date: 2017-10-26 12:46:00
categories: posts
tags: ['css']
---

### shapes
- http://webplatform.adobe.com/shapes/
- https://tympanus.net/codrops/css_reference/shape-outside/
- http://alistapart.com/article/css-shapes-101

### CSS clip 과 clip-path
https://css-tricks.com/clipping-masking-css/

clip은 css2 clip-path는 css3로 현재는 ie지원이 안됨

1. The Old/Deprecated clip
- http://www.psyonline.kr/1232032355
- https://developer.mozilla.org/ko/docs/Web/CSS/clip
- http://bennettfeely.com/clippy/

2. The New clip-path
- https://www.html5rocks.com/en/tutorials/masking/adobe/

### Blend Modes
브라우저 지원때문에 잘 사용하지 않던 스타일
포토샵에 multiply 효과 등 지원하는 브라우저에서는 스타일을 보이도록 사용
- [Basics of CSS Blend Modes](https://css-tricks.com/basics-css-blend-modes/)
- [Image Effects with CSS](http://bennettfeely.com/image-effects/)

---

### CSS Level 4
- [Intriguing CSS Level 4 Selectors](https://webdesign.tutsplus.com/tutorials/intriguing-css-level-4-selectors--cms-29499)
- [font-variation-settings](https://developer.mozilla.org/en-US/docs/Web/CSS/font-variation-settings)
- [font-display](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display)
- [CSS font-display: The Future of Font Rendering on the Web](https://www.sitepoint.com/css-font-display-future-font-rendering-web/)

---

### 리셋을 위한 스타일들

#### 아이폰(IOS)에서 input 버튼 라운딩
```
input[type=image] {
  -webkit-appearance: none;
  -webkit-border-radius: 0;
}
```

#### 텍스트 antialias
http://maxvoltar.com/archive/-webkit-font-smoothing
```
html { -webkit-font-smoothing: antialiased; }
```

#### input search IE에서 x버튼 디자인에 따라 중복되어 보여질 수 있음
```
input[type="search"]::-ms-clear { display: none; }
```

#### 테이블 작업시 IE7에서 내용이 없는 부분에 border값 표시가 안되는 경우
```
table { border-collapse:collapse }
```

---

### Reference
- [당신은 모를 수도 있는 CSS의 7가지 단위](https://webdesign.tutsplus.com/ko/articles/7-css-units-you-might-not-know-about--cms-22573)
