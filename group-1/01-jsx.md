# 01-JSX

### JSX 란?

JavaScript 를 확장한 문법이다

리액트에서 나온 부산물이지만 반드시 리액트에서만 사용되는 것은 아니며 반드시 \
사용 될 이유는 없다.

하지만 문법적 설탕이란 말처럼 코드를 달콤하고 편하게 사용할 수 있기에 사용하면\
코드를 직관적으로 볼 수 있어 용이하다



XML 이 아니기 때문에 코드를 닫아주는 필요성이 있다

```
// ex)
<p>Hello World<br></p>  >>>>>> X
<p>Hello World<br/></p> or <p>Hello World<br></br></p> >>>>> O
```



### Babel

JSX ==> JavaScript 변환기이다

→ “Presets”에서 “react”를 체크하거나, “Plugins”에서 “@babel/plugin-transform-react-jsx”를 추가하면 JSX를 실험할 수 있다

[Babel Link](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie\_mob%2011\&build=\&builtIns=false\&corejs=3.21\&spec=false\&loose=false\&code\_lz=Q\&debug=false\&forceAllTransforms=false\&modules=false\&shippedProposals=false\&circleciRepo=\&evaluate=false\&fileSize=false\&timeTravel=false\&sourceType=module\&lineWrap=true\&presets=env%2Creact%2Cstage-2\&prettier=false\&targets=\&version=7.21.4\&externalPlugins=\&assumptions=%7B%7D)



### React Runtime Options



Babel 에서 좌측 하단에 보면 react runtime 이라는 옵션이 있다

해당 옵션을 설정함에 따라 반환되는 코드가 달라진다

```
// ex)
<div class="test" >
  <p>Hello, world!</p>
  <Button type="submit">Send</Button>
</div>

```

#### classic version

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

#### automatic version

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

### React.createElement

createElement를 호출하여 지정된 type, props 및 children 으로 React 요소를 만든다.

```
class Hello extends React.Component {
  render() {
    return React.createElement('div', null, `Hello ${this.props.toWhat}`);
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(React.createElement(Hello, {toWhat: 'World'}, null));
```

위의 예시코드처럼 'div' 가 type, null 이 props, \`Hello ${this.props.toWhat}\` 가 \
children 으로  요소를 생성한다.



### React Element

react App 의 가장 작은 단위이며 type , props 필드를 가지는 react 의 객체이다.

엘리먼트들로 이루어진 트리를 엘리먼트 트리라고 하며, 메모리상에만 존재한다.



### VDOM (Virtual DOM)

> Virtual DOM (VDOM)은 UI의 이상적인 또는 “가상”적인 표현을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 “실제” DOM과 동기화하는 프로그래밍 개념입니다. 이 과정을 [재조정](https://ko.legacy.reactjs.org/docs/reconciliation.html)이라고 합니다.

### 사용 이유

Redux 창시자인 Dan Abramov 의 말을 빌리자면 미신으로는 빨라서 쓴다고 하지만 \
유지보수가 가능한 앱을 만드는 것을 도와주기 때문이다.

DOM 을 사용할 경우 전체 렌더링을 실행해야 하기 때문에 서버에 과부하가 걸릴 수 있다.\
VDOM 을 사용할 경우 변화된 컴포넌트 내에서만 리렌더링을 실행하기 때문에 과부하를 줄일 수 있다.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p><a href="https://www.howdy-mj.me/dom/what-is-dom">출처</a></p></figcaption></figure>

### <mark style="color:red;">**이 접근방식이 React 의 선언적 API 를 가능하게 한다.**</mark>

쉽게 말하자면 production(DOM) 과 develop(VDOM) 트리를 두고 비교하여 테스트할 장소를 만들어 볼 수 있는 것이다. 이에 막말로 하자면 코드를 휘갈겨놔도 큰 오류없이 망가지지 않는다는 것이다.

### React.StrictMode

`StrictMode`는 애플리케이션 내의 잠재적인 문제를 알아내기 위한 도구입니다. `Fragment`와 같이 UI를 렌더링하지 않으며, 자손들에 대한 부가적인 검사와 경고를 활성화합니다.

아래 코드처럼 앱 내의 어느 곳에서든 StrictMode 를 사용할 수 있다.

```
import React from 'react';

function ExampleApplication() {
  return (
    <div>
      <Header />
      <React.StrictMode>
        <div>
          <ComponentOne />
          <ComponentTwo />
        </div>
      </React.StrictMode>
      <Footer />
    </div>
  );
}
```

### 후기

react 를 사용하는 이유가  VDOM 을 사용해서 라는 것은 알고 있었지만 속도가 빨라서라는\
이유가 크다고 생각했었는데 선언적 API 라는 것이라는 이유가 더 크다는 것이 신선했고\
왜 1위에 올랐는지 이해할 수 있게 되었다. 과제를 하면서 배운 내용을 다시 한 번 체크해봐야겠다.
