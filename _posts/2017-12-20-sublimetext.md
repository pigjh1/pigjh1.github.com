---
bg: "tools.jpg"
layout: post
title: "Sublime Text"
date: 2017-12-20 12:00:00
categories: posts
tags: ['project setting']
---

### 관련 URL
- sublime text : https://www.sublimetext.com/
- 패키지컨트롤 : https://packagecontrol.io/
- 생활코딩 Sublime Text 2 : https://opentutorials.org/module/406/3595
- 사용자정의 : http://eduardolopes.github.io/sublime-config/

### Package
- Emmet
    - https://github.com/sergeche/emmet-sublime
    - http://docs.emmet.io/
- IME Support : 한글 입력 문제를 보완
    - https://github.com/chikatoike/IMESupport
- Side Bar Enhancements
- ConvertToUTF8 : 한글 인코딩 문서의 편집 문제 보완
- Color Picker : 편리하게 색상 수정
- SFTP : 원격으로 파일을 열고 편집
- css autocomplete : 자동완성
- AutoBackups : 텍스트 저장시 자동 백업파일 만들기
- Sublimerge : 파일비교
    - [팁]Sublime Text(서브라임텍스트) Sublimerge 사용법 1-바로가기 단축키
    - http://demun.tistory.com/2379
- SublimeLinter : 코드오류를 자동으로 잡아줌
    - http://demun.tistory.com/2240
- Text Pastry: Multi-Insert of numbers, words, sequences or UUIDs 다중 선택된 줄 (단어) 에 연속된 숫자를 입력하거나 복사한 클립보드를 순차적으로 입력해줍니다.
- livereload : 실시간 반영하기
    - http://demun.tistory.com/2345

### Sublime Text 단축키 (window)
- Ctrl + Shift + Alt + c : cmd 띄우기
- Ctrl + Alt + D : 파일 비교
- Ctrl + Shift + D : 한줄복사
- Ctrl + / : 주석
- Ctrl + Shift + P : 커멘드 팔레트 켜기
- Ctrl + Shift + F : 여러파일에서 찾기
- Ctrl + I : 증분찾기
- Ctrl + Shift + v : 들여쓰기로 붙여넣기
- Ctrl + Shift + a : 태그의 확장 선택
- Ctrl + P : 원하는 곳 가기
- Ctrl + R : 심볼로 가기
- Ctrl + Alt + a : (Alignment) 정렬 맞춰줌
- Ctrl + Shift + C : (CSSComb) 스타일 시트 정리


### 커멘드 팔레트
- Indentation: Reindent Line : 태그 자동정렬
- HTML: Encode Special Characters : 특수문자 자동변환


### 기능 확인
- 화면 분할 방법
    - File - New View into File 하여 레이아웃을 row2로 변경해서 본다
    - 레이아웃 변경 단축키 잘 안먹는 이유 : 오른쪽에 있는 숫자키로 할때 작동 안함. 위쪽에 위치한 숫자로 해야함
- 개행문자 변경
    - http://zetawiki.com/wiki/서브라임텍스트_개행문자_변경
- 스페이스 ↔ 탭 변환, 자동 태그정렬
    - Ctrl + Shift + P : 커멘드 팔레트 켜기 하여 Indentation: Reindent Line
    - http://yadw.tistory.com/280
- 선택한 파일의 이름을 복사할 수 있는 기능
    - 사이드바에서 파일 선택 후 오른쪽 마우스 클릭 Copy Name를 하면 파일명을 Copy Path를 하면 경로까지 복사
    - 사이드바 플러그인 설치시
- 클립텍스트 역할
    - 스니펫을 활용한다 Toll - New Snippet
    - http://demun.tistory.com/2241
    - tab를 누르면 자동완성이 된다.
    - tabTrigger에 한글을 사용 할 수는 없는가 - 가능하다.
    - snippet 파일 하나에 여러개의 지정은 불가능 해보인다.
- 인코딩 확인하는 법
    - 기본적으로 UTF8. euc-kr 사용할려면 패키지 설정
