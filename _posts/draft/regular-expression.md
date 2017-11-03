

자바스크립트 정규식 사용예제

http://sugame.tistory.com/entry/자바스크립트-정규식-사용예제

#### 1. 각 문자와 숫자는 해당 문자 또는 문자열이 테스트할 문자열에 있을경우 true가 된다.

```js
// ''a'' 가 있는 문자열 모두가 TRUE (대소문자 구분)
var filter = /a/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

```js
// "about" 가 있는 문자열 모두가 TRUE (대소문자 구분)
var filter = /about/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

#### 2. 대소문자 구분없이 해당 문자 또는 문자열을 검색할 경우 끝에 i 를 붙인다.

```js
// ''a'' 또는 ''A'' 가 있는 문자열 모두가 TRUE (대소문자 구분 안함)
var filter = /a/i
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

#### 3. 여러개의 이어지는 내용들을 검색할 경우는 ''-'' 를 넣어 표현한다.

```js
// ''a'' 에서 ''z'' 까지중 하나만 있으면 모두가 TRUE (대소문자 구분)
var filter = /[a-z]/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

#### 4. 여러가지의 문자 또는 문자열을 검색할 경우 ''|'' 를 넣는다.

```js
// ''a'' 또는 ''b'' 또는 ''c'' 가 있는 문자열 모두가 TRUE (대소문자 구분)
var filter = /a|b|c/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

```js
// ''a'' 에서 ''z'' 까지 또는 ''0'' 에서 ''9'' 까지중 하나만 있으면 모두가 TRUE (대소문자 구분)
var filter = /[a-z]|[0-9]/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

#### 5. 해당 문자또는 문자열이 없는 경우를 검색할 경우 브래킷(''['', '']'') 안에 ''^'' 를 넣는다.

```js
// ''a'' 에서 ''z'' 까지의 문자가 아닌 문자가 있을 경우 TRUE (대소문자 구분)
var filter = /[^a-z]/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

#### 6. 문자열의 첫번째 글자가 일치해야할 경우는 ''^'' 를 브래킷(''['', '']'') 밖에 넣는다.

```js
// ''a'' 에서 ''z'' 까지의 문자로 시작하는 문자열일 겨우 TRUE (대소문자 구분)
var filter = /^[a-z]/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

#### 7. 문자열의 끝쪽 글자가 해당 문자 또는 문자열과 일치해야할 경우는 ''$'' 를 넣는다.

```js
// ''a'' 에서 ''z'' 까지의 문자로 끝나는 문자열일 겨우 TRUE (대소문자 구분)
var filter = /[a-z]$/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```

#### 8. 특수문자('''', ''^'', ''$'', ''*'', ''+'', ''?'', ''.'', ''('', '')'', ''|'', ''{'', ''}'', ''['', '']'')를 검색할 경우는 '''' 를 넣는다.

```js
// '''' 가 있는 문자열일 겨우 TRUE (대소문자 구분)
var filter = /\/
if (filter.test("some test words") == true) { alert("ok"); } else { alert("fail"); }
```


----------

자바스크립트 정규식 유용한 예제

http://blog.naver.com/cj_park70/140111252565

String removeTags(input)

HTML tag부분을 없애준다

function removeTags(input) {
    return input.replace(/<[^>]+>/g, "");
};

example>
var str = "<b>blah</b> <i>soft</i>";
document.write(str +"<br>");
document.write(removeTags(str));
result>
blah soft
blah soft

String String.trim()

문자열의 앞뒤 공백을 없애준다.

String.prototype.trim = function() {
    return this.replace(/^\s+|\s+$/g, '');
};

example>
var str = "         untrimed string            ";
document.write("========" + str+ "==============<br>");
document.write("========" + str.trim() + "==============");
result>
======== untrimed string ==============
========untrimed string==============

String String.capitalize()

단어의 첫 글자를 대문자로 바꿔준다.

String.prototype.capitalize = function() {
    return this.replace(/\b([a-z])/g, function($1){
        return $1.toUpperCase();
    }) ;
};

example>
var str = "korea first world best";
document.write(str.capitalize());
result>
Korea First World Best

String number_format(input)

입력된 숫자를 ,를 찍은 형태로 돌려준다

function number_format(input){
    var input = String(input);
    var reg = /(\-?\d+)(\d{3})($|\.\d+)/;
    if(reg.test(input)){
        return input.replace(reg, function(str, p1,p2,p3){
                return number_format(p1) + "," + p2 + "" + p3;
            }
        );
    }else{
        return input;
    }
}

example>
document.write(number_format(1234562.12) + "<br>");
document.write(number_format("-9876543.21987")+ "<br>");
document.write(number_format("-123456789.12")+ "<br>");
result>
1,234,562.12
-9,876,543.21987
-123,456,789.12


------------









http://regexcrossword.com/
http://xregexp.com/
http://www.rexv.org/
http://txt2re.com/
http://scriptular.com/
http://www.debuggex.com/
http://www.regexplanet.com/
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions
http://leaverou.github.io/regexplained/
