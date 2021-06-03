---
title: JavaScript 03. 데이터 타입
categories: [javascript]
comments: true
---

# 데이터 타입

Data type데이터 타입은 값의 종류를 말한다. 자바스크립트의 모든 값은 데이터 타입을 갖는다.
ES6는 7개의 데이터 타입을 제공한다. 7개의 데이터타입은 primitive type원시 타입과 object/reference type 객체 타입으로 분류할 수 있다.

- 원시타입 
  
number 숫자타입 : 숫자. 정수와 실수 구분없이 하나의 숫자 타입만 존재

string 문자열타입 : 문자열

boolean 불리언타입 : 논리적 true참과 false거짓

undefined 타입 : var 키워드로 선언된 변수에 암묵적으로 할당되는 값

null 타입 : 값이 없다는 것을 의돚거으로 명시할 때 사용되는 값

symbol 심벌타입 : ES6에서 추가된 7번째 타입


- 객체타입 : 객체, 함수, 배열 등


## 숫자 타입

다른 언어들은 정수와 실수를 구분하여 int, long, float, double 등 다양한 숫자 타입을 제공하지만 자바스크립트는 하나의 숫자 타입만 존재한다.
숫자 타입은 부동소수점 형식을 따른다. 즉 모든 수를 실수로 처리하며 정수만 표현하기 위한 데이터 타입이 별도로 존재하지 않는다.

```javascript
var integer = 10; // 정수
var double = 10.12; // 실수
var negative = -20; // 음의 정수
var binary = 0b0100001 // 2진수
var octal = 0o101; // 8진수
var hex = 0x41; // 16진수

// 자바스크립트에서는 모두 숫자 타입이다.
```

자바스크립트의 숫자타입은 모든 수를 실수로 처리하기 때문에 정수로 표시해도 사실은 실수다. 정수로 표시되는 수끼리 나누더라도 실수가 나올 수 있다.
```javascript
// 숫자 타입은 모두 실수로 처리된다.
console.log(1 === 1.0 ); //ture

// 정수끼리 나누더라도 실수가 나올 수 있다.
console.log(3 / 2); // 1.5
```

숫자타입은 추가적으로 세 가지 특별한 값도 표현할 수 있다.

Infinity : 양의 무한대
-Infinity : 음의 무한대
NaN : 산술 연산 불가 (not-a-number)

```javascript
console.log(10 / 0 ); //Infinity
console.log(10 / -0); //-Infinity
console.log(10 * 'tomato'); // NaN
```
자바스크립트는 대소문자를 구별(case-sensitive)하므로 NaN을 NAN, nan, Nan 등으로 표현하면 값이 아닌 식별자로 해석하여 에러가 발생한다.

kk