---
title: JavaScript 05. 제어문
categories: [javascript]
comments: true
---

# 제어문

Control flow statement은 조건에 따라 코드 블록을 실행(조건문)하거나 반복 실행(반복문)할 때 사용한다. 제어문을 사용하면 코드의 실행 흐름을 인위적으로 제어할 수 있다.

## 블록문

Block statement/compound statement블록문은 0개 이상의 문을 중괄호로 묶은 것으로 코드 블록 또는 블록이라고 부른다. 자바스크립트는 블록문을 하나의 실행 단위로 취급한다. 블록문은 단독으로 사용할 수도 있으나 일반적으로 제어문이나 ㅎ마수를 정의할 때 사용한다. 블록문은 항상 문의 종료를 의미하는 자체 종결성을 갖기 때문에 블록문의 끝에는 세미콜론을 붙이지 않는다.


```javascript
// 블록문
{
    var tomato = 10;
}

// 제어문
var tomato = 1;
if (tomato < 10) {
    tomato++
}

// 함수 선언문
function sum(a, b){
    return a + b;
}
```

## 조건문

Conditional statement은 주어진 conditional expression조건식의 평가 결과에 따라 코드블록(블록문)의 실행을 결정한다. 조건식은 불리언 값으로 평가될 수 있는 표현식이다. 자바스크립트는 if..else 문과 switch 문으로 두 가지 조건문을 제공한다.

### if...else 문

if...else 문은 주어진 조건식의 평가 결과, 즉 논리적 참 또는 거짓에 따라 실행할 코드 블록을 결정한다. 조건식의 평가 결과가 true일 경우 if 문의 코드 블록이 실행되고 false일 경우 else 문의 코드 블록이 실행된다. 

```javascript
if (조건식) {
    // 조건식이 참이면 이 코드 블록이 실행된다.
} else {
    // 조건식이 거짓이면 이 코드 블록이 실행된다.
}
```

if 문의 조건식은 불리언 값으로 평가되어야 한다. 만약 if 문의 조건식이 불리언 값이 아닌 값으로 평가되면 자바스크립트 엔진에 의해 암묵적으로 불리언 값으로 강제 변환되어 실행할 코드 블록을 결정한다.

조건식을 추가하여 조건에 따라 실행될 코드 블록을 늘리고 싶으면 else if 문을 사용한다. else if 문과 else 문은 옵션이다. 사용할 수도 있고 사용하지 않을 수도 있다. if 문과 else 문은 2번 이상 사용할 수 없지만 else if 문은 여러 번 사용할 수 있다.

```javascript
var num = 2;
var kind;

// if 문
if (num > 0){
    kind = '양수';
} 
console.log(kind); // '양수'
// 이 경우 음수는 구별할 수 없다.

// if...else 문
if (num > 0){
    kind = '양수';
} else {
    kind = '음수';
}
console.log(kind); // '양수'
// 이 경우 0은 구별할 수 없다.

// if...else 문
if (num > 0){
    kind = '양수';
} else if (num < 0) {
    kind = '음수';
} else {
    kind = '0'
}
console.log(kind); // '양수'
// 양수, 음수, 0 인 모든 경우를 구별할 수 있다.
```

대부분의 if...else 문은 삼항 조건 연산자로 바꿔 쓸수도 있다.

```javascript
// tomato가 짝수이면 result 변수에 문자열 '짝수'를 할당하고, 홀수이면 문자열 '홀수'를 할당한다.

// if...else 문
var tomato = 2;
var result;

if (tomato % 2) { // tomato를 2로 나누었을때 나머지가 0이라면 짝수이다. 이때 0은 false로 암묵적 강제 변환된다.  
    result = '홀수';
} else {
    result = '짝수';
}

console.log(result); // 짝수

// 삼항 조건 연산자
var tomato = 2;
var result = x % 2 ? '홀수' : '짝수';
console.log(result); // 짝수
```

만약 경우의 수가 세가지('양수', '음수', '0')라면 다음과 같이 쓸 수 있다. 

```javascript
var tomato = 2;
var kind = tomato ? (tomato > 0 ? '양수' : '음수' ) : '0';

console.log(kind); // 양수
```

if...else 문은 표현식이 아니기 때문에 변수에 할당할 수 없지만 삼항 조건 연산자 표현식은 값처럼 사용할 수 있기 때문에 변수에 할당할 수 있다. 조건에 따라 단순히 값을 결정하여 변수에 할당하는 경우 삼항 조건 연산자를 사용하는 편이 가독성이 좋고 조건에 따라 실행해야 할 내용이 복잡하여 여러 줄의 문이 필요하다면 if...else 문을 사용하는 편이 가독성이 좋다.

### switch 문

switch 문은 주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case 문으로 실행 흐름을 옮긴다. case 문은 상황(case)을 의미하는 표현식을 지정하고 세미콜론으로 마친다. 그리고 그 뒤에 실행할 문들을 위치시킨다. switch 문의 표현식과 일치하는 case 문이 없다면 실행 순서는 default 문으로 이동한다. default 문은 사용할 수도 있고 사용하지 않을 수도 있다.

```javascript 
switch (표현식) {
    case 표현식1:
       (switch 문의 표현식과 표현식1이 일치하면 실행될 문)
       break;
    case 표현식2:
        (switch 문의 표현식과 표현식2가 일치하면 실행될 문)
        break;
    default:
        (switch 문의 표현식과 일치하는 case 문이 없을 때 실행될 문);     
}
```

if...else 문의 조건식은 불리언 값으로 평가되어야 하지만 switch 문의 표현식은 불리언 값보다는 문자열이나 숫자 값인 경우가 많다. 다시 말해 if...else문은 논리적 참, 거짓으로 실행할 코드 블록을 결정하는 반면 switch 문은 다양한 상황(case)에 따라 실행할 코드 블록을 결정할 때 사용한다.

break 문은 코드 블록에서 탈출하는 역할을 한다. break 문이 없다면 case 문의 표현식과 일치하더라도 실행 흐름이 다음 case 문으로 연이어 이동한다. 표현식의 평가 결과와 일치하는 case 문으로 실행흐름이 이동하여 문을 실행하더라도 switch 문을 탈출하지 않고 이후의 모든 case 문과 default 문을 실행한다. 이를 fall through 폴 스루라고 한다. default 문에는 일반적으로 break 문을 생략한다. default 문은 switch 문의 맨 마지막에 위치하므로 default 문의 실행이 종료되면 switch 문을 빠져나온다. 


```javascript 
// break 문이 없는 경우.
var day = 7
var dayname

switch (day) {
    case 1 : dayname = 'Mon'
    case 2 : dayname = 'Tue'
    case 3 : dayname = 'Wed'
    case 4 : dayname = 'Thu'
    case 5 : dayname = 'Fri'
    case 6 : dayname = 'Sta'
    case 7 : dayname = 'Sun'
    default : dayname = 'invalid dayname'
}

console.log(dayname); // invalid dayname
```

```javascript 
// break 문이 있는 경우.
var day = 7
var dayname

switch (day) {
    case 1 : dayname = 'Mon'
        break;
    case 2 : dayname = 'Tue'
        break;
    case 3 : dayname = 'Wed'
        break;
    case 4 : dayname = 'Thu'
        break;
    case 5 : dayname = 'Fri'
        break;
    case 6 : dayname = 'Sta'
        break;
    case 7 : dayname = 'Sun'
        break;
    default : dayname = 'invalid dayname'
}

console.log(dayname); // 'Sun'
```

break 문을 생략한 폴스루가 유용한 경우도 있다. 폴스루를 활용해 여러 개의 case 문을 하나의 조건으로 사용할 수도 있다.

```javascript
// 윤년인지 판별하여 2월의 일수를 계산하는 예제.

var year = 2000; // 2000년도는 윤년으로 2월이 29일이다.
var month = 2
var days = 0;

switch (month) {
    case 1: case 3:  case 5: case 7: case 8: case 10: case 12:
        days = 31;
        break;
    case 4: case 6: case 9: case 11:
        days = 30;
        break;
    case 2:
        // 1. 연도가 4로 나누어 떨어지는 해는 윤년이다.
        // 2. 연도가 4로 나누어 떨어지더라도 연도가 100으로 나누어 떨어지는 해는 평년이다.
        // 3. 연도가 400으로 나누어 떨어지는 해는 윤년이다
        days = ((year % 4 === 0 && year % 100 !== 0)) || (year % 400 === 0)) ? 29 : 28;
        break
    default:
        console.log('Invalid month');
}

console.log(days) // 29
```

만약 if...else 문으로 해결할 수 있다면 switch 문보다 if...else 문을 사용하는 편이 좋다. 하지만 조건이 너무 많아서 if...else 문보다 switch 문을 사용했을 때 가독성이 더 좋다면 switch 문을 사용하는 것이 좋다.

## 반복문

Loop statement 반복문은 조건식의 평가 결과가 참인 경우 코드 블록을 실행한다. 그 후 조건식을 다시 평가하여 여전히 참인 경우는 코드 블록을 다시 실행하고 거짓인 경우 실행을 멈춘다. 자바스크립트는 세 가지 반복문인 for 문, while 문, do...while 문을 제공한다. 자바스크립트는 이외에도 forEach() 메소드, for ...in 문, for ...of 문과 같이 반복문을 대체할 수 있는 다양한 기능을 제공한다.

### for 문

for 문은 조건식이 거짓으로 평가될 때까지 코드 블록을 반복 실행한다. 

```javascript
for (변수 선언문 또는 할당문; 조건식; 증감식) {
     조건식이 참인 경우 반복 실행될 문;
}
```


```javascript
for (var i = 0; i < 2; i++ ){
    console.log(i);
}

// 0
// 1
```
1) for 문을 실행하면 먼저 변수 선언문 var i = 0 이 실행된다. 변수 선언문은 단 한번만 실행된다.
2) 변수 선언문의 실행이 종료되면 조건식이 실행된다. 현재 변수 i 의 값은 0이므로 조건식의 평가 결과는 ture다.
3) 조건식의 평가 결과가 true이므로 코드블록이 실행된다. 
4) 코드 블록의 실행이 종료되면 증감식 i++ 이 실행되어 변수 i 의 값은 1이 된다.
5) 다시 조건식이 실행된다. 변수 i 의 값이 1이므로 평과 결과는 true이다.
6) 조건식의 평가 결과가 true이므로 코드 블록이 다시 실행된다.
7) 코드 블록의 실행이 종료되면 증감식 i++ 이 실행되어 변수 i 의 값은 2가 된다.
8) 다시 조건식이 실행된다 현재 변수 i 의 값은 2이므로 평가 결과는 false이다. 조건식의 평가 결과가 false 이므로 for 문의 실행이 종료된다.


for 문 내에 for 문을 중첩해 사용할 수 있다. 이를 중첩 for 문이라 한다.
```javascript
// 주사위의 두 눈의 합이 6이 되는 모든 경우의 수를 출력하는 코드.
for (var i =  1; i <= 6; i++){
    for (var j = 1; j <= 6; j++){
        if (i + j === 6) console.log(`[${i}, ${j}]`);
    }
}

// [1, 5]
// [2, 4]
// [3, 3]
// [4, 2]
// [5, 1]
```

### While 문

while 문은 주어진 조건식의 평가 결과가 참이면 코드 블록을 계속해서 반복 실행한다. for 문은 반복 횟수가 명확할때 주로 사용하고 while 문은 반복 횟수가 불명확할때 주로 사용한다. while 문은 조건문의 평가 결과가 거짓이 되면 코드 블록을 실행하지 않고 종료한다. 만약 조건식의 평가 결과가 불리언 값이 아니면 불리언 값으로 강제 변환하여 논리적 참, 거짓을 구별한다.

```javascript
var count = 0;

// count가 3보다 작을 때까지 코드 블록을 계속 반복 실행한다.
while (count < 3) {
    console.log(count);
    count++
}

// 0
// 1
// 2
```

조건식의 평가 결과가 언제나 참이면 무한루프가 된다. 무한 루프에서 탈출하기 위해서는 코드 블록 내에 if 문으로 탈출 조건을 만들고 break 문으로 코드 블록을 탈출한다.
```javascript
// 무한루프
while (ture) {...} 
```

```javascript
var count = 0;

while (true) {
    console.log(count);
    count++;
    if (count === 3) break;
    // count가 3면 코드 블록을 탈출한다.
}

// 0
// 1
// 2
```

### do...while 문

 