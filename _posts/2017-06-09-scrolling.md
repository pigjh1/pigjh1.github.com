---
bg: "tools.jpg"
layout: post
title: "스크롤 페이지"
date: 2017-06-09 11:26:00
categories: posts
tags: ['scrolling']
---

최근 스크롤이 길거나 무한한(Infinite scrolling) 웹사이트가 점점 더 많아지고 있습니다.
이런 페이지를 만들때 고려해봐야 할 내용들을 정리해보았습니다.

### 용어
- One Page Site : 단일 페이지로 구성된 사이트
- Infinite Scroll (인피니트 스크롤) : 스크롤링이 무한대로 되는 스타일
- Parallax Scroll (패럴랙스 스크롤) : 스크롤링 크기를 엘리먼트들에 다르게 주는 기법을 사용한 디자인

### 스크롤이 긴 페이지와 SEO
`history.pushState()`를 사용하여 스크롤이 될때마다 주소를 변경할 수 있습니다.

- [Parallax Scrolling Websites and SEO - A Collection of Solutions and Examples](https://moz.com/blog/parallax-scrolling-websites-and-seo-a-collection-of-solutions-and-examples)
- [SEO optimization for Parallax Scrolling Websites](http://www.awwwards.com/seo-optimization-for-parallax-scrolling-websites.html)
- [SEO-Friendly Infinite Scroll](http://www.sitepoint.com/seo-friendly-infinite-scroll/)
- [On Infinite Scroll, pushState and SEO](https://builtvisible.com/on-infinite-scroll-pushstate/)
- [Changing the browser-URL by scrolling down](http://forums.asp.net/t/2042240.aspx?Changing+the+browser+URL+by+scrolling+down+)
- [Using the HTML5 History API](https://css-tricks.com/using-the-html5-history-api/)

### 길고 긴 페이지를 디자인하는 방법
[smashingmagazine](https://www.smashingmagazine.com/2017/05/long-scrolling/)에 글을 요약해 보았습니다.

#### 언제 사용하는게 좋을까?
- 스토리텔링 (스토리텔러가 활용할 수 있는 선형 구조)
- 긴 기사, 다단계 자습서와 같은 연속적이고 긴 내용의 경우
- 콘텐츠를 별도의 부분으로 나눌수 없을 떄
- 스토리에 있는 제품의 기능, 품질, 속성을 강조 표시할 경우

#### 어떻게 만들어야 할까?
##### 1. 사용자가 스크롤을 할수 있도록 유도
페이지가 로드되는 즉시 보이는 콘텐츠를 잘 만들어라

##### 2. 경로를 탐색할수 있게 네비게이션을 제공해라
현재 위치와 다른 경로를 필요로 한다. sticky menu
모바일 장치의 경우 화면이 좁기 떄문에 스크롤 할때만 스크롤을 보이게 할수 있다.

##### 3. "뒤로" 버튼이 제대로 작동하는지 확인

##### 4. 스크롤 위치에 따라 URL을 변경해라
`history.pushState()`를 사용

##### 5. 섹션 이동하기 옵션을 제공해라

##### 6. 새로운 내용을로드 할 때 시각적 피드백을 제공

##### 7. Don’t Hijack Scrolling
하이재킹 스크롤링을하는 웹 사이트는 스크롤링을 제어하고 웹 브라우저의 기본 기능을 무시합니다.
[Mac Pro page](https://www.apple.com/mac-pro/)가 그러하다.

##### 8. 페이지로드 시간 최적화 링크 최적화

##### 9. 얼마나 많은 자원을 소비하는지 알아보십시오.
긴 스크롤 (특히 많은 이미지와 애니메이션이있는 페이지의 경우)을 사용하는 경우 페이지에서 소비하는 리소스 (CPU 및 메모리)의 양을 항상 고려하십시오.

##### 10. 페이지 링크에서 사용자 행동주의
긴 스크롤이 얼마나 효과적인지 확인하려면 사용자가 스크롤하는 방법을 찾으십시오.
예를 들어, Google 애널리틱스에서 페이지 분석을 열면 스크롤해야 볼 수있는 부분 아래에서 클릭 수를 확인할 수 있습니다.

#### E-Commerce
- 메뉴와 필터를 스티키로 제공
- 나중에 참조 할수 있도록 즐겨찾기 기능 제공
- 총 항목 수는 카테고리 제목 아래 표시
- 접근성 있는 링크 만들기

#### Parallax Scrolling Page
- 사용자가 명확한 작업 (예. 제품구매)를 할때는 사용하지 마라.
- 성능 고려 (translate3d, scale, rotation, opacity)
- 접근성 고려 [toggle switch](https://codepen.io/nattarnoff/pen/JoMxpK)
