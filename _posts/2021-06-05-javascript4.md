---
title: JavaScript 04. 연산자
categories: [javascript]
comments: true
---

# 연산자

Operator연산자는 하나 이상의 표현식을 대상으로 산술, 할당, 비교, 논리, 티입 operation지수연산 등을 수행해 하나의 값을 만든다. 이때 연산의 대상을 operand피연산자라 한다. 피연산자는 값으로 평가될 수 있는 표현식이어야하며 피연사자와 연산자의 조합으로 이뤄진 연산자 표현식도 값으로 평가될 수 있는 표현식이어야 한다.

```javascript
// 산술 연산자
5 * 4 // 20

// 문자열 연결 연산자
'My name is' + 'tomato' // 'My name is tomato"

//할당 연산자
color = 'red' // red

// 비교 연산자
3 > 5 // false

// 논리 연산자
true && false // false

// 타입 연산자
typeof 'Hi' // string
```

##  산술 연산자

Airthmetic operator산술연산자는 피연산자를 대상으로 수학적 계산을 수행해 새로운 숫자 값을 만든다. 산술 연산이 불가능한 경우, NaN을 반환한다. 산술 연산자는 피연산자의 개수에 따라 이항 산술연산자와 단항 산술 연산자로 구분된다.

### 이항 산술 연산자

이항(binary) 산술  연산자는 2개의 피연산자를 산술 연산하여 숫자 값을 만든다.
모든 이항 산술 연산자는 피연산자의 값을 변경하는 side effect부수 효과가 없다. 다시 말해, 어떤 산술 연산을 해도 피연산자의 값이 바뀌는 경우는 없고 언제나 새로운 값을 만들 뿐이다.

- +: 덧셈
- -: 뺄셈
- *: 곱셈
- /: 나눗셈
- %: 나머지
  
```javascript
5 + 2; // 7
5 - 2; // 3
5 * 2; // 10
5 / 2; // 2.5
5 % 2; // 1
```

### 단항 산술 연산자

단항(unary) 산술 연산자는 1개의 피연산자를 산술 연산하여 숫자 값을 만든다. 증가/감소(++/--) 연산자는 피연산자의 값을 변경하는 부수 효과가 있다.

- ++: 증가
- --: 감소
- +: 아무 효과도 없다. 사용해도 음수를 양수로 반전하지 않는다.
- -: 양수를 음수로, 음수를 양수로 반전한 값을 반환한다
  
```javascript
var tomato = 1;

tomato++; // tomato = tomato + 1;
console.log(tomato) // 2
// ++ 연산자는 피연산자의 값을 변경하는 암묵적 할당이 이뤄진다.

tomato--; // tomato = tomato - 1;
console.log(tomato) // 1
// -- 연산자는 피연산자의 값을 변경하는 암묵적 할당이 이뤄진다.
```
증가/감소(++/--) 연산자는 위치에 의미가 있다. 피연산자 앞에 위치한 증가/감소(++/--) 연산자는 prefix increment/decrement operator전위 증가/감소 연산자로 먼저 피연산자의 값을 증가/감소 시킨 후, 다른 연산을 수행한다. 반면 피연산자 뒤에 위치한 postfix increment/decrement operator후위 증가/감소 연산자로 먼저 다른 연산을 수행한 후, 피연산자의 값을 증가/감소 시킨다.

```javascript
var tomato = 5, result;

// postprefix inrement operator 선할당 후증가
result = tomato++;
console.log(result, tomato) // 5, 6

// pretprefix inrement operator 선증가 후할당
result = ++tomato;
console.log(result, tomato) // 7, 7
```

'+'단항 연산자는 피연산자에 어떠한 부수효과도 없다. 음수를 양수로 반전하지 않는다.

```javascript
+10; // +10
+(-10) // -10

// 아무런 효과도 없다.
```

숫자 타입이 아닌 피연산자에 + 단항 연산자를 사용하면 피연산자를 숫자 타입으로 변환하여 반환한다.

```javascript
//문자열을 숫자 타입으로 변환.
var tomato = '1'; 

console.log(+tomato); // 1 (number)
console.log(tomato); // '1' (string)

//불리언 값을 숫자 타입으로 변환.
var tomato = true; 

console.log(+tomato); // 1 (number)
console.log(tomato); // true (boolean)

//문자열을 숫자 타입으로 변환.
var tomato = 'pomodoro'; 

console.log(+tomato); // NaN (숫자 타입으로 변환할 수 없음)
console.log(tomato); // 'pomodoro' (string)
```

'-'단항 연산자는 피연산자의 부호를 반전한 값을 반환한다. +단항 연산자와 마찬가지로 숫자타입이 아닌 피연산자에 사용하면 피연산자를 숫자 타입으로 변환한다.
```javascript

-(-10); // 10

-'10'; // -10

-'true'; // -1

-'Hello'; // NaN
```