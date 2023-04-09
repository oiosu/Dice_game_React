#### 1. 인덱스 파일에서 하는 일

* `index.html`

> ```react
> <!DOCTYPE html>
> <html lang="ko">
> <head>
>   <meta charset="UTF-8">
>   <title>가위바위보</title>
> </head>
> <body>
>   <div id="root"></div>
> </body>
> </html>
> ```
>
> 웹 브라우저에서 가장 먼저 실행되는 파일 



* `index.js` 

> ```react
> import ReactDOM from 'react-dom/client';
> 
> 
> const root = ReactDOM.createRoot(document.getElementById('root'));
> root.render(<h1>안녕 리액트!</h1>);
> 
> ReactDOM.render(
> <>
>     <h1 id='title'>가위바위보</h1>
> </>
> )
> ```
>
> `index.html` 파일이 열리고 나서 실행되는 파일 
>
> 리액트 코드들 중에서 가장 먼저 실행되는 파일이라고 생각하기
>
> * `render` : 리액트에서 render 메소드로 html 태그를 만들어준다.
>
>   > render 메소드를 호출할 때 전달하는 첫번째 argument 값이 `h1` 태그인 것을 알 수 있다. 
>   >
>   > argument 값이 문자열과 같은 형태가 아니라 html태그를 그대로 작성했다는 점이 특이하다. 사실 이부분은 순수한 자바스크립트 코드는 아니고 리액트에서 지원하는 `JSX` 라는 문법이다.
>   >
>   > (= 순수한 자바스크립트가 아닌 리액트로 개발할 때 사용하는 문법)
>
>   > * `document.getElementById('root')`
>   >
>   > DOM 요소들 중에서`root`라는 `id` 속성을 가진 요소를 가지고 온다.
>   >
>   > 그래서 결과적으로 `root` 라는 `id`를 가지고 있는 html 요소가 두번째 argument 값으로 사용된다.
>
> 실제로 `render` 메소드가 실행되면 리액트는 첫번째 argument 값을 바탕으로 새로운 html 요소를 만들고 그 요소를 두번째 argument 값에 집어 넣는 방식으로 동작한다.



#### 2. JSX

> 자바스크립트 파일 안에 HTML 태그를 사용하는 문법 
>
> 리액트에서 지원하는 JSX 문법
>
> 자바스크립트의 확장된 문법

* `주의사항` : 자바스크립트의 확장된 문법이기 때문에 HTML 문법을 완전히 그대로 사용할 수는 없다.  대표적으로 `class`와 `for` 이다. 

  > * `class`
  >
  >   ```react
  >   class Dice {
  >       roll(){
  >           console.log('Roll!');
  >       }
  >   }
  >   ```
  >
  >   HTML 에서 class는 CSS의 class를 적용하는 속성이지만 자바스크립트에서는 이런 식으로 객체지향의 개념으로 Dice 라는 클래스를 선언할때 class라는 키워드를 사용하기 때문에 JSX에서 class 속성을 작성하려면 `className` 이라는 속성을 작성해줘야한다.
  >
  >   ```react
  >   ReactDOM.render(
  >   	<p className="hello">안녕 리액트!</p>,
  >       document.getElementById('root')
  >   );
  >   ```
  >
  > * `for`
  >
  >   HTML에서 for라는 속성은 label 태그에서 input 태그와 함께 사용되는 속성입니다. JSX 문법으로 HTML의 for라는 속성을 사용하려면 앞에 htmlFor 라고 작성해줘야 한다.
  >
  >   ```react
  >   <form>
  >   	<label htmlFor="name">이름</label>
  >       <input id="name" type="text" />
  >   </form>
  >   ```
  >
  > * 그외 이벤트 핸들러의 이름도 조금씩 다르다.
  >
  >   모두 소문자로 작성했던 이벤트 핸들러들은 JSX문법으로 작성할 땐 두번째 단어무터 첫 글자를 대문자로 작성해 줘야 한다. 
  >
  >   `onBlur` `onFocus` `onMouseDown`



#### 3. Fragment

+ JSX 요소들은 반드시 하나의 태그로 감싸줘야한다.

  하지만 마약 `DIV` 라는 태그를 사용하고 싶지 않다면 리액트에서 제공하는 Fragement 을 사용하면 된다.

```react
import {Fragment} from 'react';

ReactDOM.render(
    <Fragment>
        <p>안녕</p>
        <p>리액트</p>
    </Fragment>,
    document.getElementById('root')
);
```

* Fragment를 잘 활용하면 불필요한 `div` 태그를 줄일 수 있다.
* 자주 사용될 경우 축약형 문법으로 이름없는 태그 `<>` 로도 사용된다. 그렇다면 import 하지 않아도 되고 코드도 훨씬 깔끔하게 작성할 수 있다.



#### 4. JSX에서 자바스크립트 사용하기

* JSX는 실제로 실행될 때 자바스크립트 코드로 변환되어 실행된다.

  그래서 당연히 HTML 코드 뿐만 아니라 자바스크립트 코드로 함께 작성이 가능하다.

* JSX에서 HTML 코드와 자바스크립트 코드를 함께 사용하는 방법

  > `{}` 중괄호로 감싸주면 된다.

```react
import ReactDOM from 'react-dom';

const product = '맥북';

ReactDOM.render(
    <h1>나만의 {product} 주문하기</h1>,
    document.getElement.ById('root')
);
```

* `{}` 중괄호 안에는 변수를 그대로 사용할 수 있을 뿐만 아니라 자바스크립트로 된 표현식은 뭐든지 사용이 가능하다.

```react
{product.toUpperCase()}
```

```react
const porduct = '맥북';
const model = 'Air';

<h1>나만의 {product + model} 주문하기 </h1>
```

```react
const product = '맥북';
const model = 'Air';
const item = product + model;

<h1>나만의 {item} 주문하기 </h1>
```

```react
const imageUrl = '이미지 주소';

<img src={imageUrl} alt="제품 사진" />
```

```react
function handleClick() {
    alert('곧 도착합니다!');
}

<button onClick={handleClick}>확인</button>
```



* `주의사항` : 중괄호 안에는 자바스크립트의 표현식만 사용할 수 있기 때문에 

`if` 문이나 `for` 문 혹은 함수 선언과 같은 자바스크립트의 문장은 사용할 수 없다.



#### 5. Component

`React element` 를 ReactDOM에 render 메소드로 전달하게 되면 리액트가 이 객체를 해석해서 HTML로 렌더링 하게 된다. 

```react
import ReactDOM from 'react-dom';

const element = <h1>안녕 리액트!</h1>;

console.log(element);
ReactDOM.render(element, document.getElementById('root'));
```

결과적으로 `React element` 는 리액트로 화면을 구성하는데 있어서 가장 기본적이면서도 핵심적인 요소이다.

또한 `React element` 를 함수 형태로 만들어 내면 JSX문법을 작성할 떄 커스텀 태그처럼 활용할 수 도 있다.

```react
import ReactDOM from 'react-dom';

function Hello(){
    return <h1>안녕 리액트</h1>;
}

const element = (
<>
 <Hello />
 <Hello />
 <Hello />
</>
);

ReactDOM.render(element, document.getElementById('root'));
```

이때 Hello라는 함수를 리액트 **컴포넌트(React Component)**라고 부른다.

(참고로 리액트 컴포넌트는 단순히 함수를 만든다고 해서 모두 리액트 컴포넌트가 되는 것이 아니다. )

> 1. 함수 이름의 첫 글자를 꼭 대문자로 작성해야 한다. 
> 2. 반드시 JSX 문법으로 만든 리액트 엘리먼트를 리턴해줘야한다. 



* `App.js` 

  ```react
  function App() {
      return <div>App component</div>;
  }
  
  export default App;
  ```

* `index.js`

  ```react
  import ReactDOM from 'react-dom/client';
  import App from './App';
  
  ReactDOM.render(<App />, document.getElementById('root'));
  ```



---

* `Dice.js`

  ```react
  import diceBlue01 from './assets/dice-blue-1.svg';
  
  function Dice() {
      return <img src={diceBlue01} alt='주사위' />;
  }
  
  export default Dice;
  ```

* `App.js`

  ```react
  import Dice from './Dice';
  
  function App() {
      return (
          <div>
              <Dice />
          </div>
      );
  }
  
  export default App;
  ```

----



#### 6. Props

* `properties` 의 줄임말
* Component에 전달된 속성을 모두 가리키기 때문에 각각의 속성은 prop라고 부른다. 

* Component 태그에 지정해준 속성은 하나의 객체 형태로 컴포넌트 함수의 첫번째 파라미터로 전달된다. 

`App.js` : `<Dice color="blue" />` 

`Dice.js` : `function Dice(props) {return <img />}` 



* prop 값으로 Dice 컴포넌트의 이미지를 바꿔본다면?

```react
//Dice.js

import diceBlue01 from './assets/dice-blue-1.svg';
import diceRed01 from './assets/dice-red-1.svg';

function Dice(props) {
    const diceImg = props.color === 'red' ? diceRed01 : diceBlue01;
    return <img src={diceImg} alt="주사위" />;
}
export default Dice;
```

```react
//App.js

import Dice from './Dice';

function App() {
    return (
        <div>
        	<Dice color="red" />
        </div>
    );
}

export default App;
```



* 주사위 번호에 해당하는 num이라는 prop 을 추가한다면? 

```react
//Dice.js

import diceBlue01 from './assets/dice-blue-1.svg';
import diceBlue02 from './assets/dice-blue-2.svg';
import diceBlue03 from './assets/dice-blue-3.svg';
import diceBlue04 from './assets/dice-blue-4.svg';
import diceBlue05 from './assets/dice-blue-5.svg';
import diceBlue06 from './assets/dice-blue-6.svg';
import diceRed01 from './assets/dice-red-1.svg';
import diceRed02 from './assets/dice-red-2.svg';
import diceRed03 from './assets/dice-red-3.svg';
import diceRed04 from './assets/dice-red-4.svg';
import diceRed05 from './assets/dice-red-5.svg';
import diceRed06 from './assets/dice-red-6.svg';

const DICE IMAGES = {
    blue: [diceBlue01, diceBlue02, diceBlue03, diceBlue04, 				   diceBlue05, diceBlue06],
    red: [diceRed01, diceRed02, diceRed03, diceRed04, diceRed05, 		   diceRed06],
};


// Destructuring 문법을 활용해서 코드 정리하기 

function Dice({ color="blue", num = 1}) {
    const src = DICE_IMAGES[color][num -1];
    const alt = `${color} ${num}`;
    return <img src={src} alt={alt} />;
}

export default Dice;
```

```react
//App.js

import Dice from './Dice';

function App() {
    return (
        <div>
        	<Dice color="red"  num={2} />
        </div>
    );
}

export default App;//App.js
```

> `num={2}` props 을 추가할때 자바스크립트 숫자 2를 표현하려면 반드시 중괄호를 사용해야 한다. 



#### 7. children

> 컴포넌트의 자식들을 값으로 갖는 prop 이다. 

```react
//Button.js

function Button({ children }) {
    return <button>{children}</button>;
}

export default Button;
```

```react
//App.js

<Button>던지기</Button>
<Button>처음부터</Button>
```

> 직관적으로 코드를 작성 할 수 있는 방법 
>
> > 컴포넌트 함수에서 따로 가공하지 않고 단순히 보여 주기만 할 모습은 이렇게 children prop을 활용해서 좀 더 직관적으로 활용가능 



#### 8. State

> `State` 를 바꾸면 리액트가 알아서 화면을 새로 렌더링 해준다. 

> 1. `useState` 라는 함수 불러오기 
> 2. `useState`  함수는 파라미터로 초기값을 전달 받고 이 함수가 실행된 다음에는 배열의 형태로 요소 두개를 리턴하게 된다.  그래서 보통 배열의 Destructuring 문법으로 코드를 작성하게 되는 것이다. 
>
> ```react
> import { useState } from 'react';
> 
> function App(){
>     const [num, setNum] = useState(1);
> }
> ```
>
> * 이 배열의 두 요소들 중에서 첫 번째 요소는 Staet 값이다. 
>
>   (쉽게 말해, 현재 변수의 값을 나타내는 것 )
>
> * 두번째 요소는 `setter` 함수 이다.  이 함수를 호출할 때 파라미터로 전달하는 값으로 State 값이 변경이 되는 것이다. 
>
> 3. State 를 사용할 떄는 변수에 새로운 값을 할당하면서 값을 변경하는 것이 아닌 반드시 `setter` 함수를 통해서만 값을 변경해야 한다. 
>
> * 그렇게 때문에 변수도  const 키워드로 선언하고 `setter` 함수의 이름도 사실은 어떤 이름도 지어 주건 상관없지만 일반적으로 State 이름 앞에 `set` 을 붙인 형태로 이름을 짓는 것이다. 



* num State를 3으로 바꾸는 handleRollClick이라는 함수 만들기 

```react
//App.js

import { useState } from 'react';
import Button from './Button';
import Dice from './Dice';

fuction App() {
    const [num, setNum] = useStaet(1);
    
    const handleRollClick = () => {
        setNum(3);
    };
}

return (
    <div>
        <div>
            <Button onClick={handleRollClick}>던지기</Button>
        </div>
    </div>
)
```

* onClick 이벤트에 onClick props을 등록해주기 

```react
//Button.js

function Button({ children, onClick }){
    retrun <button onClick={onClick}>{children}</Button>;
}

export default Button;
```

* 랜덤 함수 만들기 

> 파라미터 n으로 숫자값을 전달 받아서 1부터 n까지의 랜덤한 정수를 반환하는 함수 

```react
//App.js

function random(n) {
    return Math.ceil(Math.random() * n);
}

function App() }{
    const [num, setNum] = useState(1);
    
    const handleRollClick = () => {
        const nextNum = random(6);
        setNum(nextNum);
    };
}
```

> random(6) 을 할당해 준 다음에 이 값으로 `setNum` 함수를 호출해주면 던지기 버튼을 누를 때마다 랜던한 숫자로 num State 가 변경된다. 

* num State의 값을 1로 바꾸는 handleClearClick 이라는 함수 만들기 

```react
const handleClearClick = () => {
    setNum(1);
};

<Button onClick={handleClearClick}>처음부터</Button>
```



#### 9. 참조형 State

> 주사위 게임에서 총점을 계산하는 기능과 매번 점수를 기록하는 기능을 만들면서 배열이나 객체 같은 참조형 State를 다룰 때 주의할 점 



> 1. useState 을 활용하여 sum이라는 State 만들기 
>
> ```react
> //sum State에 새로 나온 주사위 숫잣값을 더해줄 것이다.
> //당연히 state 값을 변경하려면 setter 함수를 활용해야 한다. 
> const [sum, setSum] = useState(0);
> 
> //던지기 버튼을 누를 때마다 새로운 주사위 숫잣값이 sum State에 더해진다. 
> const handleRollClick = () => {
>     const nextNum = random(6);
>     setNum(nextNum);
>     setSum(sum + nextNum);
> };
> 
> //숫잣값 0을 전달하도록 작성하기 
> const handleClearClick = () => {
>     setNum(1);
>     setSum(0);
> };
> 
> return (
>     <div>
>         <h2>나</h2>
>         <Dice color="blue" num={num} />
>         <h2>총점</h2>
>         <p>{sum}</p>
>     </div>
> )
> ```
>
> 2. 점수 기록 만들기 : 하나씩 기록하기 때문에 배열로 만들어 주기 
>
> > (1) 빈 배열을 초깃값으로 갖는 `gameHistory` 라는 State를 만들기
> >
> > ```react
> > const [gameHistory, setGameHistory] = useState([]);
> > ```
> >
> > (2) push 메소드로 nextNum을 추가한 다음에 `setter` 함수로 새 값이 추가된 `gameHistory` 를 전달해 준다. 
> >
> > ```react
> >   const handleRollClick = () => {
> >     const nextNum = random(6);
> >     setNum(nextNum);
> >     setSum(sum + nextNum);
> >     setGameHistory([...gameHistory, nextNum]);
> >   };
> > ```
> >
> > (3) 초기화 함수는 초깃값인 빈 배열을 전달해 주면 된다. 
> >
> > ```react
> >  const handleClearClick = () => {
> >     setNum(1);
> >     setSum(0);
> >     setGameHistory([]);
> >   };
> > ```
> >
> > (4) 각 주사위 숫잣값들을 쉽표로 연결해서 보여줄 것이다. 
> >
> > ```react
> > {gameHistory.join(', ')}
> > ```
> >
> > `join` 메소드는 argument 로 전달한 값을 배열의 각 요소들 사이사이에 넣어서 결과적으로 하나의 문자열로 만들어 준다. 
>
> 3. ⭐ 배열은 기본형이 아니라 참조형이다. ⭐
>
> 따라서 `gameHistory` 변수는 기록들을 가진 배열 자체를 값으로 갖는 것이 아닌 그 배열을 가리키고 있는 주솟값을 가지고 있는 것이다. 그렇기 떄문에 메소드를 이용해서 배열의 새로운 요소를 집어 넣더라도 `gameHistory` 변수가 가지고 있는 배열의 주솟값은 전혀 변하지 않은 것이다. 
>
> 그래서 이렇게 배열이나 객체 같은 참조형 타입의 State를 변경할 때는 **아예 새롭게 만든다고 생각하는 것이 좋다.** 가장 간단한 방법은 `spread` 문법을 활용하는 것이다. 
>
> ```react
>   const handleRollClick = () => {
>     const nextNum = random(6);
>     setNum(nextNum);
>     setSum(sum + nextNum);
>     setGameHistory([...gameHistory, nextNum]);
>   };
> ```



#### 10. 컴포넌트가 좋은 이유 

> `Component` : 부품
>
> * 반복적인 개발이 줄어든다. 
> * 오류를 고치기 쉽다 
> * 일을 쉽게 나눌 수 있다 (협업 장점)



#### 11. 컴포넌트 재사용하기 & 코드 정리하기 

* 자식 컴포넌트의 state를 부모 컴포넌트로 올려주는 걸 `State Lifting` 이라고 한다. 

```react
const [num, setNum] = useState(1);
    const [sum, setSum] = useState(0);
    const [gameHistory, setGameHistory] = useState([]);
    const [otherNum, setOtherNum] = useState(1);
    const [otherSum, setOtherSum] = useState(0);
    const [otherGameHistory, setOtherGameHistory] = useState([]);
```



#### 12. 리액트가 랜더링 하는 방식 

> 리액트 컴포넌트는 `props` 랑 `state` 을 사용하여 데이터마다 다른 화면을 보여줄 수 있다.
>
> state가 바뀌었을때 리액트가 렌더링 하는 방식은? 

* 기본적으로 HTML 요소들은 DOM 트리라고 하는 자료구조로 저장되어있다. 마찬가지로 리액트 내부에서는 DOM 트리를 본떠서 만든 `Virtual DOM` 이라는 자료구조를 사용한다. 

* State 변경 전의 Virtual DOM과 변경 후의  Virtual DOM을 비교한다. 이러한 과정을 통해 바뀐 부분만 찾아내여 각각에 해당하는 실제 DOM노드를 변경하는 것이다. 

  * 단순하고 깔끔한 코드를 작성할 수 있는 장점이 있다. 

  * 변경 사항들을 효율적으로 처리할 수 있는 장점이 있다. 

    (변경사랑을 바로 DOM에 보내지 않고 변경사항들을 모아서 적당이 나눠 브라우저에 전달한다.  )

* 리액트와 유사한 웹 기술들은 대부분 `Virtual DOM` 개념을 활용하고 있다. 
  * `Virtual DOM(가상DOM) `효율적인 화면을 처리할 수 있는 장점이 있다.



#### 13. 인라인 스타일 

![image-20230406161526204](C:\Users\areur\AppData\Roaming\Typora\typora-user-images\image-20230406161526204.png)

> * Button 컴포넌트의 `prop` 값에 따라 두 버튼이 스타일을 다르게 만들기
>
> ```react
> // 서로 공통되는 부분
> const baseButtonStyle = {
>     padding: '14px 27px',
>     outline: 'none',
>     cursor: 'pointer',
>     borderRadius: '9999px',
>     fontSize: '17px',
>   };
> ```
>
> ```react
> // Spread문법으로 펼쳐 준 다음에 
> // 서로 다르게 적용되어야 하는 스타일만 각 객체에 따로 추가해준 것
> 
>  const blueButtonStyle = {
>     ...baseButtonStyle,
>     border: 'solid 1px #7090ff',
>     color: '#7090ff',
>     backgroundColor: 'rgba(0, 89, 255, 0.2)',
>   };
>   
>   const redButtonStyle = {
>     ...baseButtonStyle,
>     border: 'solid 1px #ff4664',
>     color: '#ff4664',
>     backgroundColor: 'rgba(255, 78, 78, 0.2)',
>   };
> ```
>
> * Button 컴포넌트 함수에서 `color prop`을 추가해주고 그 아래 조건 연산자로 style 변수를 만들어 주면 `color prop` 값이 red인 경우에는 `redButtonStyle` 을 그렇지 않은 경우에는 `blueButtonStyle` 을 적용한다. 
> * Button에 각각 color prop 전달해주기 
>
> ```react
> <Button color="blue" onClick={handleRollClick}>던지기</Button>
> <Button color="red" onClick={handleClearClick}>처음부터</Button>
> ```
>
> ![image-20230406162158142](C:\Users\areur\AppData\Roaming\Typora\typora-user-images\image-20230406162158142.png)



#### 14. CSS 클래스네임

* 함수 내부에는 `color prop`에 따라서 스타일 객체 값이 바뀌는 것이 아닌 `className` 값이 달라지도록 해야한다. 

##### ⭐클래스 명을 추가할 때 빈 공백이 필요하다는 점 참고하기

```react
import './Button.css';

function Button({ className = '', color = 'blue', children, onClick }) {
  const classNames = `Button ${color} ${className}`;
  return (
    <button className={classNames} onClick={onClick}>
      {children}
    </button>
  );
}

export default Button;
```



---

* #### 디자인 적용하는 방법과 팁

> 1. 이미지 불러오기 
>
>    이미지 파일은 `import` 구문을 통해 불러오고, 불러온 이미지 주소를 `src` 속성으로 사용한다. 
>
>    ```react
>    import diceImg from './assets/dice.png';
>    
>    function Dice() {
>      return <img src={diceImg} alt="주사위 이미지" />;
>    }
>    
>    export default App;
>    ```
>
> 2. 인라인 스타일 
>
>    리액트에서 인라인 스타일은 문자열이 아닌 **객체형**으로 사용
>
>    프로퍼티 이름은 CSS 속성 이름으로, 프로퍼티 값은 CSS 속성 값으로 쓰는데요, 이때 프로퍼티 이름은 아래의 `boarderRadius` 처럼 **대시 기호 없이 카멜 케이스로** 써야 한다는 점도 꼭 기억
>
>    ```react
>    import diceImg from './assets/dice.png';
>    
>    const style = {
>      borderRadius: '50%',
>      width: '120px',
>      height: '120px',
>    };
>    
>    function Dice() {
>      return <img style={style} src={diceImg} alt="주사위 이미지" />;
>    }
>    
>    export default App;
>    ```
>
> 3. CSS 파일 불러오기
>
>    `import` 구문으로 파일을 불러올 수 있는데요, 이때 `from` 키워드 없이 사용하면 된다. 
>
>    ```react
>    import diceImg from './assets/dice.png';
>    import './Dice.css';
>    
>    function Dice() {
>      return <img src={diceImg} alt="주사위 이미지" />;
>    }
>    
>    export default App;
>    ```
>
> 4. 클래스네임 사용하기 
>
>    CSS 파일에 정의된 클래스명을 `className` prop에 문자열로 넣어줄때 재사용성을 위해 `className` prop을 부모 컴포넌트에서 받으면 더 좋다. 
>
>    ```react
>    import diceImg from './assets/dice.png';
>    import './Dice.css';
>    
>    function Dice({ className = '' }) {
>      const classNames = `Dice ${className}`;
>      return <img className={classNames} src={diceImg} alt="주사위 이미지" />;
>    }
>    
>    export default App;
>    ```

---



