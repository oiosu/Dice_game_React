# React 웹 개발 시작하기 
> 🟣 코드잇을 통해 `React 웹 개발 시작하기` 공부한 내용을 정리 

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
