# 01-React Component

### 데이터

B/E에서 JSON 형태의 데이터를 돌려주는 API를 제공한다고 가정(대부분은 REST API 또는 GraphQL).

**REST API**

* GET, POST, PUT/PATCH, DELETE (CRUD)
* Resource 중심

**GraphQL**

* Graph 자료 구조
* Query에서 얻고자 하는 걸 지정
* Query(Read), Mutation(Command: Create, Update, Delete), Subscription(Event)

### JSON (JavaScript Object Notation)

* [`parse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/JSON/parse): JSON 문자열을 매개변수로서 수용하고, 일치하는 자바스크립트 객체로서 변환합니다.

```
const json = '{"result":true, "count":42}';
const obj = JSON.parse(json);

console.log(obj.count);
// Expected output: 42

console.log(obj.result);
// Expected output: true

// run
> 42
> true
```

* [`stringify()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/JSON/stringify): 객체를 매개변수로서 수용하고, JSON 문자열 형태로 변환합니다.

```
console.log(JSON.stringify({ x: 5, y: 6 }));
// Expected output: "{"x":5,"y":6}"

console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)]));
// Expected output: "[3,"false",false]"

console.log(JSON.stringify({ x: [10, undefined, function(){}, Symbol('')] }));
// Expected output: "{"x":[10,null,null,null]}"

console.log(JSON.stringify(new Date(2006, 0, 2, 15, 4, 5)));
// Expected output: ""2006-01-02T15:04:05.000Z""

// run

> '{"x":5,"y":6}'
> '[3,"false",false]'
> '{"x":[10,null,null,null]}'
> '"2006-01-02T06:04:05.000Z"'
```

F/E는 이 데이터를 사용자가 볼 수 있도록 UI를 구성한다. React는 \
선언형(HTML 과 유사한 모양의  DSL을 사용) 으로 UI 를 구성할 수 있다.

선언형으로 UI 를 한 번 선언해두면 안에 있는 것들이 변경될 때 자동으로 업데이트 된다



### 컴포넌트 계층 구조



간단한 컴포넌트를 모아서 복잡한 UI 를 만들 수 있다.

예를 들어 자동차를 예시로 든다면 컴포넌트란 엔진, 타이어 등을 말하고 UI는 자동차로 말할 수 있다. 컴포넌트를 모아 하나의 결합체를 만들 수 있는 것이며 이것이 리액트의 장점이다.



### 객체 지향 프로그래밍

[객체 지향 프로그래밍](https://ko.wikipedia.org/wiki/%EA%B0%9D%EC%B2%B4\_%EC%A7%80%ED%96%A5\_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)에서 단일 책임 원칙(single responsibility principle)이란 모든 클래스는 하나의 책임만 가지며, 클래스는 그 책임을 완전히 [캡슐화](https://ko.wikipedia.org/wiki/%EC%BA%A1%EC%8A%90%ED%99%94)해야 함을 일컫는다. 클래스가 제공하는 모든 기능은 이 책임과 주의 깊게 부합해야 한다.

컴포넌트가 너무 커지고 있다면 세분화를 시켜줄 수 있다.

* CSS 의 경우 class 화를 통해 기준을 재활용할 수 있다.
* Design's Layer 디자인을 할 때에도 트리 형태로 작성하는 경우가 대부분이다
* Information Architecture (JSON Schema의 영향) → 실제로 엄청 많이 쓰게 됨. 자연스러운 SRP를 위해서 사실상 강제됨.
