---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 18"
date: 2023-08-09
descripton: "Day 18 in AI+웹개발 취업캠프"
tags:
    - diary
---

# CONTENTS SUMMARY
---
<br>

- [학습 목표](#학습-목표)
- [REVIEW](#review)
- [눈알 애니메이션 만들기](#눈알-애니메이션-만들기)
- [인터넷에 배포](#인터넷에-배포)
- [REFERENCES](#references)

<br><br><br>

## 학습 목표
---
<br>

- CRA 활용, React Hook (useEffect()) 에 대해서 이어서 알아본다.
- 애니메이션 및 media-query에 대한 이해를 높이기 위해 학습한다.
- styled-components와 keyframes 활용을 학습하여 간단한 애니메이션을 만든다.
- Netlify라는 웹호스팅 서비스를 이용하여 React로 만든 앱을 인터넷에 배포하는 방법을 배운다.

<br><br><br>

## REVIEW
---
<br>

### What is CRA?

CRA 또는 Create-React-App은 React를 만든 팀이 지원하는 SPA(Single Page Application)을 만들기 위해 사용하는 툴입니다.

다음 명령어를 실행하면 CRA를 통해 기본 템플릿을 가지고 있는 `my-app` 이라는 React 앱이 자동으로 생성됩니다.

```
npx create-react-app my-app
```

<br><br><br>

### Files & Terminology used in CRA and React

index.html
- contains metadata, basic information and data for react app
- can change title of webpage here

index.js
- calls on the components of React App and shows them on screen

React Component
- React app에서 표시해주는 웹 콘텐츠(요소)

JSX
- React 앱에서 콘텐츠를 표현하는 문법

함수형 component
- JavaScript 함수가 마크업 콘텐츠를 반환하는 형태

<br><br><br>

### React Hook

React Hook란 함수형 component에다가 기능을 추가하는 함수입니다.
지금까지 리액트 후크들 중에 `useState()`와 `useEffect()`를 실습하면서 사용을 해봤습니다.

#### `useEffect`

- react component의 생명주기에 따라 동작을 제어할 수 있는 기능을 제공한다.
- callback 함수를 입력받아 특정 생명주기마다 이를 호출한다.

```
useEffect(callback_function)
```

또한 두번째 인수(argument)로 의존성 배열을 전달받아 callback 함수의 호출 타이밍을 결정한다.

```
useEffect(callback_function, dependency_array)
```

의존성 배열에 상태명을 입력하면, 특정 상태가 변경될 때마다 callback 함수가 동작하도록 설정할 수 있다.

```
useEffect(() => {
	console.log('todo 값이 설정됨');
}, [todo]); 
```
NOTE. 상태 todo가 변경되면 이 callback 함수가 동작할 예정이다.


```jsx
function App() {
    // input에 입력되는 내용을 state(상태)에다 저장 
    // 처음에 아무것도 입력하지 않은 상태 --> useState() 초기화 --> "" 문자열로
    // 결과 : text, setText
    const [text, setText] = useState("")

    return <>
        <input type="text" placeholder='아무 내용' />
        <p>{text}</p>
    </>
}

export default App
```

![](/posts/posts_images/aiweb_day18/useEffect_1.png)

### text 상태를 업데이트하면서 표시하는 방법

상태가 변화되려면 상태 변화 함수를 같이 사용해야 한다고 배웠습니다.
상태 변화 함수는 `useState()`가 자동으로 만들어주니 이름만 붙여서 쓰면 됩니다. 여기서 텍스트 내용을 변경해주는 상태 변화 함수를 `setText`라고 부르겠습니다. 

`setText`를 부르기 전, 먼저 텍스느 내용이 바뀔 때마다 변화가 `useState()`를 통해 잘 인식되는지 확인했습니다. 이를 확인하기 위해 텍스트 내용을 입력하면서 콘솔 창에 상태마다의 텍스트 변화를 출력했습니다.

```jsx
    return <>
        <input type="text" placeholder='아무 내용' onChange={(e) => { console.log(e.target.value) }}/>
        <p>{text}</p>
    </>
```

![](/posts/posts_images/aiweb_day18/useEffect_2.png)

상태의 변화가 잘 인식되는 것을 확인한 후, 내용이 변경될 때마다 `setText` 함수를 호출하도록 설정했습니다. 다음과 같이 input에서 `onChange()` 속성을 통해 event handler 함수 `setText`를 호출했습니다.

```jsx
    return <>
        <input type="text" placeholder='아무 내용' onChange={(e) => { setText(e.target.value) }}/>
        <p>{text}</p>
    </>
```

![](/posts/posts_images/aiweb_day18/useEffect_3.png)


<br><br><br>

## 눈알 애니메이션 만들기
---
<br>


styled-components와 keyframes 가져오기
```jsx
import styled, { keyframes } from 'styled-components';
```

눈알 컴포넌츠
- 눈알을 표시하는 웹요소로 styled 컴포넌츠 하나 만들기

눈알 2개를 가운데 병렬하기 위해 하나의 container로 사용할 Eyes를 만들어봤습니다.

```jsx
const Eyes = styled.div`
  display: flex;
  justify-content: center;
`
```

그 다음, 각 눈알로 사용할 Eye 컴포넌트 만들었습니다.

```jsx
const Eye = styled.div`
  width: 200px;
  height: 200px;
  border: 5px solid black;
  border-radius: 50%;
  position: relative;
`
```

NOTE. `position: relative;`를 사용한 이유는 position을 통해 Eyes의 자식 요소가 될 눈알을 제어할 예정이기 때문입니다.

그리고 각 눈알 안에서 움직일 눈동자 컴포넌트 Pupil을 만들었습니다.

```jsx
const Pupil = styled.div`
  width: 40px;
  height: 40px;
  background-color: brown;
  border-radius: 50%;
  position: absolute;
`
```

NOTE. 눈동자는 어떤 시작점에서 부터 자유롭게 왔가갔다 이동을 시킬 것이기 때문에`position: absolute;`를 통해 절대위치를 지정했습니다. absolute position은 상위 요소/부모 요소의 기준을 잡게 됩니다. 

asbsolute position은 position이 지정된 요소를 기준으로 움직이기 때문에 상위 요소는 relative position이 지정되어 있어야 합니다.

이 상태에서 keyframe을 만들어서 animation을 넣고 싶은 component에다 keyframe을 적용하면 animation을 만들 수 있습니다.

```jsx
const moving = keyframes`
  from {
    top: 40%;
    left: 10%;
  }
  to {
    top: 40%;
    left: 70%;
  }
`
```

```jsx
const Pupil = styled.div`
  width: 40px;
  height: 40px;
  background-color: brown;
  border-radius: 50%;
  position: absolute;
  animation: ${moving} 3s 0s linear alternate infinite;
`
 // speed 3s, no delay, linear acceleration, alternate direction, infinite loop
```

NOTE. `alternate`는 애니메이션 keyframe이 이동하는 방향을 번갈아 reverse하여 나타내는 setting입니다. `alternate`를 설정해야 눈동자는 왼쪽에서 오른쪽으로 갔다가 왼쪽에서 다시 시작하지 않고 오른쪽에서 왼쪽으로 가고, 왼쪽에서 오른쪽으로 가서 실제 눈처럼 움직이는 자연스러운 애니메이션 효과를 낼 수 있습니다.

마침내로, 화면에 모두 표시를 해봅니다.

```jsx
function App() {
  return (
    <Eyes>
      <Eye className="left_eye"><Pupil /></Eye>
      <Eye className="right_eye"><Pupil /></Eye>
    </Eyes>
  );
}
```

`className`을 만들 필요가 없지만, 코드에서 구별할 수 있기 위해 왼쪽과 오른쪽 눈알의 `className`을 지었습니다.

#### OUTPUT

<img src="/posts/posts_images/aiweb_day18/animated_eyes_final.gif" style="width: 500px;">

<br>

#### ADDITIONAL

눈동자의 크기를 증가하고 추가로 눈동자 색깔이 빠뀌면서 위치가 위아래로 가는 애니메이션을 넣어봤습니다.

```jsx
const rollingColor = keyframes`
  from {
    top: 40%;
    left: 10%;
  }
  25% {
    background-color: #F1C40F;
    top: 20%;
    left: 20%;
  }
  50% {
    background-color: #0FDBDB;
    top: 10%;
    left: 25%;
  }
  75% {
    background-color: #C9EDED;
    top: 20%;
    left: 30%;
  }
  100% {
    background-color: #D5D8DC;
    top: 40%;
    left: 40%;
  }
`
```

```jsx
const Pupil = styled.div`
  width: 100px;
  height: 100px;
  background-color: brown;
  border-radius: 50%;
  position: absolute;
  animation: ${rollingColor} 3s 0s linear alternate infinite;
`
```

그리고, `App06.css` 스타일시트 파일을 만들어 배경 색깔을 넣고 눈알의 위치와 스타일링을 변경했습니다.

```jsx
// App06.css
body {
    background-color: #1C2833;
}
```

```jsx
// App06.js
...
import './App06.css'
...
```

```jsx
// 눈알 2개를 중앙으로 설정
const Eyes = styled.div`
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
`

// 눈알의 배경색깔을 하얀색으로, border 색깔을 커스텀 색깔로 설정
const Eye = styled.div`
  width: 200px;
  height: 200px;
  border: 20px solid #212F3D;
  border-radius: 50%;
  position: relative;
  background-color: #FCFCFC;
`
```

<img src="/posts/posts_images/aiweb_day18/animated_eyes_modified_final.gif" style="width: 1000px;">

<br><br><br>

## Media Queries
---
<br>

요즘 반응형(Interactive) 웹사이트를 만드는 과정에 미디어 쿼리(Media Query)가 많이 활용되고 있습니다.

미디어 쿼리(Media Query)란 media의 type을 인식하고 contents를 읽어들이는 기기나 브라우저의 물리적 속성을 감지할 수 있는 유용한 모듈 또는 기능입니다.

각 미디어 쿼리는 항상 두 가지의 요소로 구성되어 있습니다.
1) media type
2) query (조건에 대한 물음)

<br>

### styled-components + media query

styled component 내부에 media query 적용 스타일의 선언문을 다음과 같이 정의할 수 있습니다.

```jsx
const Box = styled.div`
    width: 100px;
    height: 100px;
    background-color: tomato;

    //media query 선언
    @media screen and (min-width: 768px) {
        width: 50px;
        height: 50px;
    }
`
```

<br><br><br>

## 인터넷에 배포
---
<br>

인터넷에 어떤 웹앱이나 웹사이트를 쉽게 배포할 수 있게 해주는 서비스는 웹호스팅 (Web Hosting) 서비스라고 합니다. 윕호스팅(Web Hosting) 서비스들 중에 Netlify라는 서비스를 한번 사용해봤습니다.

CRA(Create-React-App)을 통해 `npm run build` 명령어를 실행하여 build 폴더를 만든 후, 해당 build 폴더를 Netlify에 업로드하여 움직이는 애니메이션을 포함한 웹앱을 배포해 봤습니다.

### Netlify 링크

https://nipa-frontend-animated-eyes-4-eunice.netlify.app/

<br><br><br>

## REFERENCES
---
<br>

- Create React App (Official Documentation).
https://create-react-app.dev/
- Inside create-react-app.
https://medium.datadriveninvestor.com/inside-create-react-app-8f37ed9372f8
- Using the Effect Hook.
https://legacy.reactjs.org/docs/hooks-effect.html
- Built-in React Hooks.
https://react.dev/reference/react

<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프