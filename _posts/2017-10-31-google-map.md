---
bg: "tools.jpg"
layout: post
title: "웹페이지에서 구글 맵 사용하기"
date: 2017-10-31 14:20:00
categories: posts
tags: ['javascript', 'google']
---

구글 지도 사용하는 법은 매번 정리하려고 했다가도 미루던 주제라 한번 정리를 해보았습니다.
(역시나 정리한 듯 정리되지 않은 생각들...)

### 마커 적용하기
기본적인 마커와 사용자 지정 이미지를 적용하는 방법은 가이드를 참고
https://developers.google.com/maps/documentation/javascript/markers?hl=ko

### 여러개의 마커 적용
- http://en.marnoto.com/2013/12/mapa-com-varios-marcadores-google-maps.html
- [MUJI](http://www.muji.com/storelocator/)에서 사용한 방법이 인상적 : 호버시 매장명을 보여줌

### 커스텀 스타일 적용하기
구글 지도 스타일을 적용할 수 있는데 한국은 해당하지 않습니다.

> 한국은 국내법상 지도 데이터를 해외 데이터 센터로 반출할 수 없는 제약이 있어서 구글 지도에서 제공하는 일부 기능이 동작하지 않는데, 여기에 지도 이미지를 동적으로 변경하는 기능도 포함됩니다. 한국 지도는 국내 서버를 통해 제한적인 스타일의 지도만 서비스하고 있고, 그 외 API 등을 통한 지도 이미지의 변경은 현재로서는 어렵습니다.

- [Maps JavaScript API > 구글 지도 스타일 지정 시작](https://developers.google.com/maps/documentation/javascript/styling?hl=ko)
- [Google 지도 사용자 게시판 문의](https://productforums.google.com/forum/#!topic/maps-ko/AI_0FslsAs4)
- [Google MAP Style 적용하기](https://medium.com/guleum/google-map-style-적용하기-3042efc85c7e)

css filter기능을 사용하여 스타일 적용을 할 수도 있습니다.
테스트 코드는 [Codepen](https://codepen.io/pigjh1/pen/YEPGem)에서 확인할 수 있습니다.

### 스크롤 및 패닝 동작
스크롤로 확대,축소 기능을 사용하지 않고 이미지형태로 보여주고 싶다 할때는 옵션을 끄기

- [구글 맵 스크롤 비활성화하기](http://www.thewordcracker.com/miscellaneous/how-to-disable-google-map-scrol/)
- [스크롤 및 패닝 동작](https://developers.google.com/maps/documentation/javascript/interaction?hl=ko)

### 지도의 좌표 이동하기
panBy: 기본적으로 좌표가 센터에 오는데 좌표를 이동 할수 있음
https://developers.google.com/maps/documentation/javascript/reference
```
map.panBy(100, 100);
```

### infowindow
마커를 클릭했을 때 상세 정보를 보여주기 위해 사용
- http://en.marnoto.com/2014/09/5-formas-de-personalizar-infowindow.html
- https://wordpress.org/support/topic/hiding-infowindows-on-the-map-solution
- http://codinglogs.blogspot.kr/2010/05/recipe-1-infowindow-close-upon-opening.html
- http://jsfiddle.net/Guffa/GSX6G/3/

### 지도의 마크를 클릭했을 때 해당 주소의 구글 지도 페이지로 이동하기
```javascript
google.maps.event.addListener(marker, 'click', function() {
    location.href = "http://maps.google.com/maps?language=ko&z=5&q=" + encodeURI("서울특별시 구로구 구로동 222-14");
});
```

### zoom 포인트에 따라 infowindow 값 출력
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

### Static Maps API
앱과 사이트에서 지도를 이미지로 구현합니다.
반응형 웹에서는 유동적으로 보여주는게 좋아서 아직 사용해보지 않았습니다.
https://developers.google.com/maps/documentation/static-maps/?hl=ko

### iframe으로 넣을 수도 있습니다.
"구글지도에서 위치 검색 > 공유하기 > 지도퍼가기" 를 하면 iframe소스를 확인할 수 있습니다.
접근성을 위해 기본 제공 소스에 title 속성에 값을 넣어줍니다. (iframe 자체가 접근성에 좋지는 않지만)
```
<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3162.673501606904!2d126.98074241564801!3d37.562755482101664!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x357ca2f0f1f1583d%3A0xd1f6a6e94f8697d8!2zTGluZSBGcmllbmRzIO2UjOuemOq3uOyLrSDsiqTthqDslrQg66qF64-Z7Jet7KCQ!5e0!3m2!1sko!2s!4v1509344885928" width="600" height="450" frameborder="0" style="border:0" allowfullscreen title="라인스토어 명동 지도"></iframe>
```

### 그외 지도 서비스 API
- 네이버 지도 : https://navermaps.github.io/maps.js/docs/index.html
- 다음 지도 : http://apis.map.daum.net/
