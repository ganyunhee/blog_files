---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 19"
date: 2023-08-10
descripton: "Day 19 in AI+웹개발 취업캠프"
tags:
    - diary
---

# CONTENTS SUMMARY
---
<br>

- [학습 목표](#학습-목표)
- [주요한 JavaScript 스킬 리뷰](#주요한-javascript-스킬-리뷰)
- [CRA 미니 프로젝트 과정 : 할일 목록 만들기](#cra-미니-프로젝트-과정--할일-목록-만들기)
- [CRA 미니 프로젝트 결과 : 할일 목록 만들기](#cra-미니-프로젝트-결과--할일-목록-만들기)
- [TO IMPROVE](#to-improve)
- [REFERENCES](#references)

<br><br><br>

## 학습 목표
---
<br>

- 미니 프로젝트 진행에 필요한 세부 기술을 리뷰한다.
- 미니 프로젝트로 할일 목록(TODO List) React App 만든다.
- 미니 프로젝트를 netlify를 통해 배포한다.

<br><br><br>

## 주요한 JavaScript 스킬 리뷰
---
<br>

할일 목록 프로젝트 작업을 진행하기에 앞서서 먼저 주요한 JavaScript 스킬이나 React 라이브러리를 리뷰했습니다.

### Sample.js 만들기
<br>

TODO List를 만들기 전에 `Sample.js` 파일을 만들어서 TODO List 앱과 비슷한 기능을 사용하는 Food List 앱을 만들어봤습니다. 다음 

```jsx
import Sample from './Sample'
```
<!--리뷰에 대해서 자세히 작성할지 고민-->
<!--중요한 기능 짧게 설명-->

간단하게 배열을 다루는 방법, JSX syntax 또는 변수 표현하는 방법, map과 filter를 사용하는 방법, `useEffect`, `useState` 이 두 가지의 React hook를 활용하는 방식 등을 다시 복습했습니다.

<br><br><br>


## CRA 미니 프로젝트 과정 : 할일 목록 만들기
---
<br>

<!--함수, 로직 설명-->
### 할일 목록의 기능 : CRUD로 설명

TODO 목록을 관리하기 위해 생성(Create), 읽어들이기(Read), 업데이트(Update), 삭제(Delete) 기능들이 필요합니다.
즉, TODO 목록 프로그램이 기본적으로 가져야 할 기능들은 TODO 생성, 데이터를 가져오기, 데이터를 저장하고 업데이트, 그리고 TODO를 삭제하는 기능입니다.

### 데이터 영구저장
<br>

웹 데이터는 휘발성 데이터이므로 웹페이지를 새로고침할 때마다 데이터가 날라가는 상황이 발생됩니다.
TODO 목록 프로그램의 경우에는 웹페이지를 새로고침해도 데이터가 저장되고 잘 불러오는 것이어야 합니다.
따라서, 이번 프로젝트에서도 React를 통해 영구저장을 하는 방식을 실습해봤습니다.

단, 영구저장을 언제 할지 timing이 중요하다고 배웠습니다. 즉, 데이터를 언제 저장할지, 또한 저장된 데이터를 언제 불러올지 생각해야 합니다.
데이터의 영구 저장을 위해 웹앱을 접속하는 각 유저의 local storage에다 데이터를 저장하고 업데이트하면 됩니다.

이 프로젝트에서 데이터를 영구적으로 저장하기 위해 React의 hook인 `useEffect`를 사용합니다.

#### React Hook : Effect Hook (useEffect) 사용
<!--useEffect 왜 사용하는지 작성-->

useEffect는 local storage에다 데이터를 저장하기 위해 사용하는 React hook입니다.

useEffect를 통해 두가지를 해봤습니다.

1. component가 만들어지는 순간마다 local storge 읽어들입니다.

```jsx
  useEffect(() => {
    const defaultTodo = JSON.parse(localStorage.getItem("todo"));

    if(!defaultTodo) return;

    setTodo(defaultTodo)

    if(defaultTodo.length !== 0) {
      setTodo (
        defaultTodo[defaultTodo.length - 1].todoId + 1
      )
    }
  }, [])
```

2. TODO가 갱신될 때마다 local storage에 데이터를 저장했습니다.

```jsx
  useEffect(() => {
    localStorage.setItem("todo", JSON.stringify(todo))
  }, [todo])

  return (
    <Container>
    <Form onSubmit={(e) => {
      e.preventDefault()
      handleSubmit(e.target.todo.value)
      e.target.todo.value = ""
    }}>
      <TextInput type="text" placeholder='할일 쓰기' name="todo" />
      <SubmitInput type="submit" value="추가" />
    </Form>
    <UnorderedList>
      {todo.map((item, index) => (
        <ListItem key={index}>
            <TodoText onClick={() => {
              alert(item.todoDone)
              handleToggle(item.todoId)
            }} style={ item.todoDone ? {textDecoration: 'line-through'} : {} }>{item.todoText}</TodoText>
            <TodoDelete onClick={() => {
              handleDelete(item.todoId)
            }}>X</TodoDelete>
          </ListItem>
      ))}
    </UnorderedList>
    </Container>
  );
}
```

<br><br><br>

### 스타일 커스터마이징 I - App.css

웹앱의 스타일을 마음대로 변경하려면 CSS 파일(`App.css`) 즉 스타일시트를 만들어야 합니다. CSS 파일 안에서 원하는 스타일대로 커스터마이징 한 후 `App.js`안에서 스타일시트를 import하여 적용을 합니다.

```jsx
// App.js 안에서
import "./App.css"
```

이대로 CSS를 활용해 스타일을 개발할 수 있지만, 이보다 더 쉬운 방법이 있습니다 - 이미 만들어진 컴포넌츠를 불러와 사용하는 것입니다.

<br><br><br>

### 스타일 커스터마이징 II - styled-components
<br>

다른 사람이 만든 컴포넌츠 디자인이 마음에 들어 그 컴포넌츠를 자기 react 앱에 사용하기 위해 해주는 react 라이브러리는 styled-components 라이브러리입니다.

styled-components를 사용하는 방법을 배우려고 실습으로 강사님이 만드신 컴포넌츠를 가져와 할일 목록 프로젝트에 사용해 봤습니다.

styled-components 라이브러리를 사용하기 전에 먼저 패키지 매니저를 통해 라이브러리를 설치해야 합니다. 다음 명령어를 실행하여 라이브러리를 설치할 수 있습니다.

```
npm install styled-components
```

그 다음 `styledComponents.js` 파일을 같은 폴더 안에 넣어 안에 있는 컴포넌츠를 확인했습니다. 

```jsx
//styledComponents.js

import styled from "styled-components";

export const Container = styled.div`
  width: 100%;
  height: 100%;
  padding: 1.5rem 0 0;

  display: flex;
  flex-direction: column;
  align-items: center;
`

export const Form = styled.form`
  width: 33%;
  min-width: 375px;
  display: flex;
`
export const TextInput = styled.input`
  width: 80%;
  height: 3rem;
  padding: 0.5rem;
  border: none;
  border-radius: 0.2rem 0 0 0.2rem;

  font-size: 1.2rem;

  &:focus{
    outline: none;
  }
`
export const SubmitInput = styled.input`
  width: 20%;
  height: 3rem;
  border: none;
  border-radius: 0 0.2rem 0.2rem 0;

  color: #ffffff;
  background-color: #5a75aa;
  font-size: 1.2rem;
`

export const UnorderedList = styled.ul`
  width: 33%;
  min-width: 375px;
  height: 10rem;
  padding: 0;

  list-style-type: none;
`
export const ListItem = styled.li`
  padding: 0.375rem;
  margin-bottom: 0.8rem;
  border-radius: 0.2rem; 
  background-color: #FFFFFF;
  
  position: relative;
`

export const TodoText = styled.span`
  display: inline-block;
  width: 90%;
  font-size: 1.2rem;
  line-height: 1.5rem;
`
export const TodoDelete = styled.button`
  width: 10%;
  height: 1.5rem;
  border: none;
  border-radius: 0.5rem; 

  background-color: transparent;
  font-weight: 900;

  position: absolute;
  right: 0;
`
```

`styledComponents.js` 파일 안에서 `Container, Form, TextInput, SubmitInput, UnorderedList, ListItem, TodoText, TodoDelete`라는 컴포넌츠들이 정의되어 있는 것을 확인했으며 다음과 같이 `App.js` 안에 import하여 가져왔습니다.

```jsx
import {
  Container, Form, TextInput,
  SubmitInput, UnorderdList, ListItem,
  TodoText, TodoDelete } from './styledComponents'
```

기존 코드에서 다음과 같이 HTML 원소를 그대로 사용하고 CSS 파일 안에서 각 원소의 스타일을 변경했습니다.

```jsx
return <div>
<form onSubmit={(e) => {
  e.preventDefault()
  handleSubmit(e.target.todo.value)
  e.target.todo.value = ""
}}>
  <input type="text" placeholder='할일 쓰기' name="todo" />
  <input type="submit" value="추가"></input>
</form>
<ul>
  {todo.map((item, index) => {
	return <li key={index}>
		<span onClick={() => {
		  alert(item.todoDone)
		  handleToggle(item.todoId)
		}} style={ item.todoDone ? {textDecoration: 'line-through'} : {} }>{item.todoText}</span>
		<span onClick={() => {
		  handleDelete(item.todoId)
		}}>X</span>
	  </li>
  })}
</ul>
</div>
```

이번에 styled-components 라이브러리를 통해 `styledComponents.js`안에서 이미 만들어진 컴포넌츠들을 가져와 HTML 원소처럼 사용했습니다. 모든 원소를 `<Container>` 안에 넣은 다음, form 또는 ul, li 대신 `<Form>, <UnorderedList>, <ListItem>`을 사용했고 text input과 text submit의 경우 `<TextInput>`과 `<SubmitInput>`으로 수정했고, span이 가지고 있는 텍스트에 따라 `<TodoText>`와 `<TodoDelete>`으로 수정했습니다.

이런 식으로 styled-components 적용한 후 코드는 다음과 같이 변경되었습니다.

```jsx
  return (
    <Container>
    <Form onSubmit={(e) => {
      e.preventDefault()
      handleSubmit(e.target.todo.value)
      e.target.todo.value = ""
    }}>
      <TextInput type="text" placeholder='할일 쓰기' name="todo" />
      <SubmitInput type="submit" value="추가" />
    </Form>
    <UnorderedList>
      {todo.map((item, index) => (
        <ListItem key={index}>
            <TodoText onClick={() => {
              alert(item.todoDone)
              handleToggle(item.todoId)
            }} style={ item.todoDone ? {textDecoration: 'line-through'} : {} }>{item.todoText}</TodoText>
            <TodoDelete onClick={() => {
              handleDelete(item.todoId)
            }}>X</TodoDelete>
          </ListItem>
      ))}
    </UnorderedList>
    </Container>
  );
```

<br>

그리고 화면은 다음과 같이 나타납니다.
<!--결과 사진-->
![](/posts/posts_images/aiweb_day19/todo_styled_components.png)

<br><br><br>

### 스타일 커스터마이징 III - My Custom Style
<br>

styled-components 라이브러리를 통해 커스터마이징을 해 보겠습니다.
즉,`styledComponents.js` 파일 안에서 이미 정의된 컴포넌츠의 CSS 코드를 수정하여 저만의 디자인을 적용해 보겠습니다.

#### Glassmorphism

우선, 제가 적용하고 싶은 디자인 컨셉은 Glassmorphism입니다.
감상적인 배경사진 위에 어떤 텍스트나 객체 등이 유리처럼 보이는 특징을 가지고 있는 디자인 컨셉입니다.

Glassmorphism 효과를 내기 위해 배경의 투명도를 조절하고 blur를 조금 넣습니다.

이 프로젝트에서 텍스박스에다 Glassmorphism을 적용해 보겠습니다.
이를 위해 배경사진을 고려하고 다음 specifications를 CSS로 설정했습니다.

background: white or black (35% opacity)
background blur: 15px
border: 1.5px white (25% opacity);
shadow: 0px offset at x, 0px offset at y, 10px blur, 1px spread (black, 25% opacity)

<!--Show styledComponents code-->

```css
  background-color: rgba(0, 0, 0, 0.35);
  border: 1.5px solid rgba(255, 255, 255, 0.25);
  box-shadow: 0px 0px 10px 1px rgba(0, 0, 0, 0.25);
  backdrop-filter: blur(15px);
```

그 다음, 배경 사진을 아래와 같이 웹페이지에 직접 첨부했습니다.

```css
html{
  background-image: url('image_url');
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
}
```

`background-repeat: no-repeat;` -- ensures that background image does not repeat
`background-size: cover;` -- ensures that background image covers entire page
`background-attachment: fixed` -- ensures that background image always covers page

나머지는 보이는 assets들의 조화를 고려하면서 padding, margin, font, font-size, font-weight 등을 수정했습니다.

<br><br><br>

#### Tailwind CSS

Tailwind를 React와 함께 사용하는 연습으로 이 프로젝트에서 Tailwind의 Heroicon 컴포넌츠 라이브러리를 사용하고자 합니다.
해당 라이브러리를 사용하지 전에 CRA를 통해 먼저 Tailwind를 설치했습니다.

```
npm install -D tailwindcss
```

그 다음, Tailwind의 config 파인 `tailwind.config.js`를 생성하기 위해 다음 명령어를 실행했습니다.

```
npx tailwindcss init
```

```jsx
// tailwind.config.js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

config 파일을 생성한 후, React 프로젝트 폴더 안에 있는 모든 템플릿 파일을 아래와 같이 참고하도록 했습니다.

```jsx
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

마지막으로, `index.css` 파일 안에서 Tailwind의 directive 파일들을 참고하도록 아래 내용을 추가했습니다.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

이대로 React 또는 CRA 환경에서 Tailwind 셋업이 끝났습니다.

#### Tailwind를 통해 추가 또는 변경한 것들
- '추가' 버튼 대신에 Heroicon 아이콘 라이브러리에 포함된 arrow-right 아이콘을 사용했다
- Tailwind에서 주워진 accent 스타일을 적용한 checkbox을 만들었다

### 추가 기능 및 다른 이슈

1. Empty TODO -- 할일 목록에 빈칸을 넣는 것을 예방하도록 `handleSubmit` 함수 안에서 조건문을 추가

입력 상자에 내용이 없거나 공백만 넣은 상태로 버튼을 누르면 alert 메세지가 나타나게 만들었습니다.

```jsx
if(todoText.trim() === '') {
  alert('Write something. Don\'t be lazy.');
  return;
}
```
2. SubmitInput을 button으로 변경
3. Heroicon을 submit 버튼 중간에 포지션을 잡기 위한 과정
  - Heroicon svg를 submit 버튼 범위 안에 넣었다
  - 텍스트 입력 상자와 submit 버튼을 `TextInputWrapper`안에 모아서 wrapping을 했다
    - `TextInputWrapper` -- `display: flex; align-items: center;`
    - `SubmitInput` -- `display: flex; align-items: center; justify-items: center`
4. '/'를 누르면 입력 상자를 자동으로 선택 또는 focus하기

이 기능을 추가하기 위해 `useRef`를 사용했습니다.

```jsx
// Import to document
import React, { useState, useEffect, useRef } from 'react';
```

```jsx
// Add constant for key input reference
const inputRef = useRef(null);
```

```jsx
// Trigger focus upon key press
useEffect(() => {
  const handleKeyPress = (event) => {
    if (event.key === '/') {
      event.preventDefault();
      inputRef.current.focus();
    }
  };

  document.addEventListener('keydown', handleKeyPress);

  return () => {
    document.removeEventListener('keydown', handleKeyPress);
  };
}, []);
```

```jsx
<TextInput
  type='text'
  placeholder='Create TODO  . . .'
  name='todo'
  ref={inputRef} // Attach reference to text input box element
/>
```

5. CheckBox 기능 추가

체크박스를 누르면 todo를 완료 표시하는 기능을 추가했습니다.

- Checkbox를 클릭할 경우 : 체크박스가 checked인 상태가 되고 TodoText도 line-through 데코레이션이 적용된다
- TODO 텍스트 클릭할 경우 : TodoText에 line-through 데코레이션이 적용되고 체크박스도 checked인 상태로 변경된다


```jsx
// useState를 사용
const [checkedItems, setCheckedItems] = useState({});
```

```jsx
// handleSubmit 코드 수정
  const handleSubmit = (todoText) => {

    //...

    setTodo([
      //...
    ])
    setCheckedItems((prevCheckedItems) => ({
      ...prevCheckedItems,
      [todoId]: false
    }));
    
    //setTodoId(todoId + 1) ...
  }
```

```jsx
// handleToggle 코드 수정
  const handleToggle = (todoId) => {

    //...

    setCheckedItems((prevCheckedItems) => ({
      ...prevCheckedItems,
      [todoId]: !prevCheckedItems[todoId]
    }));
  }
```

```jsx
// checkbox toggle handler 함수 추가
  const handleCheckboxToggle = (todoId) => {
    setTodo((prevTodo) =>
      prevTodo.map((item) =>
        item.todoId === todoId
          ? { ...item, todoDone: !item.todoDone }
          : item
      )
    );
    setCheckedItems((prevCheckedItems) => ({
      ...prevCheckedItems,
      [todoId]: !prevCheckedItems[todoId]
    }));
  };
```

```jsx
// checkbox 요소에 id reference 추가하고
// state를 확인하기 위해 onChange() 함수 사용
<input type="checkbox" id={`checkbox-${item.todoId}`} className="accent-slate-600/25 w-4 h-4 ml-0 mr-5 px-0 hover:accent-slate-400" checked={checkedItems[item.todoId]} onChange={() => handleCheckboxToggle(item.todoId)} />
```

<br><br><br>

### 프로젝트 배포
<br>

#### CRA build folder

우선, 인터넷에 배포하기 위해 React에서 build 폴더를 먼저 생성해야 합니다.
build 폴더는 앱을 웹에서 실행하기 위한 production build의 데이터 및 파일들을 포함한 폴더입니다. 즉, 인터넷 또는 서버에 제공할 파일들은 원본 파일들이 아닌 프로덕션 빌드 폴더 안에 있는 파일들입니다.

CRA(Create React App)툴에서 build 폴더를 생성하는 기능이 이미 포함되어 있으니 배포하고자 하는 react 앱의 디렉토리 안에서 다음 명령어를 실행하면 해당 앱의 build 폴더가 생성됩니다.

```
npm run build
```

콘솔 창에서 위 명령어를 실행한 뒤 다음과 같이 "Compiled Successfully"라는 텍스트와 함께 서버에 serving하기 위한 명령어 등 안내하는 내용도 함께 나타납니다. 이 내용이 나타나면 같은 폴더 안에 build 폴더가 생성된 것을 확인할 수 있습니다.

<br>

#### Web Hosting

그 다음, build 폴더가 생성한 뒤 React에서 static 서버를 운영하고 알려주는 방식대로 서버에 배포할 수 있는 방법도 있지만, 이 프로젝트에서 Web Hosting(웹호스팅) 서비스를 활용하여 웹앱을 인터넷에 배포하겠습니다.

<b>Web Hosting</b>이란 웹 상의 메모리 공간을 임대해주는 서비스입니다.

웹앱이나 웹사이트를 인터넷에 배포하는 과정을 쉽게 해주는 서비스이지만,
매번 코드에서 수정사항이 있으면 다시 올려야 하는 번거러움이 있습니다.

<b>Netlify</b>를 통해 미니 프로젝트를 배포해 보겠습니다.

화원가입을 하고 로그인을 한 뒤, Sites라는 메뉴로 들어갔습니다.

Sites는 자기 파일들을 업로드하여 배포하는 공간입니다. GitHub 레포지터리를 선택하여 업로드할 수 있고, 또한 build 폴더를 업로드하여 배포할 수 있습니다. 이 프로젝트에서 build 폴더를 직접 업로드하여 배포하기 위 아래 절차를 따랐습니다.

<br>

먼저, 밑에 네모칸 부분이 있는데 여기에 build 폴더를 드래그해서 올렸습니다.

<!--Sites 화면 사진-->
![](/posts/posts_images/aiweb_day19/netlify_sites.png)

그 다음, build 폴더를 드래그하여 네모칸에 넣었습니다. 이후 업로드가 시작되며 "Uploading..." 문구가 뜨고 기다렸습니다.

<!--Uploading... 사진-->
![](/posts/posts_images/aiweb_day19/netlify_uploading.png)

마지막으로, 업로드하고 배포가 마치면 다음과 같이 "Deploy success!" 화면이 나타납니다.

<!--Deployment 사진-->
![](/posts/posts_images/aiweb_day19/netlify_deployed.png)


<br><br><br>

### NOTE. React App 수정서항

웹사이트를 수정할 때마다 build 폴더를 다시 만들어 Netlify에 배포한 웹앱을 업데이트하기 위해 build 폴더를 다시 업로드합니다.

업로드하는 방식은 배포할 때와 똑같습니다. Netlify 홈페이지에서 Deploys > Sites 안에서 다시 드래그하여 웹 앱을 업데이트할 수 있습니다.

![](/posts/posts_images/aiweb_day19/netlify_reupload.png)

<br><br><br>


## CRA 미니 프로젝트 결과 : 할일 목록 만들기
---
<br>

### OUTPUT

![](/posts/posts_images/aiweb_day19/output.png)

<img src="/posts/posts_images/aiweb_day19/todoapp_output.gif">


### Netlify 링크

https://nipa-frontend-todo-4-eunice.netlify.app/

### SOURCE

(Initial)
https://github.com/ganyunhee/ai_webdev/tree/main/react/0810_react_todoapp/todo-app

(Custom)
https://github.com/ganyunhee/react_todoapp_custom

<br><br><br>

## TO IMPROVE
---
<br>

- TODO 내용을 편집할 수 있는 기능을 추가할 것
- 각 TODO entry를 따로 표시하는 것보다 하나의 container 안에 모든 TODO를 모으는 형식을 해볼 것
  - TODO가 추가될 때마다 container가 늘린다, List 형식처럼
- React Hook 복습하고 계속 실습할 것

<br><br><br>

## REFERENCES
---
<br>

- Using the Effect Hook.
https://legacy.reactjs.org/docs/hooks-effect.html
- Built-in React Hooks.
https://react.dev/reference/react
- Create React App: Deployment.
https://create-react-app.dev/docs/deployment/
- Install Tailwind CSS with Create React App.
https://tailwindcss.com/docs/guides/create-react-app
- Tailwind CSS - Configuration.
https://tailwindcss.com/docs/configuration
- Tailwind Heroicons
https://heroicons.com/
- Glassmorphism의 모든 것.
https://ldrerin.tistory.com/479
- How to implement glassmorphism with CSS.
https://blog.logrocket.com/implement-glassmorphism-css/

<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프