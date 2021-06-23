---
title: JavaScript 07. 객체 리터럴
categories: [javascript]
comments: true
---

# 객체 리터럴


## 객체

자바스크립트는 object객체 기반의 프로그래밍 언어이며, 원시 값을 제외한 자바스크립트를 구성하는 거의 모든 것이 객체다. 원시 타입은 단 하나의 값만 나타내지만 object/reference type은 다양한 타입의 값을 하나의 단위로 구성한 복합적인 data sctructure자료구조다. 또한 원시 타입의 값, 즉 원시 값은 immutable value변경 불가능한 값이지만 객체 타입의 값, 즉 객체는 mutable value변경 가능한 값이다. 객체는 0개 이상의 property프로퍼티로 구성된 집합이며, 프로퍼티는 key키와 value값으로 구성된다. 자바스크립트에서 사용할 수있는 모든 값은 프로퍼티 값이 될 수 있다. 자바스크립트의 함수는 일급 객체이므로 값으로 취급할 수 있다. 따라서 함수도 프로퍼티 값으로 사용할 수 있다. 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 method메소드라고 부른다.

```javascript
var tomato ={
    key : value, // property
    increase: function () {
        this.key++;
    }
};
```

이처럼 객체는 프로퍼티와 메소드로 구성된 집합체다. 프로퍼티와 메소드의 역할은 다음과 같다.

- Property프로퍼티 : 객체의 상태를 나타내는 값(data)
- Method메소드 : 프로퍼티(상태 데이터)를 참조하고 조작할 수 있는 동작(behavior)

이처럼 객체는 객체의 상태를 나타내는 값(property)와 프로퍼티를 참조하고 조작할 수 있는 동작(method)을 모두 포함할 수 있기 때문에 상태와 동작을 하나의 단위로 구조화할 수 있어 유용하다.


## 객체 리터럴에 의한 객체 생성

C++이나 자바 같은 클래스 기반 객체지향 언어는 클래스를 사전에 정의하고 필요한 시점에 new 연산자와 함께 contructor생성자를 호출하여 인스턴스를 생성하는 방식으로 객체를 생성한다.
(인스턴스란 클래스에 의해 생성되어 메모리에 저장된 실체를 말한다. 객체지향 프로그래밍에서 객체는 클래스와 인스턴스를 포함한 개념이다. 클래스는 인스턴스를 생성하기 위한 템플릿의 역할을 한다. 인스턴스는 객체가 메모리에 저장되어 실제로 존재하는 것에 초점을 맞춘 용어이다.)

자바스크립트는 프로토타입 기반 객체지향 언어로서 클래스 기반 객체지향 언어와는 달리 다양한 객체 생성 방법을 지원한다.

- 객체 리터럴
- Object 생성자 함수
- 생성자 함수
- Object.crate 메소드
- 클래스(es6)

이러한 객체 생성 방법 중에서 가장ㅇ 일반적이고 간단한 방법은 객체 리터럴을 사용하는 방법이다. literal리터럴은 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용하여 값을 생성하는 표기법을 말한다. 객체 리터럴은 객체를 생성하기 위한 표기법이다.
객체 리터럴은 중괄호({...}) 내에 0개 이상의 프로퍼티를 정의한다. 변수에 할당되는 시점에 자바스크립트 엔진은 객체 리터럴을 해석해 객체를 생성한다.

```javascript
var tomato = {
    name : 'bangto',
    sayHello : function () {
        console.log(`Hello! My name is ${this.name}.`);
    }
};

console.log(typeof tomato); // object
console.log(tomato); // {name :  "bangto", sayHelloj:f}
```

만약 중괄호 내에 프로퍼티를 정의하지 않으면 빈 객체가 생성된다.

```javascript
var tomato = {}; // 빈 객체
console.log(typeof tomato) // object
```
객체 리터럴의 중괄호는 코드 블록을 의미하지 않는다. 코드 블록의 닫는 중괄호 뒤에는 세미콜론을 붙이지 않는다. 하지만 객체 리터럴은 값으로 평가되는 표현식이다. 따라서 객체 리터럴의 닫는 중괄호 뒤에는 세미콜론을 붙인다.

객체 리터럴은 자바스크립트의 유연함과 강력함을 대표하는 객체 생성 방식이다. 객체를 새엉하기 위해 클레스를 먼저 정의하고 new 연산자와 함께 생성자를 호출할 필요가 없다. 숫자 값이나 문자열을 만드는 것과 유사하게 리터럴로 객체를 생성한다. 객체 리터럴에 프로퍼티를 포함시켜 객체를 생성함과 동시에 프로퍼티를 만들 수도 있고, 객체를 생성한 이후에 프로퍼티를 동적으로 추가할 수도 있다.


## 프로퍼티

객체는 프로퍼티의 집합이며, 프로퍼티는 키와 값으로 구성된다.

```javascript
var tomato = {
    name: 'Choi',  //프로퍼티 키는 name, 프로퍼티 값은 'Choi'
    age:20 //프로퍼티 키는 age, 프로퍼티 값은 20
} 
```

프로퍼티를 나열할 때는 쉼표(,)로 구분한다. 일반적으로 마지막 프로퍼티 뒤에는 쉼표를 사용하지 않으나 사용해도 좋다.
프로퍼티 키와 프로퍼티 값으로 사용할 수 있는 값은 다음과 같다.

- 프로퍼티 키 : 빈 문자열을 포함하는 모든 문자열 또는 심벌 값
- 프로퍼티 값 : 자바스크립트에서 사용할 수 있는 모든 값

프로퍼티 키는 프로퍼티 값에 접근할 수 있는 이름으로서 식별자 역할을 한다. 하지만 반드시 식별자 네이밍 규칙을 따라야하는 것은 아니다. 단 식별자 네이밍 규칙을 준수하는 프로퍼티 키와 그렇지 않은 프로퍼티 키는 미묘한 차이가 있다.

심벌 값도 프로퍼티 키로 사용할 수 있지만 일반적으로 문자열을 사용한다. 이때 프로퍼티 키는 문자열이므로 따옴표('...' 또는 "...")로 묶어야 한다. 하지만 식별자 네이밍 규칙을 준수하는 이름, 즉 자바스크립트에서 사용가능한 유효한 이름인 경우 따옴표를 생략할 수 있다. 즉 식별자 네이밍 규칙을 따르지 않는 이름에는 반드시 따옴표를 사용해야 한다.

식별자 네이밍 규칙을 따르지 않는 프로퍼티 키를 사용하면 번거로운 일이 발생한다. 따라서 가급적 식별자 네이밍 규칙을 준수하는 프로퍼티 키를 사용할 것을 권장한다. 

```javascript
var tomato = {
    firstName: 'Bang-to', // 식별자 네이밍 규칙을 준수하는 프로퍼티 키
    'last-name': 'Choi' // 식별자 네이밍 규칙을 준수하지 않는 프로퍼티 키
};
console.log(tomato); // {firstName: "Bang-to", last-name "Choi"}
```
프로퍼티 키로 사용한 firstName은 식별자 네이밍 규칙을 준수한다. 따라서 따옴표를 생략할 수 있다. 하지만 last-name은 식별자 네이밍 규칙을 준수하지 않는다. 따라서 따옴표를 생략할 수 없다. 자바스크립트 엔진은 따옴표를 생략한 last-name을 연산자 -가 있는 표현식으로 해석한다.

```javascript
var tomato = {
    fisrtName: 'Bang-to',
    last-name: 'Choi' // SyntaxError: Unexpected token -
}
console.log(tomato);
```

문자열 또는 문자열로 평가할 수 있는 표현식을 사용해 프로퍼티 키를 동적으로 생성할 수도 있다. 이 경우에는 프로퍼티 키를 사용할 표현식을 대괄호([...])로 묶어야 한다.

```javascript
var obj = {};
var key = 'hello';

obj[key] = 'world';
// var obj = {[key] : 'world'};

console.log(obj); // {hello: "world"}
```
빈 문자열을 프로퍼티 키로 사용해도 에러가 발생하지는 않는다. 하지만 키로서의 으미를 갖지 못하므로 권장하지 않는다.

```javascript
var tomato = {
    '': '' // 빈 문자열도 프로퍼티 키로 사용할 수 있다.
};

console.log(tomato); // {"": ""}
```

프로퍼티 키에 문자열이나 심벌 값 외의 값을 사용하면 암묵적 타입 변환을 통해 문자열이 된다. 예를 들어, 프로퍼티 키로 숫자 리터럴을 사용하면 따옴표는 붙지 않지만 내부적으로는 문자열로 변환된다.

```javascript
var tomato = {
    0: 1,
    1: 2,
    2: 3
};

console.log(tomato); // {0: 1, 1: 2, 2: 3}
```

var, function과 같은 예약어를 프로퍼티 키로 사용해도 에러가 발생하지 않는다. 하지만 예상치 못한 에러가 발생할 여지가 있으므로 권장하지 않는다.

```javascript
var tomato = {
    var:'',
    function:''
};

console.log(tomato); // {var:"", function:""}
```

이미 존재하는 프로퍼티 키를 중복 선언하면 나중에 선언한 프로퍼티가 먼저 선언한 프로퍼티를 덮어쓴다. 하지만 에러는 발생하지 않기 때문에 유의해야한다.

```javascript
var tomato = {
    name : "Choi",
    name : "Choe"
};

console.log(toamto); // {name : "Choe"}
```

## 프로퍼티 값 갱신

이미 존재하는 프로퍼테 값을 할당하면 프로퍼티 값이 갱신된다.

```javascript
var tomato =  {
    name : "tomato"
};

tomato.name = 'pomodoro'; // tomato 객첸에 name 프로퍼티가 존재하므로 name 프로퍼티의 값이 갱신된다.

console.log(tomato); // {name: 'pomodoro'}
```

## 프로퍼티 동적 생성

존재하지 않는 프로퍼티에 값을 할당하면 프로퍼티가 동적으로 생성되어 추가되고 프로퍼티 값이 할당된다

```javascript
var tomato = {
    name: 'tomato'
};

tomato.age = 20; // tomato 객체에는 age 프로퍼티가 존재하지 않는다. 따라서 tomato 객체에 age 프로퍼티가 동적으로 생성되고 값이 할당된다.

console.log(tomato); // {name: "tomato", age: 20}
```

## 프로퍼티 삭제

delete 연산자는 객체의 프로퍼티를 삭제한다. 이때 delete 연산자의 피연산자는 프로퍼티 값에 접근할 수 있는 표현식이어야한다. 만약 존재하지 않는 프로퍼티를 삭제하면 아무런 에러 없이 무시된다.

```javascript
var tomato = {
    name: 'tomato',
    age:20;
};

delete tomato.age; // tomato 객체에 age 프로퍼티가 존재한다. 따라서 delete 연산자로 age 프로퍼티를 삭제할 수 있다.
delete tomato.address; // tomato 객체에 address 프로퍼티가 존재하지 않는다. 따라서 아무일도 일어나지 않고, 에러도 발생하지 않는다.

console.log(tomato); // {name : "tomato"}
```

## ES6에서 추가된 객체 리터럴의 확장기능

ES6에서는 더욱 간편하고 표현력 있는 객체 리터럴의 확장 기능을 제공한다.

### 프로퍼티 축약 표현

객체 리터럴의 프로퍼티는 프로퍼티 키와 프로퍼티 값으로 구성된다. 프로퍼티 값은 변수에 할당된 값, 즉 식별자 표현식일 수도 있다.

```javascript
// ES5
var tomato = 1, pomodoro = 2;

var obj = {
    tomato: tomato,
    pomodoro: pomodoro
};

console.log(obj); // {tomato: 1, pmodoro: 2}
```

ES6에서는 프로퍼티 값으로 변수를 사용하는 경우 변수 이름과 프로퍼티 키가 동일한 이름일 때 프로퍼티 키를 생략(property shorthand)할 수 있다. 이때 프로퍼티 키는 변수 이름으로 자동 생성된다.

```javascript
// ES6
var tomato = 1, pomodoro = 2;

var obj = { tomato, pomodoro };

console.log(obj); // {tomato: 1, pmodoro: 2}
```

### 계산된 프로퍼티 이름

문자열 또는 문자열로 타입 변환할 수 있는 값으로 평가되는 표현식을 사용해 프로퍼티 키를 동적으로 생성할 수도 있다. 단, 프로퍼티 키로 사용할 표현식을 대괄호([...])로 묶어야 한다. 이를 computed properrty name계산된 프로퍼티 이름이라 한다.

ES5에서 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생성하려면 객체 리터럴 외부에서 대괄호([...]) 표기법을 사용해야 한다.

```javascript
// ES5
var tomato = 'prop';
var i = 0;

var obj = {};

// 계산된 프로퍼티 이름으로 프로퍼티 키 동적 생성
obj[prefix + '-' + ++i] = i;
obj[prefix + '-' + ++i] = i;
obj[prefix + '-' + ++i] = i;

console.log(obj); // {prop-1: 1, prop-2: 2, prop-3: 3}
```

ES6에서는 객체 리터럴 내부에서도 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생성할 수 있다.

```javascript
// ES5
var tomato = 'prop';
let i = 0;

const obj = {
    [`${prefix}-${++i}`]: i,
    [`${prefix}-${++i}`]: i,
    [`${prefix}-${++i}`]: i
};

console.log(obj); // {prop-1: 1, prop-2: 2, prop-3: 3}
```

### 메소드 축약 표현

ES5에서 메소드를 정의하려면 프로퍼티 값으로 함수를 할당한다.

```javascript
// ES5
var obj = {
    name : 'tomato',
    sayHi: function() {
        console.log('Hi! ' + this.name);
    }
};

obj.sayHi(); // Hi! tomato
```

ES6에서는 메소드를 정의할 때 function 키워드를 생략한 축약 표현을 사용할 수 있다.

```javascript
// ES6
const obj = {
    name: 'tomato',
    sayHi() {
        console.log('Hi! ' + this.name);
    } // 메소드 축약 표현
};

obj.sayHi(); // Hi! tomato
```