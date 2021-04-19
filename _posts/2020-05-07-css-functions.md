---
bg: "tools.jpg"
layout: post
title: "CSS 함수"
date: 2020-05-05 10:45:00
categories: posts
tags: ['css']
---

css-tricks에 소개된 내용 요약
- https://css-tricks.com/complete-guide-to-css-functions/

### Basics of CSS Functions
![img](https://i2.wp.com/css-tricks.com/wp-content/uploads/2020/04/LV2OI0TM.png?resize=1000%2C325&ssl=1)

### Common CSS Functions
- url()
- attr()
- calc()
- lang()
- :not()

### CSS Custom Properties
- var()

### Color Functions
- rgb() and rgba()
- hsl() and hsla()

### Pseudo Class Selectors
- :nth-child()
- :nth-last-child()
- :nth-last-of-type()
- :nth-of-type()

### Animation Functions
- cubic-bezier()
- path()
- steps()

### Sizing and Scaling Functions
- scaleX(), scaleY(), scaleZ(), scale3d(), and scale()
- translateX(), translateY(), translateZ(), translate3d(), and translate()
- perspective()
- rotateX(), rotateY(), rotateZ(), rotate3d(), and rotate()
- skewX(), skewY(), and skew()

### Filter Functions
- brightness()
- blur()
- contrast()
- grayscale()
- invert()
- opacity()
- saturate()
- sepia()
- drop-shadow()
- hue-rotate()

### Gradient Functions
- linear-gradient() and repeating-linear-gradient()
- radial-gradient() and repeating-radial-gradient()
- conic-gradient() and repeating-conical-gradient

### Grid Functions
- fit-content()
- minmax()
- repeat()

### Shape Functions
- circle()
- ellipse()
- inset()
- polygon()

### Miscellaneous Functions (기타)
- element()
- image-set()
- ::slotted()

### Not Ready for Prime Time (준비중)
- annotation()
- counter() and counters()
- cross-fade()
- dir()
- env()
- has()
- image()
- Trigonometry functions - sin(), cos(), tan(), acos(), asin(), atan(), atan2(), sqrt(), hypot(), pow()
- clamp()
- :host() and :host-context()
- max() and min()
- :nth-col() and :nth-last-col()
- symbols()

### 더 이상 사용되지 않는 함수
레거시 지원 이유로 브라우저에서 계속 렌더링 될 수 있지만 앞으로는 사용하지 않는 것이 좋습니다.

- matrix() and matrix3d()
- rect()
- target-counter(), target-counters(), and target-text()
- Typography - format(), leader(), local(), ornaments(), swash()
