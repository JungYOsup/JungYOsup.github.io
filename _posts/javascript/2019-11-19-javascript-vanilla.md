---
title: "Javascript 핵심 요약"
excerpt: "javascript 핵심이 잘 나와있다."
categories:
  - javascript
tags:
  - jekyll
last_modified_at: 2018-07-01T13:00:00+09:00
toc: true
toc_sticky: true
---

# 자바스크립트 핵심 이론 100가지

## 1. 자바스크립트는 변수를 선언할때 데이터 타입을 미리 지정하지 않는다. 다시말해, 변수는 할당된 값의 타입에 의해 **동적**으로 변수의 타입이 결정된다.

## 2. 동일한 작업을 반복적으로 수행해야 한다면, 미리 정의된 함수를 **재사용** 하는것이 효율적이다.

## 3. **자바스크립트 객체는 키와 값으로 구성된 프로퍼티(key : value)의 집합**이다. **프로퍼티 값이 함수일 경우 일반함수와 구별하기 위해 메소드라고 부른다.**

## 4. 자바스크립트는 number라는 하나의 숫자 타입만 존재한다.

## 5. **자바스크립트의 숫자타입은 모든 수를 실수를 처리한다**. 정수로 표시된다해도 사실은 실수이다. 따라서 정수로 표시되는 수끼리 나누더라도 실수가 나올수 있다.

## 6. undefined 타입의 값은, 선언 이후 값을 할당하지 않은 변수가 가지는 값이다. 그러나 **개발자가 의도적으로 undefined를 할당해야하는 경우는 권장하지 않는다.** **그럼 변수의 값이 없다는 것을 명시하고 싶은 경우 어떻게 하는게 좋을까? 그런 경우 undefined를 할당하는 것이 아니라 null을 할당한다.**

## 7. type of 연산자로 null 값을 연산해보면 null이 아닌 obeject가 나오는데 이는 자바스크립트의 설계상의 오류이다.

## 8. 따라서 null 타입을 확인할 때는 type of 연산자를 사용하면 안되고 **일치 연산자(===) 를 사용** 해야한다.

## 9. 변수의 존재 목적을 쉽게 이해할 수 있도록 의미 있는 변수명을 지정해야한다.

## 10. var 키워드로 선언한 변수는 중복 선언이 가능하다, 다시 말해 변수명이 같은 변수를 중복으로 선언해도 에러가 발생하지 않는다

    하지만 변수를 중복 선언하면 에러없이 이전 변수의 값을 덮어쓰므로, 만약 동일한 변수명이 선언되있는것을 모르고 중복 선언했다면 의도치 않게 변수의 값을 변경하는 부작용을 발생시킨다. **따라서 변수의 중복 선언은 문법적으로 허용되지만 사용하지 않는것이좋다.**

## 11. 변수 선언시 var 키워드를 생략할 경우, 이때 변수는 전역 변수가 된다. **그러나 var 키워드의 생략은 문법적으로 혀옹 되지만 의도하지 않게 변수를 전역화 할수 있으므로 사용하지 않는것이 좋다.**

## 12. 호이스팅이란 var 선언문이나 function 선언문 등 모든 선언문이 해당 Scope의 선두로 옮겨진 것처럼 동작하는 특성을 말한다, 즉 자바스크립트는 모든 선언문(var, let, const, function, function\*,class)이 선언되기 이전에 참조 가능하다.

```javascript
console.log(foo); //c나 다른 언어의 경우 변수를 선언하지 않았으므로 오류가 발생해야 정상이지만 javascript에서는 undefined
//javascript의 특징인 모든 선언문은 호이스팅이 되기 때문에 오류가 아닌 undefined이 정의되는것이다.
var foo = 123;
console.log(foo); // 123
{
  var foo = 456;
}
console.log(foo); //456
```

## 13. 자바스크립트 변수는 **함수 레벨 스코프**를 갖는다. 함수 레벨 스코프란, 함수 내부에서 선언한 변수는 지역변수이며 함수 외부에서 선언한 변수는 모두 전역변수이다.

## 14. 그러나 ECMAScript 6에서 도입된 let, const 키워드를 사용하면 **블록레벨 스코프**를 사용할수 있다. 블록레벨스코프란, 코드블록({})내에서 선언된 변수는 코드블록 내에서만 유효하며 코드 불록 외부에서는 참조할수 없다.

## 15. var 키워드로 선언된 변수의 문제점

> 1.함수레벨 스코프
>
> > 전역변수의 남발
>
> > for loop 초기화식에서 사용한 변수를 for loop 외부 또는 전역에서 참조
>
> 2.var 키워드 생략허용
>
> > 의도치 않은 변수의 전역화
>
> 3.중복 선언 허용
>
> > 의도치 은 변수값 변경
>
> 4.변수 호이스팅
>
> > 변수를 선언하기 이전에 참조가 가능하다.

대부분의 문제는 전역 변수로 인해 발생한다. **전역변수는 간단한 애플리케이션의 경우, 사용이 편리한 면이 있지만 불기피한 상황을 제외하고는 사용을 억제한다.** 또한 전역변수는 유효범위(scope)가 넓어서 의도치 않은 변수의 변경이 발생할수 있고, 여러 함수와 상호 의존하는 등 부수 효과가 발생할수 있어서 복잡성이 증가한다.

변수의 유효범위는 좁을수록 좋다

그래서 등장한것이 ES6의 let과 const 키워드이다.

## 16. 이미 존재하는 프로퍼티 키를 중복 선언하면 나중에 선언한 프로퍼티가 먼저 선언한 프로퍼티를 덮어쓴다.

## 17. ECMAScript 6에서 새롭게 클래스가 도입, 프로토타입 기반 프로그래밍(클래스가 없는 객체지향 프로그래밍)인 기존의 javascript에서

    클래스 기반 언어에 익숙한 프로그래머가 보다 빠르게 학습할 수 있는 단훈하고 깨긋한 새로운 문법을 제시, 클래스 없이 프로토타입 체인과 클러저 등으로 객체지향 언어의 상속, 캡슐화(은닉화)등의 개념을 클래스를 사용함으로써 쉽게 해결함

## 18. 가장 기본적인 객체 생성방식은 {} 를 사용({}내에 아무것도 없으면 즉 프로퍼티가 없으면 빈객체 )

## 19. new 연산자와 Obejct 생성자 함수를 호출하여 빈 객체를 생성할 수 있다.**그러나 일부러 Object 생성자 함수를 사용해 객체를 생성해야 할 일은 거의 없다. 즉 거의 {}로 객체생성을 한다.**

## 20. 생성자 함수를 이용하면 동일한 프로퍼티를 갖는 객체를 만드는데 아주 유용하다.

동일한 프로퍼티를 갖는 객체를 이렇게 선언하는것보다

```javascript

var person1 = {
  name = 'Lee',
  gender = 'male',
  sayHello : function(){
    console.log('Hi My Name is' + this.name); // this는 person 1을 가리킴
  }
}

var person2 = {
  name = 'Jung',
  gender = 'female',
  sayHello : function(){
    console.log('Hi My Name is' + this.name); //this는 person2를 가리킴
  }
}
```

생섬자 함수를 이용하여 여러개를 간편하게 생성할수 있다.

```javascript
function Person(name, gender) {
  var married = true; // private
  this.name = name; //public
  this.gender = gender; //public
  this.sayHello = function() {
    //public
    console.log("Hi My Name is" + this.name); //this는 person2를 가리킴
  };
}

var person1 = new Person("Lee", "male");
var person2 = new Person("Jung", "female");
```

> 1.**생성자 함수는 일반적으로 대문자**로 시작
>
> 2.프로퍼티 또는 메소드명 앞에 기술한 **this는 생성자 함수가 생성할 인스턴스**를 가르킨다.
>
> 3.this에 연결(바인딩)되어 있는 **프로퍼티와 메소드는 public(외부에서 참조 가능)하다.**
>
> 4.생성자 함수 내에서 선언된 **일반 변수는 private(외부에서 참조 불가능)하다.** 즉 생성자 함수 내부에서는 자유롭게 접근이 가능하나 외부에서 접근할 수 없다.

## 21. 자바스크립트의 생성자 함수는 형식 정해져 있는것이 아니기 때문에 기존함수와 동일한 방법으로 생성자 함수를 선언하고 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작한다.

이는 생성자 함수가 아닌 일반 함수에 new 연산자를 붙여 호출하면 생성자 함수처럼 동작할 수 있다는 것을 의미한다. 따라서 일반적으로 **생성자 함수명은 첫문자를 대문자로 기술**하여 혼란을 방지하려는 노력을 한다.

new 연선자와 함께 함수를 호출하면 this 바인딩은 다르게 동작한다.

예를들어 java의 경우 생성자 함수는 클래스 명과 이름이 같아야하는게 형식인데, javascript는 클래스가 없으므로 일반 함수가 new를 붙임으로써 생성자 함수가 될수 있기에, **일반함수를 쓸것과 생성자 함수로 쓸것을 이름으로써 명확하게 구분지어야 한다.**

## 22. 프로퍼티의 key는 *예약어*와 같은 이름으로 사용하면 안된다.

## 23. 프로퍼티 키는 자바스크립에서 사용 가능한 유효한 이름이 아닌경우, 반드시 따음표를 사용하여야 한다.

    ex) first_name : 'Yosup' , 'first-name' : 'Yosup' (- 는 사용하가능한 유요한 이름이 아니므로 ''를 사용함)

## 24. 프로퍼티 값 읽기

객체의 프로퍼티 값에 접근하는 방법은 마침표(.) 표기법과 대괄호([]) 표기법이 있다.

```javascript
var person = {
  "first-name": "ung-mo",
  "last-name": "lee",
  gender: "male",
  1: 10
};

console.log(person.first - name); // Nan : undefined-undefuned
console.log(person[first - name]); //ReferenceError : first is not defined (first하나만 인식해버림)
console.log(person["fist-name"]); // 'ung-mo'

console.log(person.gender); //'male'
console.log(person[gender]); // ReferenceError : gender is not defined
console.log(person["gender"]); // 'male'

console.log(person['1']) // 10
console.log(person[1]) //10
console.log(person.1) // SyntaxError
```

## 25. 프로퍼티 동적생성

```javascript
var person = {
  "first-name": "yosup",
  "last-name": "jung",
  gender: "male"
};

person.age = 20;
console.log(person.age); //20
```

## 25.for-in 문

for-in문을 사용하면 객체(배열포함)에 포함된 모든 프로퍼티에 대해 루프를 수행할 수 있다.

```javascript
var person = {
  'first-name' : 'Yosup',
  'last-name' : 'Jung',
  gender : 'male'
}

for(var prop in person){
  console.log(prop+ ':' person[prop]); //person.prop (x)


}
// 결과값
// 'first-name' : 'Yosup',
//  'last-name' : 'Jung'
// gender : male

// person.prop을 쓸경우

// 'first-name' : undefined
//  'last-name' : undefined
// gender : undefined


```

```javascript
var array = ['one','two'];

for(var index in array){
  console.log(index+ ':' array[index]); // array.index (x)
}

// 0 : one
// 1 : two

```

```javascript
var array = ["one", "two"];
array.name = "my array";

for (var index in array) {
  console.log(index + ":" + array[index]);
}

// 0 : one
// 1: two
// name : my array
```

> 1.for-in 문은 객체의 문자열 키를 순회하기 위한 문법이므로 배열에는 사용하지 않는것이 좋다.
> 왜냐하면 객체의 경우 프로퍼티의 순서가 보장될 필요가 없지만, 배열은 순서를 보장해야하기 때문이다.
>
> 2.배열 요소만을 순회하지 안다.
>
> 3.for-in 문은 마침표(.) 표기법을 사용할시 값이 undefined가 나오므로 대괄호 표기법을 사용해야한다.

## 26. 이와 같은 for-in문의 단점을 극복하기 위해 ES6에서 for-of문이 추가되었다.

```javascript
const array = ["one", "two"];
array.name = "my array";

for (const value of array) {
  console.log(value);
}

// one
// two
```

> **즉 for-in문은 객체의 프로퍼티를 순회하기 위해 사용하고 for-of 문은 배열의 요소를 순회하기 위해 사용한다**.

## 27. 함수표현식 방식으로 정의한 함수는 함수명을 생략할 수 있고 이러한 함수를 익명 함수라고 한다 **함수 표현식에서는 함수명을 략하는 것이 일반적이다.**

```javascript
var bar = function(a, b) {
  return a * b;
};
```

## 28. 함수 호이스팅은 함수 선언의 위치와는 상관없이 코드 내 어드 곳에서든지 호출이 가능한것을 말한다.

(1) 함수 선언문

```javascript
var res = square(5); //java에서는 이렇게 호출 못함, but javascript에서는 호이스팅이 되므로 오류가 발생안하고 동작함

function square(number) {
  //함수선언문
  return number * number;
}
```

(2) 함수표현식

```javascript
var res = square(5); // TypeError : square is nor a function

var square = function(number) {
  //함수 표현식
  return number * number;
};
```

함수 선언문의 경우와 달리 TypeError가 발생하였다. 함수표현식의 경우 함수 호이스팅이 아니라 변수 호이스팅이 발생한다.

따라서 **함수 표현식만을 사용할 것을 권고하고 있다.** 함수 호이스팅이 함수 호출전 반드시 함수를 선언하여야 한다는 규칙을 무시하므로 코드의 구조를 엉성하게 만들수 있기 때문이다.
또한 함수 선언문으로 함수를 정의하면 사용하기에는 쉽지만 대규모 애플리케이션을 개발하는경우 **응답속도가 현저히 떨어질 수 있으므로 주의**해야 할 필요가 있다.

## 29. 함수는 배열등을 이용하여 한번에 여러개의 값을 리턴할 수도 있다, 함수는 반환을 생략할수 있다. 이때 함수는 암묵적으로 undefined를 반환한다.

```javascript
var getSize = function(width, heigh, depth) {
  var area = width * height;
  var volume = width * height * depth;
  return [area, volume]; //배열의 형태로 복수값의 반환
};

console.log(getSize(3, 2, 3)[0]); //6
console.log(getSize(3, 2, 3)[1]); // 18
```

## 30. 콜백함수는 함수를 명시적으로 호출하는 방식이 아니라 **특정 이벤트가 발생했을 때 시스템에 의해 호출되는 함수**를 말한다.

## 31. 자바스크립트는 함수레벨 스코프를 따른다. 함수레벨 스코프란 함수 코드불록내에서 선언된 변수는 함수 코드불록내에서만 유효하고 함수 외부에서는 유효하지(참조할수 없다) 않다. 단 ECMAScript6에서 도입된 let 키워드를 사용하면 블록 레벨 스콜프를 사용할수 있다.

## 32. **전역변수 사용은 변수이름이 중복될수 있고, 의도치 않은 재할당에 의한 상태 변화로 코드를 예층하기 어렵게 만드므로 사용을 억제해야한다**.

## 33. var 키워드를 생략한 변수는 암묵적으로 전역변수가 되므로, **키워드 생략없이 반드시 var 키워드를 사용**해야한다.

## 34. 앞에서 말한것처럼 **전역변수를 사용하여야 할 이유를 찾지 못한다면 지역변수를 사용하여야한다**. **변수의 범위인 스코프는 좁을수록 좋다.**

## 35. 전역변수 사용을 최소화 하는 방법이 좋다고 햇는데, 그러기 위해서는 다음과 같은 방법을 사용하는것이 좋다.

```javascript

var MyAPP ={}; // 전역변수 객체를 하나 만들어서 더이상 전역변수 객체를 늘리지 않고 계속 사용하는거임

MyAPP.student = {
  name : "Lee";
  gender : "Male";
};

console.log(MyApp.student.name);

```

## 36. 즉시 실행함수에만 Strict Mode를 사용하자. (즉시 실행함수와 Strict Mode는 나중에 배워보겠다.)

## 37. 함수 호출방식에 의해 결정되는 this

자바스크립트 함수는 호출될 떄, 매개변수로 전될다는 인자값 이외에, argument 객체와 this 를 암묵적으로 전달받는다.
그리고 자바스크립트에서 this는 함수 호출방식에 따라 this에 바인딩되는 객체가 달라진다.

자바스크립트경우 함수 호출에 의해 this에 바인딩 할 어떤 객체가 동적으로 결정된다.

함수 호출하는 방식은 아래와 같다.

1. 함수 호출
2. 메소드 호출 (객체의 value가 함수 = 메소드)
3. 생성자 함수 호출
4. apply/call/bind 호출 (이거는 나중에 더 배워보자)

결론 : 메소드 안의 this는 참조하는 객체를 바인딩하고 , 생성자 함수 호출 즉 new연산자와 함께 함수를 호출하면 this는 생성자 함수가 암묵적으로 생성한 빈 객체를 바인딩한다. 그외 나머지는 전역객체(window)를 가르킨다.
하지만 위에서 동적으로 결정되는 방법외에도 명시적으로 바인딩하는 방법이 있는데 그 방법이 4번인 apply/call/bind이다.
이 방법은 나중에 배워보도록 하자
