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

### 문자열 연결 연산자

'+' 연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작한다. 그 외의 경우는 산술 연산자로 동작한다.
개발자의 의도와는 상관없이 암묵적으로 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다. 이를 implicit coerction암묵적 타입 변환 혹은 type coericon강제 타입 벼환이라고 한다. 

```javascript
// 문자열 연결 연산자
'1' + 2; // '12'

// 산술 연산자
1 + 2 // 3

// true는 1로, fasle는 0으로 타입 변환된다.
1 + true; // 2
1 + false; // 1

// null은 0으로 타입변환된다.
1 + null; // 1

// undefined는 숫자 타입으로 변환되지 않는다.
+undefined; // NaN
1 + undefined; // NaN
```

## 할당 연산자

Assignment operator할당 연산자는 우항에 있는 피연산자의 평가 결과를 좌항에 잇는 변수에 할당한다. 할당 연산자는 좌항의 변수에 값을 할당하므로 변수의 값이 변하는 부수효과가 있다.

- = : 예) x = 5
- += : 예) x = x + 5
- -= : 예) x = x - 5
- *= : 예) x = x * 5
- /= : 예) x = x / 5
- %= : 예) x = x % 5

```javascript
var tomato;

tomato = 10;
console.log(tomato); // 10

tomato += 5; // tomato = tomato + 5
console.log(tomato); // 15

tomato -= 5; // tomato = tomato - 5
console.log(tomato); // 10

tomato *= 5; // tomato = tomato * 5
console.log(tomato); // 50

tomato /= 5; // tomato = tomato / 5 
console.log(tomato); // 10

toamto %= 5; // tomato = tomato % 5
console.log(tomato); // 0

// 문자열 연결 연산자
var str = "My name is ";
str += "tomato"; // str = str + "tomato";
consloe.log(str); // "My name is tomato"
```

할당문은 값으로 평가되는 표현식인 문으로서 할당된 값으로 평가된다. 이러한 특징을 활용해 여러 변수에 동일한 값을 연쇄 할당할 수도 있다.
```javascript
a = b = c = 0;
// 오른쪽에서 왼쪽으로 진행하며 연쇄 할당된다.
// 1) c = 0 
// 2) b = 0
// 3) a = 0

console.log(a, b, c); // 0 0 0 
```


## 비교 연산자

Comparison operator비교 연산자는 좌항과 우항의 피연산자를 비교한 다음 그 결과를 불리언 값으로 반환한다. 주로 if 문이나 for 문과 같은 제어문의 조건식에서 주로 사용한다.

### 동등/일치 비교 연산자

loose equality동등 비교 연산자와 strict equality일치 비교 연산자는 좌항과 우항의 피연산자가 같은 값으로 평가되는지 비교해 불리언 값을 반환한다. 동등 비교 연산자는 느슨한 비교를하고 일치 비교 연산자는 엄격한 비교를 한다. 

- == : 동등 비교. x와 y의 값이 같음. 
- === : 일치 비교. x와 y의 값과 타입이 같음.
- != : 부동등 비교. x와 y의 값이 다름.
- !== : 불일치 비교. x와 y의 값과 타입이 다름.

동등 비교 연산자(==)는 좌항과 우항의 피연산자를 비교할때 먼저 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교한다. 따라서 동등 비교 연산자는 좌항과 우항의 피연산자가 타입은 다르더라도 암묵적 타입 변환 후에 같은 값일 수 있다면 true를 반환한다.

```javascript
//동등 비교
5 == 5; // true
5 == '5' // true 타입은 다르지만 암묵적 타입 변환을 통해 타입을 일치시키면 동등하다.
```
동등 비교 연산는 편리하지만 결과를 예측하기 어렵고 실수하기 쉽다. 대신 일치 비교(===) 연산자를 사용하는 것이 권장된다.
일치 비교 연산자(===)는 좌항과 우항의 피연산자가 타입도 같고 값도 같은 경우에 한하여 true를 반환한다. 즉, 암묵적 타입 변환을 하지 않고 값을 비교한다.

```javascript
// 일치 비교
5 === 5; // true
5 == '5' // false 타입이 다르다.
```

일치 비교 연산자에서 주의할 것은 NaN과 0이다. NaN은 자신과 일치하지 않는 유일한 값이다.
```javascript
NaN === NaN; // false
```
숫자가 NaN인지 검사하려면 빌트인 함수 isNaN()을 사용할 수 있다. isNaN()은 지정한 값이 NaN인지 확인하고 그 결과를 불리언 값으로 반환한다.
```javascript
isNaN(NaN); // true
isNaN(10); // false
isNaN(1 + undefined); // true
```
자바 스크립트에는 양의 0과 음의 0이 있는데 이들을 비교하면 동등/일치 비교 모두 true를 반환한다.
```javascript
0 === -0; // true
0 == -0; // true
```

다만 ES6에서 도입된 Object.is() 메소드는 0과 NaN에 대해서도 예측 가능한 정확한 비교 결과를 반환한다.
```javascript
Object.is(-0, +0); // false
Object.is(NaN, NaN); // true
```

부동등 비교 연산자(!=)와 불일치 비교 연산자(!==)는 동등/일치 비교 연산자의 반대 개념이다.

### 대소 관계 비교 연산자

대소 관계 비교 연산자는 피연산자의 크기를 비교하여 불리언 값으로 반환한다.

- '>' : x > y ( x가 y보다 크다 )
- '<' : x < y ( x가 y보다 작다 )
- '>=' : x >= y ( x가 y보다 같거나 크다 )
- '<=' : x <= y ( x가 y보다 작거나 크다 )

```javascript
//대소 관계 비교

5 > 0; // ture
5 > 5 // false
5 => 5; // true
5 <= 5; // true
```

### 삼항 조건 연산자

Ternary operator는 조건식의 평가 결과에 따라 반환할 값을 결정한다. 자바스크립트의 유일한 삼항 연산자이며 부수 효과는 없다. 

조건식 ? 조건식이 true일 때 반환할 값 : 조건식이 false일때 반환할 값

```javascript
var result = tomato >= 60 ? 'pass' : 'fail';

//tomato가 60보다 같거나 크면 result에는 'pass'가 반환된다. 그렇지 않다면 'fail'이 반환된다.
```
? 앞의 조건식은 불리언 타입의 값으로 평가될 표현식이다. 만약 조건식의 평가 결과가 불리언 값이 아니면 불리언 값으로 암묵적 타입 변환된다. 조건식이 참이면 콜론(:) 앞의 두 번째 피연산자가 평가되어 반환되고 거짓이면 콜론(:) 뒤의 세 번째 피연산자가 평가되어 반환된다.

```javascript
var tomato = 2;

var result = tomato % 2 ? '홀수' : '짝수';
console.log(result) // 짝수
// 2 % 2 는 0이고 0은 false로 암묵적 타입 변환되어 세번째 피연산자가 평가되어 반환되었다.
```

### 논리 연산자

 Logical operator논리 연산자는 우항과 좌항의 피연산자(부정 논리 연산자의 경우 우항의 피연산자)를 논리 연산자라고 한다.

- || : 논리합(OR)
- && : 논리곱(AND)
- ! : 부정(NOT)
  
 ```javascript
 // 논리합(||) 연산자
true || true; // true
true || false; // true
false || true; // true
false || false; // false
 

 // 논리곱(&&) 연산자
true && true; // ture
true && false; // flase
false && true; // false
false && false; // false

// 논리부정(!) 연산자
!true; // false
!false; // true
 ```

논리 부정(!) 연산자는 언제나 불리언 값을 반환한다. 하지만 피연산자가 반드시 불리언 값일 필요는 없다. 만약 피연산자가 불리언 값이 아니면 불리언 타입으로 암묵적 타입 변환된다.

```javascript
!0; // true
!'Hello' // false
```
논리합(||) 또는 논리곱(&&) 연산자 표현식의 평가 결과는 불리언 값이 아닐 수도 있다. 논리합(||) 또는 논리곱(&&) 연산자 표현식은 언제나 2개의 연산자 중 어느 한쪽으로 평가된다(단축평가).

### 쉼표 연산자

쉼표(,) 연산자는 왼쪽 피연산자부터 차례대로 피연산자를 평가하고 마지막 피연산자의 평가가 끝나면 마지막 피연산자의 평가 결과를 반환한다.

```javascript
var x, y, z;
x = 1, y = 2, z = 3 // 3
```

### 그룹 연산자

소괄호'()'로 피연산자를 감싸는 그룹 연산자는 자신의 피연산자인 표현식을 가장 먼저 평가한다. 따라서 그룹 연산자를 사용하면 연산자의 우선순위를 조정할 수 있다. 그룹 연산자는 연산자 우선순위가 가장 높다.

```javascript
10 * 2 + 3; // 23

//그룹 연산자를 사용하여 우선순위를 조절
10 * ( 2 + 3 ); // 50
```

### typeof 연산자

typeof 연산자는 피연산자의 데이터 타입을 문자열로 반환한다. typeof 연산자가 반환하는 문자열은 7개의 데이터 타입과 정확하게 일치하지는 않는다. typeof 연산자는 7가지 문자열 "string", "number", "boolean", "undefined", "symbol", "object, "function" 중 하나를 반환한다. null을 반환하는 경우는 없고 함수의 경우에는 function을 반환한다. 

```javascript
typeof '' // "string"
typeof 1 // "number"
typeof NaN // "number"
typeof true // "boolean"
typeof undefined // "undefined"
typeof Syombol() // "symbol"
typeof null // "null"
typeof [] // "object"
typeof {} // "objecgt"
typeof new Date() // "object"
typeof /test/gi // "object"
typeof funtion(){} // "object"
)
```

typeof 연산자로 null의 값을 연산해 보면 "null"이 아닌 "object"를 반환한다. 따라서 null 타입인지 확인할 때에는 typeof 연산자 대신에 일치 연산자(===)를 사용해야한다.

선언하지 않은 연산자를 typeof 연산자로 연산해보면 ReferenceError가 아닌 undefined를 반환한다.
```javascript
typeof tomato; // undefined
```
