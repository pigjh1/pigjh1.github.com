---
bg: "tools.jpg"
layout: post
title: "웹페지에서 구글 맵 사용하기"
date: 2017-10-31 14:20:00
categories: posts
tags: ['javascript', 'google']
---

@@@@@@@@@@@@@@@@@@@ 확인할 내용

### 구글 지도를 표현하는 방법
#### 1. iframe 사용
구글지도에서 위치 검색 > 공유하기 > 지도퍼가기 를 하면 iframe소스를 확인할 수 있습니다.
접근성을 위해 기본 제공 소스에 title 속성에 값을 넣어줍니다. (iframe 자체가 접근성에 좋지는 않지만)
```
<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3162.673501606904!2d126.98074241564801!3d37.562755482101664!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x357ca2f0f1f1583d%3A0xd1f6a6e94f8697d8!2zTGluZSBGcmllbmRzIO2UjOuemOq3uOyLrSDsiqTthqDslrQg66qF64-Z7Jet7KCQ!5e0!3m2!1sko!2s!4v1509344885928" width="600" height="450" frameborder="0" style="border:0" allowfullscreen title="라인스어 명동 지도"></iframe>
```

#### 2. JavaScript API를 사용
아래 케이스 별로 자세히 살펴봅시다.

### 케이스별
#### 마커 적용하기
기본적인 마커와 사용자 지정 이미지를 적용하는 방법을 가이드를 참고
https://developers.google.com/maps/documentation/javascript/markers?hl=ko


@@@@@@@@@@@@@@@@@@@
이야기 하고 싶은건은 여러개의 마커를 적용하고 컨트롤 하는것
http://www.muji.com/storelocator/
멀티플 마크 찍는 방법 테스트. 효과 구현에 따라 스크립트 추가
지도 클릭하면 핀이 바뀌는 거 확인 필요

http://en.marnoto.com/2013/12/mapa-com-varios-marcadores-google-maps.html

#### 커스텀 스타일 적용하기
구글 지도 스타일을 적용할 수 있는데 한국은 해당하지 않습니다.

> 한국은 국내법상 지도 데이터를 해외 데이터 센터로 반출할 수 없는 제약이 있어서 구글 지도에서 제공하는 일부 기능이 동작하지 않는데, 여기에 지도 이미지를 동적으로 변경하는 기능도 포함됩니다. 한국 지도는 국내 서버를 통해 제한적인 스타일의 지도만 서비스하고 있고, 그 외 API 등을 통한 지도 이미지의 변경은 현재로서는 어렵습니다.

- [Maps JavaScript API > 구글 지도 스타일 지정 시작](https://developers.google.com/maps/documentation/javascript/styling?hl=ko)
- [Google 지도 사용자 게시판 문의](https://productforums.google.com/forum/#!topic/maps-ko/AI_0FslsAs4)
- [Google MAP Style 적용하기](https://medium.com/guleum/google-map-style-적용하기-3042efc85c7e)

css filter기능을 사용하여 스타일 적용을 할 수도 있습니다.

#### 스크롤 및 패닝 동작
이미지만 보여주고 싶다 할때는 옵션을 끄기

구글 맵 스크롤 비활성화하기
http://www.thewordcracker.com/miscellaneous/how-to-disable-google-map-scrol/
https://developers.google.com/maps/documentation/javascript/interaction?hl=ko



기본 옵션이 있으니 그걸 적용


#### 지도의 좌표 이동하기
@@@@@@@@@@@@@@@@@@@
https://developers.google.com/maps/documentation/javascript/reference

panBy 검색
여기서 panBy
지도api가 좌표가 센터에 오는게 기본이라서 '-' 여태 지도 위에 레이어 올린거 어떻게 이쁘게 맞추나 했는데

map.panBy(100, 100);


#### infowindow
http://en.marnoto.com/2014/09/5-formas-de-personalizar-infowindow.html
https://wordpress.org/support/topic/hiding-infowindows-on-the-map-solution
http://codinglogs.blogspot.kr/2010/05/recipe-1-infowindow-close-upon-opening.html
http://jsfiddle.net/Guffa/GSX6G/3/


### Static Maps API

앱과 사이트에서 지도를 이미지로 구현합니다.
반응형 웹에서는 사용시 유동적으로 변하지 않아서 (?) 아직 사용은.
https://developers.google.com/maps/documentation/static-maps/?hl=ko

#### 기타 활용 케이스
##### 지도의 마크를 클릭했을 때 해당 주소의 구글 지도 페이지로 이동하기
```javascript
google.maps.event.addListener(marker, 'click', function() {
    location.href = "http://maps.google.com/maps?language=ko&z=5&q=" + encodeURI("서울특별시 구로구 구로동 222-14 에이스하이앤드타워2차");
});
```

##### zoom 포인트에 따라 infowindow 값 출력
```javascript
var infowindow = new google.maps.InfoWindow({
    content: 'Change the zoom level',
    position: originalMapCenter
});

infowindow.open(map);

map.addListener('zoom_changed', function() {
    infowindow.setContent('Zoom: ' + map.getZoom());
});
```


### 그외 지도 서비스 API
- 네이버 지도 : https://navermaps.github.io/maps.js/docs/index.html
- 다음 지도 : http://apis.map.daum.net/

### 맺음말
구글 지도 사용하는 법은 매번 정리하려고 했다가도 미루던 주제이다.
구글, 네이버, 다음 이렇게 사용한 적이 있어서 케이스별로 정리해두면 좋을텐데...

테스트 파일을 이곳에 : https://codepen.io/pigjh1/pen/YEPGem
