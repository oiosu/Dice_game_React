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



