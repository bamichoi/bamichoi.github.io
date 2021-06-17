---
title: JavaScript 06. 타입 변환과 단축평가
categories: [javascript]
comments: true
---

# 타입 변환

자바스크립트의 모든 값은 타입이 있다. 값의 타입은 개발자의 의도에 따라 다른 타입으롭 ㅕㄴ환할 수 있다. 개발자가 의도적으로 값의 타입을 변환하는 것을 explicit coeration 명시적 타입 변환 또는 type casting 타입 캐스팅이라 한다.

```javascript
var tomato = 10;

var str = tomato.toString() // 명시적 타입 변환. 숫자를 문자열로 타입 캐스팅.
console.log(typeof str, str) // string, 10
console.log(typeof x, x); // number 10
// 변수 x 의 값이 변경된 것은 아니다.
```

개발자의 의도와는 상관없이 표현식을 평가하는 도중에 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다. 이를 implicit coericon 암묵적 타입 변환 또는 type coericon 타입 강제 변환이라 한다.

```javascript
var tomato = 10;

var str = tomato + ''; // 암묵적 타입 변환. 문자열 연결 연산자는 x의 값을 바탕으로 새로운 문자열을 생성한다.
console.log(typeof str, str) // string 10
console.log(typeof x, x) // number 10
// 변수 x 의 값이 변경된 것은 아니다.
```
명시적 타입 변환이나 암묵적 타입변환이 기존 원시 값을 직접 변경하는 ㅛ것은 아니다. 원시 값은 immutable value변경 불가능한 값이므로 변경할 수 없다. 타입 변환이란 기존 원시 값을 사용해 다른 타입의 새로운 원시 값을 생성하는 것이다. 

## 암묵적 타입 변환

자바스크립트 엔진은 표현식을 평가할 때 개발자의 의도와는 상관없이 코드의 문맥을 고려해 암묵적으로 데이터 타입을 강제 변환할 때가 있다.

```javascript
// 피연산자가 모두 문자열 타입이어야 하는 문맥
'10' + 2 // '102'

// 피연산자가 모두 숫자 타입이어야 하는 문맥
5 * '10' // 50

// 피연산자 또는 표현식이 불리언 타입이어야하는 문맥
!0 // true
```

이처럼 표현식을 평가할 때 코드의 문맥에 부합하는 다양한 상황이 발생할 수 있다. 이때 자바스크립트는 가급적 에러를 발생시키지 않도록 암묵적 타입 변환을 통해 표현식을 평가한다. 암묵적 타입 변환이 발생하면 문자열, 숫자, 불리언과 같은 원시 타입 중 하나로 타입을 자동 변환한다.

### 문자열 타입으로 변환

```javascript
1 + '2' // '12'
```

위 예제의 + 연산자는 피연산자 중 하나 이상이 문자열이므로 문자열 연결 연산자로 동작한다. 문자열 연결 연산자의 역할은 문자열 값을 만드는 것이다. 따라서 문자열 연결 연산자의 모든 피연산자는 코드의 문맥상 문자열 타입이어야 한다. 자바스크립트 엔진은 문자열 연결 연산자 표현식을 평가하기 위해 문자열 연결 연산자의 피연산자 중에서 문자열 타입이 아닌 피연산자를 문자열 타입으로 강제 변환한다.

자바스크립트 엔진은 문자열 타입 아닌 값을 문자열 타입으로 암묵적 타입 변환을 수행할 때 다음과 같이 동작한다.

```javascript
// 숫자 타입
0 + '' // "0"
-0 + '' // "0" 
1 + '' // "1"
-1 + '' // "-1"
NaN + '' // "NaN"
Infinity + '' // "Infinity"
-Infinity + '' // "-Infinity"

// 불리언 타입
true + '' // "true"
false + '' // "false"

// null 타입 
null + '' //  "null"

// undefined 타입
undefined + '' // "undefined"

// 심벌 타입
(Symbo()) + '' // TypeError : Cannot convert a Symbol value to a string

// 객체 타입
({}) + '' // "[obejct object]"
Math + '' // "[obejct Math]"
[] + '' // ""
[10, 20] + '' // "10, 20"
(function(){}) + '' // "function(){}"
Array + '' // "function Array() { [native code] }"
```


### 숫자 타입으로 변환

```javascript
1 - '1' // 0
1 * '10' // 10
1 / 'one' // NaN
```

위 예제에서 사용한 연산자는 모두 산ㄱ술 연산자다. 산술 연산자의 역ㄷ할은 숫자 값을 만드는 것이다. 산술연산자의 모든 피연산자는 코드 문맥상 모두 숫자 타입이어야 한다. 자바스크립트 엔진은 산술 연산자 표현식을 평가하기 위해 산술 연산자의 피연산자 중에서 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다. 이때 피연산자를 숫자 타입으로 변환할 수 없는 경우는 산술 연산을 수행할 수 없으므로 표현식의 평가결과는 NaN이 된다. 

비교 연산자 또한 피연산자를 숫자 타입으로 강제 변환한다.

```javascript
'1' > 0 // ture
```

비교 연산자의 역할은 불리언 값을 만드는 것이다. > 비교 연산자는 피연산자의 크기를 비교하므로 모든 피연산자는 코드의 문맥상 숫자 타입이어야한다. 자바스크립트 엔진은 비교 연산자 표현식을 평가하기 위해 비교 연산자의 피연산자 중에서 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다.

자바스크립트 엔진은 숫자 타입이 아닌 값을 숫자 타입으로 암묵적 타입 변환을 수행할 때 다음과 같이 동작한다. 즉, + 단항 연산자는 피연산자가 숫자 타입의 값이 아니면 숫자 타입의 값으로 암묵적 타입변환을 수행한다.

```javascript
// 문자열 타입
+ '' //0
+ '0' // 0
+ '1' // 1
+ 'string' // NaN

// 불리언 타입
+ true // 1
+ flase // 0

// null 타입
+null // 0

// undefined 타입
+undefined //  NaN

// 심벌 타입
+(Symbol()) // TypeError : Cannot convert a Symbol value to a string

// 객체 타입
+{} // NaN
+[] // 0
+[10, 20] // NaN
+(function(){}) + '' // NaN
```

빈문자열(''), 빈 배열([]), null, false는 true는 1로 변환된다. 객체와 빈 배열이 아닌 배열, undefined는 변환이 되지 않아 NaN이 된다.

### 불리언 타입으로 변환


if 문이나 for 문과 같은 제어문 또는 삼항 조건 연산자의 조건식은 불리언 값. 즉 논리적 참/거짓으로 평가되어야 하는 표현이다. 자바스크립트 엔진은 조건식의 평가 결과를 불리언 타입으로 암묵적 타입 변환한다. 이때 자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy 값(참으로 평가되는 값) 또는 Falsy 값(거짓으로 평가되는 값)으로 구분한다.즉 Truthy 값은 true로 Falsy 값은 false로 암묵적 타입 변환된다.

```javascript
if ('') console.log('1');
if (ture) console.log('2');
if (0) console.log('3');
if ('str') console.log('4');
if (null) console.log('5');
```

아래 값들은 false로 평가되는 Falsy 값이다.
- false
- undefined
- null
- 0, -0
- NaN
- '' (빈 문자열)

Falsy 값 외의 모든 값은 모두 true로 평가되는 Truthy 값이다.

```javascript
// 아래의 조건들은 모두 참으로 코드 블로글 실행한다.
if (!false) console.log("tomato") //tomato
if (!undefined) console.log("tomato") //tomato
if (!null) console.log("tomato") //tomato
if (!0) console.log("tomato") //tomato
if (!NaN) console.log("tomato") //tomato
if (!'') console.log("tomato") //tomato
```


## 명시적 타입 변환

개발자의 의도에 따라 명시적으로 타입을 변경하는 방법은 다양하다. 표준 빌트인 생성자 함수(String, Number, Boolean)를 new 연산자 없이 호출하는 방법과 빌트인 메소드를 사용하는 방법. 그리고 앞에서 살펴본 암묵적 타입 변환을 이용하는 방법이 있다.


### 문자열 타입으로 변환

- String 생성자 함수를 new 연산자 없이 호출하는 방법
- Object.prototype.toString 메소드를 사용하는 방법
- 문자열 연결 연산자를 이용하는 방법

```javascript
// 1. String 생성자 함수를 new 연산자 없이 호출하는 방법
// 숫자 타입 => 문자열 타입
String(1); // "1"
String(NaN); // "NaN"
String(Infinity) // "Infinity"

// 불리언 타입 => 문자열 타입
String(true) // "true"
String(false) // "false"

// 2. Object.prototype.toString 메소드를 사용하는 방법
// 숫자 타입 => 문자열 타입
(1).toString(); // 1
(NaN).toString(); // "NaN"
(Infinity).toString(); // "Infinity"

// 불리언 타입 => 문자열 타입
(true).toString(); // "true"
(false).toString(); // "false"

// 3. 문자열 연결 연산자를 이용하는 방법
// 숫자 타입 => 문자열 타입
1 + ''; // "1"
NaN + ''; // "NaN"
Infinity + ''; // "Infinity"

// 불리언 타입 => 문자열 타입
true + ''; // "true"
false + ''; // "false"
```

### 숫자 타입으로 변환

숫자 타입이 아닌 값을 숫자 타입으로 변환하는 방법은 다음과 같다.

- Number 생성자 함수를 new 연산자 없이 호출하는 방법
- parseInt, parseFloat 함수를 사용하는 방법(문자열만 숫자 타입으로 변환 가능)
- 단항 산술 연산자 +를 이용하는 방법
- 산술 연산자 *를 이용하는 방법
  
```javascript
// 1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 숫자 타입
Number('0'); // 0
Number('-1') // -1
Number('10.53') // 10.53

//불리언 타입 => 숫자 타입
Number(true); // 1
Number(false) //  0 

// 2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
// 문자열 타입 => 숫자 타입
parseInt('0') // 0
parseInt('-1') // -1
parseFloat('10.53') // 10.53

// 3. + 단항 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
+ '0'; // 0
+ '-1'; // -1
+ '10.53'; // 10.53

//불리언 타입 => 숫자 타입
+true; // 1
+false; // 0

// 4. * 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
'0' * 1; // 0
'-1' * 1; // -1
'10.53' * 1; // 10.53

// 불리언 타입 => 숫자 타입
true * 1; // 1
false * 1; // 0
```

### 불리언 타입으로 변환

불리언 타입이 아닌 값을 불리언 타입으로 변환하는 방법은 다음과 같다.

- Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
- ! 부정 논리 연산자를 두 번 사용하는 방법

```javascript
// 1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 불리언 타입
Boolean('x'); // true
Boolean(''); // false
Boolean('false'); // true

//숫자 타입 => 불리언 타입
Boolean(0); // false
Boolean(1); // true
Boolean(NaN); // false
Boolean(Infinity); // true

// null 타입 => 불리언 타입
Boolean(null); // false

// undefined 타입 => 불리언 타입
Boolean(undefined); // fasle

// 객체 타입 => 불리언 타입
Boolean({}); // true
Boolean([]); // true

// 2. ! 부정 논리 연산자를 두 번 사용하는 방법
// 문자열 타입 => 불리언 타입
!!'x' // true 
!!'' // false
!!'false' // true

// 숫자 타입 => 불리언 타입
!!0; // false
!!1; // true
!!NaN; // false
!!Infinity; // true

// undefined 타입 => 불리언 타입
!!undefined // false

// 객체 타입 => 불리언 타입
!!{}; // true
!![]; // true
```

# 단축 평가

### 논리 연산자를 사용한 단축 평가

논리합(||) 또는 논리곱(&&) 연산자 표현식의 평가 결과는 불리언 값이 아닐 수도 있다. 논리합(||) 또는 논리곱(&&) 연산자 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.

```javascript
'Cat' && 'Dog' // "Dog"
```

논리곱(&&) 연산자는 두 개의 피연산자가 모두 true로 평가 될 때 ture를 반환한다. 논리곱 연산자는 좌항에서 우항으로 평가가 진행된다. 첫번째 피연산자 'Cat'은 Truthy 값이므로 true로 평가된다. 하지만 이 시점까지는 위 표현식을 평가할 수 없다. 두 번째 피연산자까지 평가해 보아야 위 표현식을 평가할 수 있다. 다시 말해, 두 번째 피연산자가 논리곱 연산자 표현식의 평가 결과를 결정한다. 이때 논리곱 연산자는 논리 연산의 결과를 결정하는 두 번째 피연산자(문자열 'Dog')를 그대로 반환한다.

```javascript
'Cat' || 'Dog' // "Cat"
```

논리합(||) 연산자는 두 개의 피연산자 중 하나만 true로 평가되어도 true를 반환한다. 논리합 연산자도 좌항에서 우항으로 평가가 진행된다. 첫번째 피연산자 'Cat'은 Truthy 값이므로 ture로 평가된다. 이 시점에 두 번째 피연산자까지 평가해보지 않아도 위 표현식을 평가할 수 있따. 이때 논리합 연산자는 논리 연산의 결과를 결정한 첫 번째 피연산자, 즉 문자열 'Cat'을 그대로 반환한다.

논리곱(&&) 연산자와 논리합(||) 연산자는 이처럼 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환한다. 이를 short-circuit evaluation단축 평가라고 한다. 단축 평가는 표현식을 평가하는 도중에 평가 결과가 확정된 경우 나머지 평가 과정을 생략하는 거슬ㅇ 말한다. 대부분의 프로그래밍 언어는 단축 평가를 통해 논리 연산을 수행한다.

- 단축 평가의 규칙

1. ture || anything => true
2. false || anything => anything
3. true && anything => anything
4. false && anything => false

```javascript
// 논리합(||) 연산자
'Cat' || 'Dog' // "Cat"
false || 'Dog' // "Dog"
'Cat' || 'false' // "Cat"

// 논리곱(&&) 연산자
'Cat' && 'Dog' // "Dog"
false && 'Dog' // "false"
'Cat' && false // "false"
```

단축 평가를 사용하면 if 문을 대체할 수 있다. 어떤 조건이 Truthy 값(참으로 평가되는 값)일 때 무언가를 해야 한다면 논리곱(&&) 연산자 표현식으로 if 문을 대체할 수 있다.

```javascript
var done = true;
var message = '';

// 주어진 조건이 true일 때
if (done) message = '완료';

// if 문은 단축 평가로 대체 가능하다.
// done이 ture라면 message에 '완료'를 할당
message = done && '완료';
console.log(message); // 완료
```

조건이 Fasly 값(거짓으로 평가되는 값)일 때 무언가를 해야 한다면 논리합(||) 연산자 표현식으로 if 문을 대체할 수 있다.

```javascript
var done = false;
var message = '';

// 주어진 조건이 true일 때
if (!done) message = '미완료';

// if 문은 단축 평가로 대체 가능하다.
// done이 false라면 message에 '미완료'를 할당
message = done || '미완료';
console.log(message); // 미완료
```

단축평가는 다음과 같은 유용하게 사용될 수 있다.

- 객체가 가리키기를 기대하는 변수가 null 또는 undefined가 아닌지 확인하고 프로퍼티를 참조할 때. 객체는 키와 값으로 구성된 프로퍼티의 집합이다. 만약 객체를 가리키기를 기대하는 변수의 값이 객체가 아니라 null 또는 undefined인 경우 객체의 프로퍼티를 참조하면 TypeError 타입에러가 발생한다. 에러가 발생하면 프로그램이 강제 종료된다.

```javascript
var tomato = null;
var value = tomato.value; // TypeError: Cannot read property 'value' of null
```

이때 단축 평가를 사용하면 에러를 발생시키지 않는다.

```javascript
var tomato = null

// tomato가 null이나 undefined와 같은 Falsy 값이면 tomato로 평가되고 Truthy 값이면 tomato.value로 평가된다.
var value = tomato && tomato.value // null
```

- 함수 매개변수에 기본값을 설정할 때. 함수를 호출할때 인수를 전달하지 않으면 매개변수에는 undefined가 할당된다. 이땨ㅐ 단축 평가를 사용해 매개변수의 기본값을 설정하면 undefined로 인해 발생할 수 있는 에러를 방지할 수 있다.

```javascript
// 단축 평가를 사용한 매개변수의 기본값 설정 
function getStringLength(str) {
    str = str || '';
    return str.length;
}

getStringLength(); // 0
getStringLength('hi'); // 2 

// ES6dml 매개변수의 기본값 설정
function getStringLength(str = '') {
    return str.length;
}

getStringLength(); // 0
getStringLength('hi'); // 2 
```

### 옵셔널 체이닝 연산자

Optional Chaining옵셔널 체이닝 연산자 ?.는 좌항의 피연산자가 undefined인 경우 undefined를 반환하고 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.

```javascript
var tomato = null;

var value = tomato?.value;
console.log(value); // undefined
```

옵셔널 체이닝 연산자 ?.는 객체를 가리키기를 기대하는 변수가 null 또는 undefined가 아닌지 확인하고 프로퍼티를 참조할때 유용하다. 옵셔널 체이닝 연산자 ?.가 도입되기 이전에는 논리 연산자 &&를 사용한 단축 평가를 통해 변수가 null 또는 undefined인지 확인했다.


```javascript
var tomato = null;

var value = tomato && tomato.value;
console.log(value); // null
```
논리 연산자 &&는 좌항 피연산자가 false로 평가되는 Falsy 값(false, undefined, null 0, -0, NaN, '')이면 좌항 피연산자를 그대로 반환한다. 하지만 0이나 ''은 객체로 평가될 때도 있다.

```javascript
var tomato = ''

// 문자열의 길이(length)를 참조한다.
var length = tomato && tomato.length;

// 문자열의 길이를 참조하지 못한다
console.log(length); // ''
```

하지만 옵셔널 체이닝 연산자 ?.는 좌항 피연산자가 false로 평가되는 Falsy 값(false, undefined, null 0, -0, NaN, '')이라도 null 또는 undefined가 아니면 우항의 프로퍼티 참조를 이어간다.

```javascript
var tomato = ''

// 문자열의 길이(length)를 참조한다. 좌항 피연산작 Falsy 값이라도 null 또는 undefined가 아니면 우항의 프로퍼티 참조를 이어간다.
var length = tomato?.length;
console.log(length); // 0
```

