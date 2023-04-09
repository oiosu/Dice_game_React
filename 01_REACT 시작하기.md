# 01_REACT 시작하기

> #### 1. 리액트 탄생
>
> > 처음엔 페이스북 내부에서만 사용하다가 시간이 지나면서 누구나 쓸 수 있게 오픈 소스로 공개가 되었다.
> >
> > 웹 사이트의 URL을 효율적으로 개발하기 위해 만들어진 기술이지만 리액트의 영향력은 브라우저에서 그치지 않고 모바일까지 뻗어나간다. 
> >
> > 리액트로 개발한 UI 코드를 조금만 변형해서 모바일 앱으로 만들 수는 없을까고민하다 등장한 것이 바로 리액트 네이티브이다. 



---



#### 2. 나의 첫 리액트 프로젝트

* `NODE.JS` : 원래 자바스크립트는 이 부라우저 내에서만 실행 가능한 언어인데, 이 기술을 통해 브라우저 밖에서도 사용할 수 있도록 해준다. 

```bash
npm init react-app . 
```

> `.` 현재 디렉토리에 프로젝트를 생성할 것이다.



```bash
react start
```

> localhost:3000 프로젝트 접근
>
> `npm start`

![image-20230405170157032](C:\Users\areur\AppData\Roaming\Typora\typora-user-images\image-20230405170157032.png)



* `npm run start` : 어떤 파일을 수정하면 그것을 인식해서 바로 반영해주는 기능도 한다. = `개발모드를 실행했다.`

---

> ✔️ 요약 
>
> * `create-react-app` 으로 리액트 프로젝트 생성 
> * `npm init react-app <폴더 이름>` 혹은 
> * 폴더를 VS Code로 열고 터미널에서 `npm init react-app .` 
> * 개발 모드 실행 : `npm run start`
> * 개발 모드 종료 : `ctrl+c`

---



#### 3. 리액트 개발자 도구 살펴보기

`react developer tools` 

![image-20230405171400746](C:\Users\areur\AppData\Roaming\Typora\typora-user-images\image-20230405171400746.png)

> ![image-20230405171636140](C:\Users\areur\AppData\Roaming\Typora\typora-user-images\image-20230405171636140.png)