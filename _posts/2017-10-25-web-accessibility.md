---
bg: "tools.jpg"
layout: post
title: "접근성 관련 정리"
date: 2017-10-25 19:03:00
categories: posts
tags: ['html', 'accessibility']
---

### 국내 가이드 참고
- [웹접근성 연구소](http://www.wah.or.kr/Participation/technique.asp)
- [네이버 널리](http://nuli.navercorp.com/sharing/a11y/)
- [다음 다룸](http://darum.daum.net/accessibility/intro)

### 웹 접근성 검사 도구
- 크롬 익스텐션
    - [OpenWAX](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=kohttps://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko)
    - [N-WAX](https://chrome.google.com/webstore/detail/n-wax/jngfhfcfdliajpedjfnbefhckaoknclp) : 네이버에서 만듬 Open-WAX와 유사
    - [WAVE Evaluation Tool](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh?hl=ko)
- 서비스형
    - [비엑스](https://www.beaccessible.net/) : 1개 페이지만 무료 검사 가능. 명도 대비 체크하기 좋았음
    - [한국웹접근성평가센터 자가진단 서비스 - 비엑스](https://www.beaccessible.net/dashboard/selfAnalyze) : 10개 페이지 검사 가능. 대체텍스트, 제목, 기본언어, 레이블 제공 항목을 검사. 오류 위치를 상세히 알려주어 좋음
    - [웹 접근성 자가진단 서비스](https://accessibility.kr/nia/check.php) : 10개 페이지 검사 가능. 이미지, 제목, 언어, 레이블, 표 검사 (아는 사람은 다 아는 신현석님이 만드셨습니다.)
    - [wave](http://wave.webaim.org/) : 외국 검사 도구. 페이지당 검사하여 오류에 빨간 딱지
- 설치형
    - [K-WAH 4](http://www.wah.or.kr/board/boardView.asp?page=1&brd_sn=2&brd_idx=1012) : 한국정보화진흥원에서 만들 프로그램 서비스 중단되어 공식적인 파일은 없음. 페이지 전체를 검사해서 마크업 닫기 오류 등 실수를 확인하기에 좋음
    - [Watch 1.0](http://www.webwatch.or.kr/solution/N05_01.html) : 다운받아봤는데 실행이 안됨.
    - [A=CoolCheck!](http://www.webwatch.or.kr/solution/N05_03.html) : (유료) 센티널테크놀로지와 웹와치에서 만듬. 무료버전이 있으나 제약이 많음
- 명도대비
    - [Colour Contrast Analyser](http://www.visionaustralia.org/digital-access-cca) : Download Colour Contrast Analyser 하여 압축 풀어 exe 파일 실행
    - [snook 명도대비 온라인 측정](http://snook.ca/technical/colour_contrast/colour.html)
    - [Contrast Ratio (포토샵 익스텐션)](http://nuli.navercorp.com/sharing/a11y/tool#cr) : 네이버에서 공개. 사용해보지 않음
- 모바일
    - [안드로이드의 TalkBack(토크백)](https://support.google.com/accessibility/android/answer/6283677?hl=ko)
    - [IOS의 VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/?lang=ko)

### 최근에 본 글 스크랩
- [Web Content Accessibility Guidelines—for People Who Haven't Read Them](https://24ways.org/2017/wcag-for-people-who-havent-read-them)
- [Stop Designing For Only 85% Of Users: Nailing Accessibility In Design](https://www.smashingmagazine.com/2017/10/nailing-accessibility-design/)

### 웹 접근성 향상을 위한 10가지 지침
[aerolab](https://aerolab.co/blog/web-accessibility/)에 소개된 내용입니다.

#### 1. 색상에 의존하지 마십시오

#### 2. 줌을 차단하지 마십시오
반응형 웹 제작시 모바일 장치를 사용하여 웹 페이지를 확대할수 없게 최대 배율을 1로 고정하지 않는다.
사용자가 휴대기기에서 자유롭게 확대/ 축소 할수 있도록 하고, 데스크톱에서도 확대되는지 확인 해야 한다.

```html
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1">
```

#### 3. alt 속성
1. 의미없는 이미지에는 공백으로
2. `<img>` 태그가 이미지기 때문에 ~이미지라고 알릴 필요는 없다.
3. 이미지의 기능은 의미만큼 중요. 로고가 웹사이트의 홈페이지로 연결되면 "로고"대신 "홈페이지"와 같아아 한다. (의미 있는 대체텍스트를 쓰라는 이야기 인 듯...)
4. 대체텍스트는 접근성만을 위한건 아니다. 느린 데이터 연결을 사용할 경우 이미지를 비활성하여 볼 수도 있다. 이러한 사용자를 염두해 두자.

##### SVG 대체택스트
SVG에 대체텍스트는 `<title>`과 `<desc>` 태그를 사용한다.

```html
<symbol id="langIcon">
  <title>Language Icon</title>
  <desc>Longer description</desc>
  <path d="M0 2C6.47 2 2 6.48 2 12s4.47 10 9.99 0h24v24H0z" />
</symbol>
```

#### 4. 비디오에 자막 및 캡션 추가
1. 유튜브 동영상 업로드시 자막 사용
2. 유튜브에서 정확한 작막을 제공하고 싶다면 .srt, .sub 및 .sbv를 사용할 수도 있다.
3. 비디오 태그를 사용할 경우 WebVTT형식의 파일을 사용할수 있다. (국내 상황도 같은지까지는 잘 모르겠다...)

```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track label="English Captions" kind="captions" srclang="eN" src="captions.vtt" default>
  <track label="Subtitulos en español" kind="captions" srclang="es" src="subs.vtt">
</video>
```

#### 5. 의미있는 태그를 사용하자 (Semantics = accessibility)
헤딩 태그(`<h1>~<h6>`)를 잘쓰자

#### 6. 올바른 마크업을 사용

##### Time vs. Datetime
- time 요소는 ISO 8601 표준을 사용하여 날짜와 시간을 나타내는 많은 형식의 날짜 형식, 표준 시간대 및 기간을 표시
- datetime은 <time>의 내용을 나타내는 데 도움이되는 선택적 특성

```html
<time>14:54</time> Hours and minutes
<time>2018-06</time> Year and month
<time>-03:00</time> Time zones
<time>2h 32m</time> Harry Potter 2 Duration
<p>CSSConf Argentina took place on <time datetime=”2016-08-07”>August 7th</time></p>
```

##### Del and Ins
- ins 요소는 문서에 추가
- del 요소는 삭제 된 내용

```html
<ul>
    <li><ins datetime="2017-08-02">Icecream</ins></li>
    <li>Candy</li>
    <li>Pasta</li>
</ul>
<ul>
    <li><del datetime="2017-06-05">Rewatch Harry Potter 8</del></li>
    <li><del datetime="2017-06-05">Cry because ____ dies.</del></li>
    <li><del datetime="2017-06-06">Write article</del></li>
    <li>Order room</li>
</ul>
```

##### Button vs. <a> tag
`<a>` 태그는 링크를 연결하기 위한 것입니다. 메뉴 열고 닫기나 이미지 갤러러 같은 경우에는 `<button>`

#### 7. roles를 사용
역할 속성은 기본값을 변경하려는 경우에만 사용
덧. WAI-ARIA를 사용하라 국내에도 [사례집]( http://www.wah.or.kr/board/boardView.asp?page=1&brd_sn=5&brd_idx=1019)과 [예제](https://github.com/niawa/ARIA)가 공개 되었으니 참고

#### 8. 숨김 텍스트
숨김 텍스트를 위한 스타일
```css
.visually-hidden {
    position: absolute !important;
    clip: rect(1px 1px 1px 1px); /* IE6, IE7 */
    clip: rect(1px, 1px, 1px, 1px);
    padding:0 !important;
    border:0 !important;
    height: 1px !important;
    width: 1px !important;
    overflow: hidden;
}
body:hover .visually-hidden a, body:hover .visually-hidden input, body:hover .visually-hidden button { display: none !important; }
```

#### 9. W3C표준 과 WCAG 가이드 라인을 지킴

#### 10. 검사도구 이용하여 테스트
이 지식을 모두 적용했으면 테스트 할 시간입니다.
다음은 웹 사이트 접근성을 감사 할 수있는 최상의 도구 목록입니다.
위에서 소개한 국내에 맞는 도구를 사용해주세요.

- [ChromeVox](http://www.chromevox.com/) : Mac 및 Windows 사용자가 사용할 수있는이 Chrome 확장 프로그램은 웹 사이트를 테스트하는 데 사용할 수있는 스크린 리더입니다.
- [Chrome 용 접근성 개발자 도구](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?hl=en) : 일상적인 개발자 도구에 접근성 감사 옵션을 추가 한이 브라우저의 또 다른 멋진 확장 프로그램입니다.
- [컬러 필터](https://www.toptal.com/designers/colorfilter) : 이 온라인 도구로 다양한 유형의 색맹 환자를위한 웹 사이트를 테스트하십시오.
- [W3C 검사기](https://validator.w3.org/) : 이 공식 W3C 도구는 HTML 마크 업이 웹 접근성 규칙을 따르는 지 알려줍니다!
- [A11Y Compliance Platform](https://www.boia.org/wc3-free-2-0-aa-report) : BOIA (Internet Accessibility Bureau)는 WCAG A / AA 체크 포인트에 대해 테스트했을 때 웹 사이트 요금을 개괄적으로 보여주는 등급 보고서를 제공합니다.
- [WAVE](http://wave.webaim.org/) :  WebAIM이 만든 웹 접근성 평가 도구.
