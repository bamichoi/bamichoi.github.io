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

null 타입 : 값이 없다는 것을 의도적으로 명시할 때 사용되는 값

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

## 문자열 타입

String문자열 타입은 텍스트 데이터를 나타내는 데 사용한다. 문자열은 0개 이상의 16비트 유니코드 문자(UTF-16)의 집합으로 전 세계 대부분의 문자를 표현할 수 있다. 
문자열은 작은따옴표(''), 큰따옴표(""), 백틱(``)으로 텍스트를 감싼다. 자바스크립트에서 가장 일반적인 표기법은 작은따옴표를 사용하는 것이다.

```javascript
var string;
string = '문자열'; // 작은따옴표
string = "문자열"; // 큰따옴표
string = `문자열`; // 백틱

string = '작은따옴표로 감싼 문자열 내의 "큰따옴표"는 문자열로 인식된다';
string = "큰따옴표로 감싼 문자열 내의 '작은따옴표'는 문자열로 인식된다";
```

다른 타입의 값과 달리 문자열을 따옴표로 감싸는 것은 키워드나 식별자 같은 토큰과 구분하기 위해서다. 또한 따옴표로 문자열을 감쌈으로써 공백 문자도 포함시킬 수 있다. 자바스크립트의 문자열은 원시타입이며 immutable value변경 불가능한 값이다. 즉, 문자열이 생성되면 그 문자열을 변경할 수 없다.


## 템플릿 리터럴


## 불리언 타입

불리언 타입의 값에는 논리적 참, 거짓을 나타내는 true와 false가 있다. 조건문에서 자주 사용된다.

```javascript
var tomato = true;
console.log(tomato); // ture

tomato = false;
console.log(tomato); // false
```


## undefined 타입

var 키워드로 선언한 변수는 암묵적으로 undefined로 초기화된다. 자바스크립트 엔진은 변수 선언에 의해 확보된 메모리 공간을 첫 할당이 이루어질때까지 빈 상태(대부분 비어 있지 않고 garbage value쓰레기 값가 들어있다)로 내버려두지 않고 undefined로 초기화한다. 따라서 변수를 선언한 이후 값을 할당하지 않은 변수를 참조하면 undefined가 반환된다.

```javascript
var tomato;
console.log(tomato); // undefined
```
undefined는 개발자가 의도적으로 할당하기 위한 값이 아니라 자바스크립트 엔진이 변수를 초기화할 때 사용하는 값이다. 변수를 참조했을 때 undefined가 반환된다면 참조한 변수가 선언 이후 값이 할당된 적이 없는 변수라는 것을 알 수 있다. 개발자가 의도적으로 사용하는 것은 undefined의 취지와 어긋나는데다 혼란을 줄 수도 있으므로 권장되지 않는다. 값이 없다는 것을 명시하고 싶을때는 undefined대신 null을 할당한다.

## null 타입

null타입의 값은 null이 유일하다. 자바스크립트는 대소문자를 구별하므로 null은 Null, NULL 등으로 쓰일 수 없다. null은 변수에 값이 없다는 것을 의도적으로 명시(intentional absence)할 때 사용한다. null을 사용하는 것은 할당되어 있던 값에 대한 참조를 명시적으로 제거하는 것을 의미한다.

```javascript
var tomato = 'pomodoro';

tomato = null;
// 이전 참조를 제거. tomato는 더 이상 'pomodoro'를 참조하지 않는다.
```
함수가 유효한 값을 반환할 수 없는 경우 명시적으로 null을 반환하기도 한다. 예를 들어 html요소를 검색해 반환하는 document.querySelector 메소드는 조건에 부합하는 요소를 검색할 수 없을 경우 에러 대신 null을 반환한다.

## 심벌 타입

ES6에서 추가된 7번째 타입. 변경 불가능한 원시 타입의 값이다. 심벌 값은 다른 값과 중복되지 않은 유일무이한 값이다. 주로 이름이 충돌할 위험이 없는 객체의 유일한 프로퍼티 키를 만들기 위해 사용한다. 심벌은 Symbol() 함수를 호출해 생성한다. 이때 생성된 심벌 값은 외부에 노출됮 ㅣ않으며 다른 값과 절대 중복되지 않는 유일한 값이다.

```javascript
var tomato = Symbol('key') // 심벌 값 생성
console.log(typeof key); // symbol

var obj ={}; // object 생성

obj[key] = 'value'; // 충돌할 위험이없는 심벌 값을 프로퍼티 키로 사용한다.
console.log(obj[key]); // value
```

## 객체 타입

자바스크립트는 객체 기반의 언어다. 자바스크립트를 이루고 있는 거의 모든 것이 객체다. 6가지 원시타입의 데이터 이외의 값은 모두 객체 타입이다.

## 데이터 타입은 왜 필요한가?

- 값을 저장할 때 확보해야 하는 메모리 공간의 크기를 결정하기 위해
- 값을 참조할 때 한 번에 읽어 들여야할 메모리 공간의 크기를 결정하기 위해
- 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정하기 위해

메모리에 값을 저장하려면 먼자 확보해야할 메모리 공간의 크기를 결정해야 한다. 변수에 할당되는 값의 데이터 타입에 따라 확보해야할 메모리 공간의 크기가 결정된다. 이로써 메모리 공간의 낭비와 손실 없이 값을 저장할 수 있다. 값을 참조하는 경우 식별자를 통해 값이 저장되어 잇는 메모리 공간의 선두 메모리 셀을 찾아가게 되는데 데이터 타입에 따라 한번에 읽어 들여야 할 메모리 공간의 크기, 즉 메모리 셀의 개수(바이트 수)가 결정된다. 이렇게 메모리에서 읽어들인 2진수는 데이터 타입에 따라 어떻게 해석할 것인지가 결정된다.

## 동적 타이핑

C나 Java등의 static/strong type정적 타입 언어들은 변수를 선언할 때 변수에 할당할 수 있는 데이터 타입을 사전에 선언해야 한다. 이를 explicit type declation이라고 한다. 반면 자바스크립트는  변수를 선언할때 타입을 선언하지 않는다. 정적 타입 언어에서는 변수 선언 시점에 변수의 타입이 결정되고 이후에는 변수의 타입을 변경할 수 없다. 자바스크립트에서는 값을 할당하는 시점에 변수의 타입이 동적으로 결정되고 타입을 언제든지 자유롭게 변경할 수 있다.
자바스크립트의 변수는 선언이 아닌 할당에 의해 타입이 결정(type inference타입 추론)이 된다. 그리고 재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다. 이러한 특징을 dynamic typing동적 타이핑이라고 하며 이러한 특징을 가진 언어를 dynamic/weak type동적 타입 언어라고 한다. 

```javascript
var tomato;
console.log(typeof tomato) // undefined

tomato = 3;
console.log(typeof tomato) // number

tomato = 'Hello';
console.log(typeof tomato) // string

tomato = true;
console.log(typeof tomato) // boolean

tomato = null;
console.log(typeof tomato) // null

tomato = null;
console.log(typeof tomato) // object

tomato = Symbol();
console.log(typeof tomato); // symbol

tomato = {};
console.log(typeof tomato) // object

tomato = [];
console.log(typeof tomato) // object

tomato = funtion();
console.log(typeof tomato) // funtion
```

동적 타입 언어는 변수에 어떤 데이터 타입의 값이라도 자유롭게 할당할 수 있지만 값의 변경에 의해 타입도 언제든지 변경될 수 있다. 따라서 동적 타입 언어의 변수는 값을 확인하기 전에는 타입을 확신할 수 없다. 또한 자바스크립트는 개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동적으로 변환 되기도 한다. 결국 동적 타입 언어는 flexbility유연성은 높지만 reliability신뢰성은 떨어진다. 이러한 이유로 안정적인 프로그램을 만들기 위해 변수를 사용하기 이전에 데이터 타입을 체크해야하는 경우도 있는데 번거롭기도하고 코드의 양도 많아지게 된다.

### 변수를 사용할 때의 주의사항

- 변수는 꼭 필요한 경우에 한해 제한적으로 사용한다. 자바스크립트에서는 재할당에 의해 타입이 얼마든지 변경될 수 있기 때문에 변수의 개수가 많으면 많을 수록 오류가 발생할 확률도 높아진다. 따라서 변수를 무분별하게 남발하기보다는 필요한만큼 최소한으로 유지하도록 주의해야 한다.
- 변수의 유효범위(스코프)는 최대한 좁게 만들어 변수의 부작용을 억제해야 한다. 변수의 유효범위가 넓으면 넓을 수록 변수로 인해 오류가 발생할 확률이 높아진다.
- 전역변수는 최대한 사용하지 않도록 한다. 어디서든지 참조/변경 가능한 전역변수는 의도치 않게 값이 변경될 가능성이 높고 다른 코드에 영향을 줄 가능성도 높다. 따라서 전역 변수는 프로그램의 복잡성을 증가시키고 처리 흐름을 추적하기 어렵게 만들고 오류가 발생할 경우 오류의 원인을 특정하기 어렵게 만든다.
- 변수보다는 상수를 사용해 값의 변경을 억제한다.
- 변수 이름은 변수의 목적이나 의미를 파악할 수 있도록 네이밍한다. 변수 뿐아니라 모든 식별자는 그 존재 이유를 파악할 수 있는 적절한 이름으로 지어야 한다. 특히 식별자의 유효범위가 넓을 수록 명확한 이름을 명명하도록 해야한다. 개발자의 의도를 나ㅏ내는 명확한 네이밍은 코드를 이해하기 쉽게 만들고, 이는 협업과 생산성 향상에 도움을 준다.
  
코드는 오해하지 않도록 작성해야한다. 코드는 동작하는 것만이 존재목적은 아니다. 코드는 개발자를 위한 문서이기도 하다. 따라서 사람이 이해할 수 있는 코드, 즉 가독성이 좋은 코드가 좋은 코드다.