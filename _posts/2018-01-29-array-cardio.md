---
bg: "tools.jpg"
layout: post
title: "자바스크립트 배열 메서드"
date: 2018-01-29 10:26:00
categories: posts
tags: ['Javascript', 'es6']
---

요즘 vue.js를 공부하는데 데이터 변수를 다룰때 배열을 많이 사용하는데 익숙하지 않는 메서드들이 더 어려운 것 같아 한번 정리를 해보았습니다.
es6를 학습할때 [javascript30](https://javascript30.com/)이 많은 도움이 되었는데 특히 배열 다루는 예제가 좋아서 다시 복습하는 의미로 정리!

### 메서드 정리
[Array.prototype MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype)에 잘 정리되었습니다.

| Priority apples | Second priority | Third priority |
|-------|--------|---------|
| ambrosia | gala | red delicious |
| pink lady | jazz | macintosh |
| honeycrisp | granny smith | fuji |

#### 변경자 메서드 : 배열을 수정합니다.
| 메서드 | 용도 |
|-------------------|----------|
| copyWithin()      | 배열 내의 지정된 요소들을 동일한 배열 내에서 복사합니다. |
| fill()            | 배열 안의 시작 인덱스부터 끝 인덱스까지의 요소값을 지정된 정적 값으로 채웁니다. |
| pop()             | 배열에서 마지막 요소를 뽑아내고, 그 요소를 반환합니다. |
| push()            | 배열의 끝에 하나 이상의 요소를 추가하고, 변경된 배열의 길이를 반환합니다. |
| reverse()         | 배열의 요소 순서를 반전시킵니다. - 첫 번째가 마지막이 되고 마지막이 첫 번째가 됩니다. |
| shift()           | 배열에서 첫 번째 요소를 삭제하고 그 요소를 반환합니다. |
| sort()            | 배열의 요소를 정렬하고 그 배열을 반환합니다. |
| splice()          | 배열에서 요소를 추가/삭제합니다. |
| unshift()         | 배열의 앞에 하나 이상의 요소를 추가하고 새로운 길이를 반환합니다. |

#### 접근자 메서드 : 배열을 수정하지 않고 배열 일부를 반환합니다.
| 메서드 | 용도 |
|-------------------|----------|
| concat()          | 배열과, 인자로 주어진 배열/값을 결합해 새로운 배열을 만들고, 이 새 배열을 반환합니다. |
| includes()        | 배열에 특정 요소가 포함돼있는지 알아내어 true 또는 false를 적절히 반환합니다. |
| indexOf()         | 배열에서 지정한 값과 같은 요소의 첫 인덱스를 반환합니다. 없으면 -1을 반환합니다. |
| join()            | 배열의 모든 요소를 문자열로 변환하여 합칩니다. |
| lastIndexOf()     | 배열에서 지정한 값과 같은 요소의 마지막 인덱스를 반환합니다. 없으면 -1을 반환합니다. |
| slice()           | 배열의 일부를 추출한 새 배열을 반환합니다. |
| toSource()        | 지정한 배열을 나타내는 배열 리터럴을 반환합니다.새로운 배열을 만들기 위해 이 값을 사용할 수 있습니다. |
| toString()        | 배열과 요소를 반환하는 문자열을 반환합니다. Object.prototype.toString() 메서드를 재정의합니다. |
| toLocaleString()  | 배열과 요소를 나타내는 지역화된 문자열을 반환합니다. Object.prototype.toLocaleString() 메서드를 재정의합니다. |

#### 반복 메서드
| 메서드 | 용도 |
|-------------------|----------|
| entries()         | 배열의 각 인덱스에 대한 키/값 쌍을 포함하는 새로운 배열 반복자 객체를 반환합니다. |
| every()           | 만약 배열의 모든 요소가 제공된 검사 함수를 만족하면 true를 반환합니다. |
| filter()          | 주어진 필터링 함수의 값의 결과가 참인 경우의 배열 요소들만으로 새로운 배열을 생성하여 반환합니다. |
| find()            | 주어진 테스팅 함수의 요구조건을 만족하는 배열 요소를 반환합니다. 그러한 배열 요소가 없으면 undefined를 반환합니다. |
| findIndex()       | 주어진 테스트 함수를 만족하는 배열의 첫 번째 요소에 대한 인덱스를 반환합니다. 그렇지 않으면 -1이 리턴됩니다. |
| forEach()         | 배열의 각각의 요소에 함수를 호출합니다. |
| keys()            | 배열의 각 인덱스에 대한 key들을 가지는 새로운 Array Iterator 객체를 반환합니다. |
| map()             | 배열 내의 모든 요소 각각에 대하여  제공된 함수(callback)를 호출하고, 그 결과를 모아서  만든 새로운 배열을 반환합니다. |
| reduce()          | 배열의 각 값에 대해 왼쪽에서 오른쪽으로 함수를 적용하여 단일 값으로 줄입니다. |
| reduceRight()     | 배열의 각 값에 대해 오른쪽에서 왼쪽으로 함수를 적용하여 단일 값으로 줄입니다. |
| some()            | 배열중의 적어도 한 요소가 테스팅 함수를 만족시킨 다면 true를 반환합니다. |
| values()          | 배열의 요소값들에 대한 Array Iterator 객체를 반환합니다. |


### 생소한 매소드 사용 예제
```JavaScript
[1, 2, 3].includes(2); // true

[12, 5, 8, 130, 44].filter(function (value) {
    return value >= 10;
});
// [12, 130, 44]

[1, 4, 9].map(function(num) {
    return num * 2;
});
// [1, 4, 9]

[0, 1, 2, 3].reduce(function(a, b) {
    return a + b;
});
// 6

[0, 1, 2, 3].reduce( (prev, curr) => prev + curr );
// 6

[[0, 1], [2, 3], [4, 5]].reduce(function(a, b) {
  return a.concat(b);
}, []);
// [0, 1, 2, 3, 4, 5]

[2, 5, 8, 1, 4].some(elem => elem > 10);  // false
[12, 5, 8, 1, 4].some(elem => elem > 10); // true

[5, 12, 8, 130, 44].find(function(element) {
    return element > 10;
});
// 12

[5, 12, 8, 130, 44].filter(function(element) {
    return element > 10;
});
// [12, 130, 44]
```

---

### JavaScript30의 배열 부분 보기
Day4, Day7, Day12, Day17

#### 0. 변수
```JavaScript
const inventors = [
  { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
  { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
  { first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
  { first: 'Marie', last: 'Curie', year: 1867, passed: 1934 },
  { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
  { first: 'Nicolaus', last: 'Copernicus', year: 1473, passed: 1543 },
  { first: 'Max', last: 'Planck', year: 1858, passed: 1947 },
  { first: 'Katherine', last: 'Blodgett', year: 1898, passed: 1979 },
  { first: 'Ada', last: 'Lovelace', year: 1815, passed: 1852 },
  { first: 'Sarah E.', last: 'Goode', year: 1855, passed: 1905 },
  { first: 'Lise', last: 'Meitner', year: 1878, passed: 1968 },
  { first: 'Hanna', last: 'Hammarström', year: 1829, passed: 1909 }
];
const people = ['Blake, William', 'Beck, Glenn', 'Becker, Carl', 'Beckett, Samuel', 'Beddoes, Mick', 'Beecher, Henry', 'Beethoven, Ludwig', 'Begin, Menachem', 'Belloc, Hilaire', 'Bellow, Saul', 'Benchley, Robert', 'Benenson, Peter', 'Ben-Gurion, David', 'Benjamin, Walter', 'Benn, Tony', 'Bennington, Chester', 'Benson, Leana', 'Bent, Silas', 'Bentsen, Lloyd', 'Berger, Ric', 'Bergman, Ingmar', 'Berio, Luciano', 'Berle, Milton', 'Berlin, Irving', 'Berne, Eric', 'Bernhard, Sandra', 'Berra, Yogi', 'Berry, Halle', 'Berry, Wendell', 'Bethea, Erin', 'Bevan, Aneurin', 'Bevel, Ken', 'Biden, Joseph', 'Bierce, Ambrose', 'Biko, Steve', 'Billings, Josh', 'Biondo, Frank', 'Birrell, Augustine', 'Black Elk', 'Blair, Robert', 'Blair, Tony'];
```

#### 1. filter()
inventors에서 1500 년대에 태어난 사람들을 필터링 하세요.
```JavaScript
inventors.filter(inventor => (inventor.year >= 1500 && inventor.year < 1600));
```

#### 2. map()
inventors에서 이름과 성을 합쳐서 보여주세요.
```JavaScript
inventors.map(inventor => `${inventor.first} ${inventor.last}`);
```

#### 3. sort()
inventors 생년월일별로 정렬해주세요.
```JavaScript
inventors.sort((a, b) => a.year > b.year ? 1 : -1 );
```

#### 4. reduce()
inventors가 살았던 년도의 총 합계를 구하세요.
```JavaScript
inventors.reduce((a, b) => {
    return a + (b.passed - b.year);
}, 0);
```

#### 5. sort()
inventors가 살았던 기간별 정렬해주세요.
```JavaScript
inventors.sort((a,b) => a.passed - a.year > b.passed - b.year ? 1 : -1);
```

#### 6. map(), filter(), includes()
[성당 목록](https://en.wikipedia.org/wiki/Category:Boulevards_in_Paris)에서 이름에 de가 들어있는 파리 대성당의 목록
```JavaScript
const category = document.querySelector('.mw-category');
const links = Array.from(category.querySelectorAll('a'));
const de = links
        .map(link => link.textContent)
        .filter(streetName => streetName.includes('de'));
```


#### 7. sort()
people을 last name 순서대로 정렬
```JavaScript
people.sort((a,b) => { return a > b ? 1 : -1; });
```

#### 8. reduce()
각 인스턴스의 합을 구합니다.
```JavaScript
['car', 'car', 'truck', 'truck', 'bike', 'walk', 'car', 'van', 'bike', 'walk', 'car', 'van', 'car', 'truck' ].reduce(function(obj, i) {
  if (!obj[i]){
    obj[i] = 0;
  }
  obj[i]++;
  return obj;
}, {});
```

#### 9. some(), every()
```JavaScript
const people = [
    { name: 'Wes', year: 1988 },
    { name: 'Kait', year: 1986 },
    { name: 'Irv', year: 1970 },
    { name: 'Lux', year: 2015 }
];

// 19세 이상의 사람이 적어도 한 명입니까?
people.some(arr => nowFullyear - arr.year >= 19);
// 모두 19 세 이상입니까?
people.every(arr => nowFullyear - arr.year >= 19);
```

#### 10. find(), findIndex()
```JavaScript
const comments = [
    { text: 'Love this!', id: 523423 },
    { text: 'Super good', id: 823423 },
    { text: 'You are the best', id: 2039842 },
    { text: 'Ramen is my fav food ever', id: 123523 },
    { text: 'Nice Nice Nice!', id: 542328 }
];

// id가 823423
const findComment = comments.find(item => item.id === 823423);
// id가 823423가 몇번째 요소인지
const findCommentIdx = comments.findIndex(item => item.id === 2039842);
// id가 823423인 요소를 지우기
const newComments = [
  ...comments.slice(0, findCommentIdx),
  ...comments.slice(findCommentIdx + 1)
];
```

### 11. push(), splice(), join(), includes()
키보드를 눌러 비밀코드를 입력하면 메시지를 보여준다.
```JavaScript
const input = [];
const secret = 'secret';

window.addEventListener('keyup', (e) => {
    input.push(e.key);
    input.splice(-secret.length - 1, input.length - secret.length);

    if (input.join('').includes(secret)) {
        console.log('🤡 비밀코드를 찾았습니다.');
    }
});
```

---

### Reference
- [자바스크립트에서 당장 사용해야 할 5가지의 배열 메소드들 (Array)](http://blog.kazikai.net/?p=16)
- [Array 객체에서 놓치기 쉬운 6개의 메서드 ](http://programmingsummaries.tistory.com/357)
- [JavaScript Reduce 함수](https://gamecodingschool.org/2015/06/16/javascript-reduce-함수/)
