# 웹페지에서 구글 맵 사용하기

## 구글 지도를 표현하는 방법
1. 스크립트

2. 아이프레임으로

## 커스텀 마커 적용하기

## 커스텀 스타일 적용하기

## 웹접근성과 구글맵

## 그외 지도 서비스 API
네이버 지도 : https://navermaps.github.io/maps.js/docs/index.html
다음 지도 : http://apis.map.daum.net/

---

https://navermaps.github.io/maps.js/docs/tutorial-5-map-moves.example.html
https://developers.google.com/maps/documentation/javascript/reference
여기서 panBy
지도api가 좌표가 센터에 오는게 기본이라서 '-' 여태 지도 위에 레이어 올린거 어떻게 이쁘게 맞추나 했는데

ap랑 리리코스

map.panBy(100, 100);

---

Our Company > Global Network > Overview
http://www.muji.com/storelocator/

참고 자료
구글맵 infowindow http://en.marnoto.com/2014/09/5-formas-de-personalizar-infowindow.html
http://www.sulwhasoo.com/int/en/misc/store.html
http://www.sulwhasoo.com/int/en/flagship/journey.html

구글 맵 스크롤 비활성화하기
http://www.thewordcracker.com/miscellaneous/how-to-disable-google-map-scrol/

메모
멀티플 마크 찍는 방법 테스트. 효과 구현에 따라 스크립트 추가
지도 클릭하면 핀이 바뀌는 거 확인 필요
흑백처리 하면서 핀도 검정으로
막는 옵션 설화수 플래그쉽에서 사용한건 IE9에서 작동하지 않음 api에서 옵션 찾아 적용

---

1. 지도api를 이용한 지도 서비스도 당연히 접근성이 준수되어야 합니다. 접근성이 준수된 웹 페이지를 이용하는사람이 지도는 필요없을리 없으니까요. 다만 지도의 특성상 많은 내용을 담고 있기 때문에, 대체 텍스트 부분은 제대로 지정되지 않고 지도콘텐츠 영역 밖에서 설명하는 방법을 권장하고 있습니다. 약도를 설명하는등의 방법을 말합니다.
대체텍스트를 제외한 모든 항목은 지켜져야합니다.

2. 앞서 말한것처럼 대체텍스트를 제공하지 못하더래도 지도가 표현하고자 하는 콘텐츠를 대체 콘텐츠로 제공

3. 구글맵같은 GIS의 경우는 평가 대상에서 제외가 됩니다. 만약 다이나믹한 맵이 아닌, 단순히 약도등을 제공하기 위해 사용되는 경우라면 약도에 대응하는 정보를 하단에 제공해주셔야 합니다.

---

구글 맵(google map) 등 외부 오픈 API 사용시 대체텍스트 관련

김근우 님 담변

구글맵과 같은 외부 API를 사용한 콘텐츠의 경우에도 심사는 동일하게 수행됩니다. 이 경우 다음 두가지 측면을 고려해서 제작하시면 되겠습니다.

1. "지도위에 표시되는 정보와 동일한 형태의 목록"이 구글맵에 접근할 수 없는 시각장애인을 위한 대체 콘텐츠이죠? 이 대체 콘텐츠가 구글맵을 통해 제공하고자 하는 정보를 충분히 전달하고 있는지 점검하세요. 충분하지 않다면 접근성이 떨어진다고 판단하시면 됩니다.

2. 구글맵 자체가 alt 속성이 선언되지 않은 img 요소, 구글맵 애플리케이션의 UI 구성 요소 등 시각장애인에게 접근 자체만으로도 혼란을 일으킬 수 있는 정보가 있다면 이를 마크업 상 구글맵이 등장하기 직전에 가이드와 구글맵을 건너뛸 수 있는 링크를 추가하세요. 가이드에는 구글맵이 접근성이 없으니 건너뛴 후 제공되는 대체 콘텐츠를 참고하라는 식의 내용을 포함하시는 것을 권장합니다

+ 접근성
http://nuli.navercorp.com/forum/post/87

----

구글맵 infowindow
http://en.marnoto.com/2014/09/5-formas-de-personalizar-infowindow.html
https://wordpress.org/support/topic/hiding-infowindows-on-the-map-solution
http://codinglogs.blogspot.kr/2010/05/recipe-1-infowindow-close-upon-opening.html
http://jsfiddle.net/Guffa/GSX6G/3/
