# 02-TypeScript



## REPL

ts-node 를 실행하여 테스트한다

```
npx ts-node
```

```
ex)
let name: string;
let age: number:

name = 'jinwood';
age: = 12;
```

<figure><img src=".gitbook/assets/스크린샷 2023-04-13 오후 8.53.40.png" alt=""><figcaption></figcaption></figure>

타입 내용을 잡을 수 있고 형식이 틀릴 경우 오류 메시지로 표기하여 실제 코드에서 발생할 오류를 사전에 방지할 수 있다.



## Type vs Interface

### Type 형의 선언 및 적용 방식

<figure><img src=".gitbook/assets/스크린샷 2023-04-13 오후 8.57.44.png" alt=""><figcaption></figcaption></figure>

### interface 형의 선언 및 적용 방식

<figure><img src=".gitbook/assets/스크린샷 2023-04-13 오후 9.01.25.png" alt=""><figcaption></figcaption></figure>

나는 현재 interface 형을 주로 사용하고 있었어서 interface 형이 더 익숙하였다\
typescriptlang 의 문서를 보면 핵심적인 차이는 <mark style="color:red;">**타입은 새 프로퍼티를 추가하도록 개방될 수 없는 반면, 인터페이스의 경우 항상 확장될 수 있다는 점**</mark>이라고 하지만 아직은 사실 큰 차이점을 잘 모르겠다.

<figure><img src=".gitbook/assets/스크린샷 2023-04-13 오후 9.06.41.png" alt=""><figcaption></figcaption></figure>

### Type 을 깐깐하게 잡고 싶을 때

'Tuple' 이라는 타입을 사용할 수 있다.

```
let anythings: any[];

anythings = ['hp', 256];

let pair: [string, number];

pair = ['hp', 256];
```

### Union Type

여러 타입 중 하나. 예를 들어 boolean은 true | false라고 볼 수 있다.

ex) typeof 's' 의 경우 string 이 표기된다



평소 코딩할 때 쓰던 Optional Parameter 에 대한 효용도와 사용법에 대한 이해도를 올릴 수 있었다

```
type Human = {
  name: string;
  age?: number;
};

// 이전에 선언해 둔 Human 을 이용하여 코드를 간략하게 표현할 수 있다.
function greeting({ name, age }: Human): string {
  return age ? `${name} (${age})` : name;
}

greeting()

greeting({ name: '홍길동' })

greeting({ name: '홍길동', age: 13 })
```

### Intersection Type

각 타입의 교집합을 설정할 수 있다.\
간단히 말하자면 설정한 모든 값이 있어야 선언될 수 있는 타입으로 이해할 수 있다.

```
type Human = {
  name: string;
  age: number;
};

type Creature = {
  hp: number;
  mp: number;
};

type Person = Human & Creature;

let person: Person;

// Human 과 Creature 의 모든 상태값을 선언해야 한다

person = { name: '홍길동', age: 13, hp: 256, mp: 16 };
```

아래처럼 name 만 선언했을 경우 그 이후 선언 될 age 에서 break 가 걸린다

<figure><img src=".gitbook/assets/스크린샷 2023-04-13 오후 9.43.26.png" alt=""><figcaption></figcaption></figure>

선언 순서로는 name, age, hp, mp 이기 때문에 age 값이 없는 경우 뒤에 hp 가 선언되어 있더라도 age 에서 오류\
선언이 먼저 나고 mp 가 없다는 내용은 나오지 않는다. 추후 개발할 때 조심하도록 하자

<figure><img src=".gitbook/assets/스크린샷 2023-04-13 오후 9.45.44.png" alt=""><figcaption></figcaption></figure>

## Generics

### 파라미터 형태로 넘겨주는 것

```
function identity<Type>(arg: Type): Type {
  return arg;
} 
```

### 타입스크립트 사용하는 이유 및 후기

아샬님은 VS Code 내에서  자동검사 및 실시간 검사가 있어 \
사용하기 편하다는 간단한 이유를 말씀하셨다.\
나도 사실 제대로 오류 없이 돌아만 가면 되는데 왜 쓰는지에 대해서 아직 잘 이해가 안되는데\
vs code 기능인줄 알았던 것들도 타입스크립트 기능이라는 것이 조금 다시 생각하게 되었다.
