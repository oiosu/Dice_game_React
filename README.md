# React 웹 개발 시작하기 
> 🟣 코드잇을 통해 `React 웹 개발 시작하기` 공부한 내용을 정리 
### [🎲 주사위게임](http://dicegame.react.su.s3-website.us-east-2.amazonaws.com/)
![image](https://user-images.githubusercontent.com/99783474/230758280-1b9829d8-a8f2-45ef-a38e-b808e9bc5ae7.png)

<br>

## [0. React Start](https://github.com/oiosu/React-web/blob/master/01_REACT%20%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0.md)
* `create-react-app` 으로 리액트 프로젝트 생성 
* `npm init react-app <폴더 이름>` 혹은 
* 폴더를 VS Code로 열고 터미널에서 `npm init react-app .` 
* 개발 모드 실행 : `npm run start`
* 개발 모드 종료 : `ctrl+c`

<br>

## [1. `index.html` 파일에서 하는 일](https://github.com/oiosu/React-web/blob/master/02_1.%20%EC%9D%B8%EB%8D%B1%EC%8A%A4%20%ED%8C%8C%EC%9D%BC%EC%97%90%EC%84%9C%20%ED%95%98%EB%8A%94%20%EC%9D%BC.md)
> * 웹 브라우저에서 가장 먼저 실행되는 파일 
* 

> ```react
> import ReactDOM from 'react-dom/client';
> 
> 
> const root = ReactDOM.createRoot(document.getElementById('root'));
> root.render(<h1>안녕 리액트!</h1>);
> 
> ReactDOM.render(
> <>
> <h1 id='title'>가위바위보</h1>
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


<br>

## [2. JSX](https://github.com/oiosu/React-web/blob/master/02_2.%20JSX.md)
> 자바스크립트 파일 안에 HTML 태그를 사용하는 문법 
>
> 리액트에서 지원하는 JSX 문법
>
> 자바스크립트의 확장된 문법

* `주의사항` : 자바스크립트의 확장된 문법이기 때문에 HTML 문법을 완전히 그대로 사용할 수는 없다.  대표적으로 `class`와 `for` 이다. 

<br>

## [3. Fragment](https://github.com/oiosu/React-web/blob/master/02_3.%20Fragment.md)
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


<br>

## [4. JSX에서 자바스크립트 사용하기](https://github.com/oiosu/React-web/blob/master/02_4.%20JSX%EC%97%90%EC%84%9C%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0.md)
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

<br>

## [5. Component](https://github.com/oiosu/React-web/blob/master/02_5.%20Component.md)
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

<br>

## [6. Props](https://github.com/oiosu/React-web/blob/master/02_6.%20Props.md)

* properties 의 줄임말
* Component에 전달된 속성을 모두 가리키기 때문에 각각의 속성은 prop라고 부른다.\
* Component 태그에 지정해준 속성은 하나의 객체 형태로 컴포넌트 함수의 첫번째 파라미터로 전달된다.

<br>

## [7. children](https://github.com/oiosu/React-web/blob/master/02_7.%20children.md)
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


<br>

## [8. State](https://github.com/oiosu/React-web/blob/master/02_8.%20State.md)
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


<br>

## [9. 참조형 State](https://github.com/oiosu/React-web/blob/master/02_9.%20%EC%B0%B8%EC%A1%B0%ED%98%95%20State.md)
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
> > const handleRollClick = () => {
> > const nextNum = random(6);
> > setNum(nextNum);
> > setSum(sum + nextNum);
> > setGameHistory([...gameHistory, nextNum]);
> > };
> > ```
> >
> > (3) 초기화 함수는 초깃값인 빈 배열을 전달해 주면 된다. 
> >
> > ```react
> > const handleClearClick = () => {
> > setNum(1);
> > setSum(0);
> > setGameHistory([]);
> > };
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

<br>

## [10. Component 장점 ](https://github.com/oiosu/React-web/blob/master/02_10.%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%20%EC%9E%A5%EC%A0%90.md)
`Component` : 부품

* 반복적인 개발이 줄어든다. 
* 오류를 고치기 쉽다 
* 일을 쉽게 나눌 수 있다 (협업 장점)

<br>

## [11. 컴포넌트 재사용하기 & 코드 정리하기 ](https://github.com/oiosu/React-web/blob/master/02_11.%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%20%EC%9E%AC%EC%82%AC%EC%9A%A9%26%EC%BD%94%EB%93%9C%EC%A0%95%EB%A6%AC.md)
* 자식 컴포넌트의 state를 부모 컴포넌트로 올려주는 걸 `State Lifting` 이라고 한다. 

```react
const [num, setNum] = useState(1);
    const [sum, setSum] = useState(0);
    const [gameHistory, setGameHistory] = useState([]);
    const [otherNum, setOtherNum] = useState(1);
    const [otherSum, setOtherSum] = useState(0);
    const [otherGameHistory, setOtherGameHistory] = useState([]);
```

<br>

## [12. 리액트가 랜더링 하는 방법](https://github.com/oiosu/React-web/blob/master/02_12.%20%EB%A6%AC%EC%95%A1%ED%8A%B8%EA%B0%80%20%EB%9E%9C%EB%8D%94%EB%A7%81%20%ED%95%98%EB%8A%94%20%EB%B0%A9%EC%8B%9D.md)
> > 리액트 컴포넌트는 `props` 랑 `state` 을 사용하여 데이터마다 다른 화면을 보여줄 수 있다.
> >
> > state가 바뀌었을때 리액트가 렌더링 하는 방식은? 



> * 기본적으로 HTML 요소들은 DOM 트리라고 하는 자료구조로 저장되어있다. 마찬가지로 리액트 내부에서는 DOM 트리를 본떠서 만든 `Virtual DOM` 이라는 자료구조를 사용한다. 
>
> * State 변경 전의 Virtual DOM과 변경 후의  Virtual DOM을 비교한다. 이러한 과정을 통해 바뀐 부분만 찾아내여 각각에 해당하는 실제 DOM노드를 변경하는 것이다. 
>
>   * 단순하고 깔끔한 코드를 작성할 수 있는 장점이 있다. 
>
>   * 변경 사항들을 효율적으로 처리할 수 있는 장점이 있다. 
>
>     (변경사랑을 바로 DOM에 보내지 않고 변경사항들을 모아서 적당이 나눠 브라우저에 전달한다.  )
>
> * 리액트와 유사한 웹 기술들은 대부분 `Virtual DOM` 개념을 활용하고 있다. 
>
>   * `Virtual DOM(가상DOM) `효율적인 화면을 처리할 수 있는 장점이 있다.

<br>

## [13. 인라인 스타일](https://github.com/oiosu/React-web/blob/master/02_13.%20%EC%9D%B8%EB%9D%BC%EC%9D%B8%20%EC%8A%A4%ED%83%80%EC%9D%BC.md)
<br>
## [14. CSS 클래스네임](https://github.com/oiosu/React-web/blob/master/02_14.%20CSS%20%ED%81%B4%EB%9E%98%EC%8A%A4%EB%84%A4%EC%9E%84.md)
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



----

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


<br>

---
<br>

# [React 배포하기](https://github.com/oiosu/React-web/blob/master/03_REACT%20%EB%B0%B0%ED%8F%AC%ED%95%98%EA%B8%B0.md) 
#### 1. 빌드하기 

```bash
npm run build
```

> `build` 라는 폴더 생성

```bash
npx serve build
```

> 방금 생성한 `build` 라는 폴더에서 서버를 실행



#### 2. 명령어 복습하기 

* 프로젝트 생성

  ```
  npm init react-app .
  ```

* 개발 모드 실행 

  ```
  npm start (npm run start)
  ```

* 실행 중인 서버 종료 

  ```
  ctrl + c
  ```

* 개발된 프로젝트 빌드 

  ```
  npm run build
  ```

* 빌드 한 것 로컬에서 실행

  ```
  npx serve build
  ```

  

#### 3. 웹 사이트 배포하기(AWS S3)

* AMAZON S3 > 버킷

* `버킷` : S3 파일을 모아두는 큰 저장소

> 1. 버킷 이름 설정 : `dicegame.react.su`
> 2. 버킷 액세스 차단 설정 : 체크 해체, 체크 표시는 다음과 같다. 
>
> ![image](https://user-images.githubusercontent.com/99783474/230757442-459b2bce-4c2d-4083-94d6-b9326d6ee6fa.png)
>
> 3. 버킷 만들기 
> 4. 속성 > 정적 웹 사이트 호스팅 편집 > `활성화` 체크 
> 5. 인텍스 문서 : `index.html`
> 6. 오류 문서 : `index.html`
> 7. 권한 > 버킷 정책 > 편집 > 정책 생성기 
>    * 웹 브라우저가 버킷에서 할 수 있는 권한을 설정해주는 것
>
> ![image](https://user-images.githubusercontent.com/99783474/230757448-08d206cf-28b7-4fe1-9db0-fb704143c3bb.png)
>
> 8. Add Statement > Generate Policy 
>    * Policy JSON Document => 정책부분에 복붙하기 > 변경사항 저장
> 9. 객체 > 업로드 (build 폴더 안에 있는 모든 파일 끌어다 놓기) > 업로드
> 10. 업로드가 완료가 된다면 속성 > 정적 웹 사이트 호스팅 > 생성된 url 로 접속하면 배포된 것을 확인 할 수 있다. 



#### 4. 배포한 리액트 코드가 어떻게 실행되는가

* 웹 브라우저에서는 JSX 문법을 사용할 수 없다. 그래서 JSX는 순수한 자바스크립트로 변역해서 실행되어야 한다. 

* `babeljs.io` 사이트에 접속하면 Babel 이라는 프로그램을 통해 JSX가 어떻게 순수 자바스크립트로 번역되는지 확인 할 수 있다. 

* BABEL은 JSX를 JS로 번역해주는 프로그램들 중에서 가장 대표적인 프로그램이다. (=트랜스파일러)

* 자바스크립트 파일을 과자처럼 묶어서 하나의 파일로 만든다. 이런 형식으로 번들 파이을 만드는 것을 `번들링`이라고 한다. 

  (번역된 코드들은 번들링을 통해 웹 브라우저가 다운받기 좋도록 묶으므로 만들어진다.)





