# React

[TOC]



## 1. Overview

### 1. Components as classes

1. currently to provide more features
2. need to extend `React.Component`

```
class Welcome extends React.Component {
  render () {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

3. render() must be defined in a React.Component subclass.
4. All the other methods described on this page are optional.
5. 컴포넌트 클래스를 직접 만들어서 사용하지 마세요. React 컴포넌트를 사용할 때에는 **상속보다 합성을 주로 사용합니다**.



### 2. ES6 class syntax

1. if you don't prefer to use the ES6 class syntax, you may use the `create-react-class` module or a similar custom abstraction instead.

2. Reference : https://reactjs.org/docs/react-without-es6.html





## 2. The Component LifeCycle

1. Each component has several "lifecycle methods" that you can override to run code at particular times in the process.
2. You can use this lifecycle diagram as a cheat sheet. http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/



### 1. Mounting

 아래 메서드들은 컴포넌트의 인스턴스가 생성되어 DOM 상에 삽입될 때에 순서대로 호출됩니다:

- **constructor()**
- static getDerivedStateFromProps()
- **render()**
- **componentDidMount()**

> 주의 : 기존에 사용되었지만 이제는 사용하면 안되는 메소드 UNSAFE_componentWillMount()



#### 1. constructor()

1. If you don't initialize state and you don't bind methods, you don't need to implements a constructor for your React component.

2. The constructor for a React component is called before it is mounted.

3. You should call `super(props)` before any other statement. Otherwise, `this.props` will be undefined in the constructor, which can lead to bugs.

4. Typically, in React constructor are only used for two purpose:

   > Initializing **local state** by assigning an object to this.state.

   > Binding **event handler** methods to an instance.
   
5. You **should not call setState()** in the constructor(). Instead, if your component needs to use local state, assign the initial state to **this.state** directly in the constructor:

```
constructor(props) {
  super(props);
  // Don't call this.setState() here!
  this.state = { counter: 0 };
  this.handleClick = this.handleClick.bind(this);
}
```

6. Constructor is the only place where you should assign this.state directly. In all other methods, you need to use this.setState() instead.



#### 2. Static getDerivedStateFromProps()

#### 3. Render()

#### 4. ComponentDidMount()



### 2. Updating

props 또는 state가 변경되면 갱신이 발생합니다. 아래 메서드들은 컴포넌트가 다시 렌더링될 때 순서대로 호출됩니다.

- static getDerivedStateFromProps()
- shoudComponentUpdate()
- **render()**
- getSnapshotBeforeUpdate()
- **componentDidUpdate()**

> 주의 : 아래 메서드는 더이상 사용하지 않습니다. 
>
> - UNSAFE_componentWillUpdate()
> - UNSAFE_componentWillReceiveProps()



### 3. Unmounting

아래 메서드는 컴포넌트가 DOM 상에서 제거될 때에 호출됩니다.

- **componentWillMount()**



### 4. 오류 처리

아래 메서드들은 자식 컴포넌트를 렌더링하거나, 자식 컴포넌트가 생명주기 메서드를 호출하거나, 또는 자식 컴포넌트가 생성자 메서드를 호출하는 과정에서 오류가 발생했을 때에 호출됩니다.

- static getDeriverdStateFromError()
- componentDidCatch()





## 3. Other APIs

- setState()
- forceUpdate()



## 4. Class Properties

- defaultProps
- displayName



## 5. Instance Properties

- props
- state

