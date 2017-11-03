---
bg: "tools.jpg"
layout: post
title: "달력으로 표현한 예약 UI 개발 후기"
date: 2017-11-03 11:27:00
categories: posts
tags: ['javascript', 'jquery', 'jqueryui', 'calendar']
---

프로젝트에서 [jQuery UI Datepicker](https://jqueryui.com/datepicker/)를 사용하여 달력으로 표현한 예약 화면을 만들어 보았습니다.  
작업한 코드의 일부는 [Codepen](https://codepen.io/pigjh1/pen/YEwaEG)에서 확인할 수 있습니다.
(스타일도 넣고 스크립트도 보완하고 싶었지만...)

<p data-height="300" data-theme-id="28106" data-slug-hash="YEwaEG" data-default-tab="html,result" data-user="pigjh1" data-embed-version="2" data-pen-title="jQuery UI Datepicker" class="codepen">See the Pen <a href="https://codepen.io/pigjh1/pen/YEwaEG/">jQuery UI Datepicker</a> by pigjh1 (<a href="https://codepen.io/pigjh1">@pigjh1</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

### 개발 환경
- IE 크로스브라우징: IE9부터
- 반응형: 모바일 환경 고려
- 접근성 준수: 마크 획득 필요
- 시스템 개발 환경: AME. 기본으로 jqueryui를 로드하는게 있어서 css 리셋 스타일을 재확인 해야 함


### 다른 플러그인을 선택한다면
추가로 브라우저 지원이 IE10부터 되서 익숙한 jQuery UI를 사용했습니다.
- [MultiDatesPicker for jQuery UI](http://dubrox.github.io/Multiple-Dates-Picker-for-jQuery-UI/)
- [Air Datepicker](http://t1m0n.name/air-datepicker/docs/)


### 접근성
이전, 다음 버튼에 키보드 접근이 되지 않아서 수정된 js를 사용 했습니다.  
(Codepen에는 적용해두지 않았습니다)
- [jquery.ui.datepicker_koreaWA.js](https://gist.github.com/dstyle0210/b29d7528bba27fdc75fe)


### 달력에 예약 불가능한 옵션에 날짜 비활성화 처리
- 오늘 기준으로 N일까지는 예약이 불가능
- 오늘 기준으로 90일, 2개월, 다음달까지만 예약 가능
- 특정 요일만 선택 할 수 있음
- 관리자가 설정한 예약 불가능한 날이 있음. 또는 예약이 마감된 경우 시스템에서 예약 불가일 설정
- 주차별 예약
    - N주차 묶음으로 특정 요일 예약 (e.g. 11월 화요일 4주 교육)
    - 요일을 선택하면 다른 요일도 활성화 표시를 해주어야 함
    - 첫 교육이 시작되면 예약 불가 (이러면 월 초에만 예약이 가능한게 됨)
    - 월의 N주차 이상인경우 N주차 만큼만 활성화 (e.g. 11월이 5주인데 4주자라면 마지막 주차는 비활성화)
    - 월의 시작일이 시작일을 지정 (e.g. 11월의 수요일이 1, 8, 15, 22,29인데 4주차 교육으로 1일이 아니라 8일이 시작일로 할 때)
    - 월의 요일에 첫 날짜를 구하기 (e.g. 첫 교육이 시작됬는지 알기 위해 11월의 첫번째 화요일은 몇일인지 알아내기 위함)


### 그 외 특이사항
- 예약 시간이 고정된 경우도 있고, 특졍요일(토요일)에는 예약 시간을 선택할 수 있음
- 날짜 비교 조건은 년을 포함했는데 어차피 최대 3개월 단위라 편의를 위해 월,일 형식 사용


### 배운점
- [자바스크립트 Data 개체](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date)를 많이 다뤄봄
- data를 받아올 때 1,3,2을 콤마(,)로 split하게 되는데 그럼 문자형에서 숫자형으로 바뀌게 됨
- 단위 테스트가 필요한 경우를 알게됨 (주로 화면을 구성하고 모션을 주는 작업을 하다보니 이런 사고를 하는 일이 적음)
- for문을 돌리는거나 배열을 다루는게 아직 부족한 듯 (아쉬움)


### 맺음말
조건이 하나, 둘 붙으면서 소스도 복잡해지고 신경써야 할 부분이 많아서 한번 더 정리하는 개념으로 공들여 글을 작성해 보았습니다.  
주차별 예약이 정말 어려웠습니다. 아하하하하.  
나중에 스크립트를 보면 모를 것 같아서 주석도 잘 달아두었는데 글로 더 복잡하게 만드는것 같기도 합니다ㅠ  
그 외도 예약 정보를 넣기 위해 [formvalidator](http://www.formvalidator.net/)를 붙였는데 여기서도 소소한 이슈가 있어 애를 먹었던 작업하기 힘든 화면이였습니다.  
공부는 많이 되었습니다. 😚