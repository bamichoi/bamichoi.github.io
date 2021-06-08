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

