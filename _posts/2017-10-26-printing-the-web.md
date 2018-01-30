---
bg: "tools.jpg"
layout: post
title: "웹페이지 인쇄하기"
date: 2017-10-26 14:20:00
categories: posts
tags: ['javascript', 'css']
---

### css로 인쇄시 제외 설정
- `@media print { … }`를 사용
- 인쇄시 다음 페이지로 넘길 수 있는 page-break-before 속성도 있다.

```css
@page a4sheet { size: 21.0cm 29.7cm }
.a4 { page: a4sheet; page-break-after: always }
```

### 원하는 영역만 인쇄하기
- `window.onbeforeprint`와 `window.onafterprint`로 인쇄 전과 후를 처리할수 있습니다.
- Chrome, Opera는 `window.matchMedia(‘print’)`로 이벤트 식별

```javascript
//페이지 내에서 특정 영역만 인쇄하기
function divPrint(divID) {
    var initBody = document.body.innerHTML; //원래 있는 내용을 임시 저장
    //onbeforeprint는 인쇄 하기전 발생하는 이벤트
    window.onbeforeprint = function(){
        //인쇄할 원하는 영역(div)을 본문에 넣고
        document.body.innerHTML = document.getElementById(divID).innerHTML;
    }
    //인쇄가 끝나고 발생하는 이벤트
    window.onafterprint = function(){
        //원래 내용으로 본문을 채운다.
        document.body.innerHTML = initBody;
    }

    window.print();
}
```

### 원하는 영역을 윈도우 팝업으로 만들어 인쇄후 창 닫기
```javascript
$("#printBtn").click(function() {
    var win = null;
    var tmpHtml = "<html><head><style>body {font-family:Dotum, Arial; font-size: 12pt;}</style></head><body>"
                    +  $("#printcont").html();
                    + "</body></html>"
    win = window.open();
    self.focus();
    win.document.open();
    win.document.write(tmpHtml);
    win.document.close();
    win.print();
    win.close();
});
```

### iframe 이용하여 원하는 영역만 인쇄하기
화면에 보이지는 않지만 iframe을 하나 만들어서 거기에 인쇄할 내용을 복사해서 붙여 넣고, 그 iframe 자체를 인쇄해 버리는 방법이다.

```javascript
var print-contents = $("#print-div").html();
$("#print-iframe").contents().find("body").html(print-contents);
$("#print-iframe").contents().find(".btn_box_hidden").hide();
$("#print-iframe").focus();
frames["print-iframe"].focus();
frames["print-iframe"].print();
```
```html
<div id="print-div">이 부분이 인쇄가 됩니다.</div>
<iframe name="print-iframe" id="print-iframe" src="" width="0" height="0" style="display:none"></iframe>
```

### jquery 플러그인 printArea 사용
- https://plugins.jquery.com/PrintArea/

```javascript
$(document).ready(function() {
   $("#printButton").click(function(){
      $("#printable").printArea();
   });
});
```

### 맺음말
인쇄 관련해서는 채용시스템을 구축하면서 고생을 많이 했습니다.
입사지원 목록을 출력하는데 규격이 A4가 아니라고 해서 B4로 최적화 작업하는데 고생했던 기억이 납니다.
고객사에서 사용하는 인쇄 장비까지 대여해서 엄청난 출력 테스트를 했던 기억이 나는군요. (어색한 맺음말)

### Reference
- [웹을 인쇄하기](https://mytory.net/archives/9796)
- [웹 A4 출력](http://kimmogoon-textcube.blogspot.kr/2010/02/웹-a4-출력.html)
- [print.css 파일을 따로 만들 필요가 없습니다.](http://naradesign.net/wp/2007/12/19/133/)
- [jQuery printArea - 특정 요소만을 선택해서 인쇄](http://blog.naver.com/whwlfnsl/70066917709)
- [jQuery div print 하기(iframe이용)](http://codewave.tistory.com/17)
- [원하는 영역(div)만 프린트하기](http://cambo95.blog.me/100154119350)
- [특정-영역-인쇄](http://eternallife.tistory.com/entry/특정-영역-인쇄)
- [javascript window.print() 이전/이후 시점 알기](http://blog.hemapresso.com/?p=560)
- https://developer.mozilla.org/en-US/docs/Web/API/WindowEventHandlers/onbeforeprint
- https://developer.mozilla.org/en-US/docs/Web/API/Window.matchMedia
