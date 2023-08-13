---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Udemy - React [PART I]"
date: 2023-08-13
descripton: "A journal on the 한입 크기로 잘라 먹는 리액트(React.js) Udemy Class. This entry is for Week 4 (PART I)."
tags:
    - diary
---

<br><br>

---
# CONTENTS SUMMARY
- [INTRODUCTION](#introduction)
- [Wny React?](#why-react)
- [INFOGRAPHICS](#infographics)
- [REFERENCES](#references)
---

<br><br><br>

## INTRODUCTION
---
<br>

4주차부터 프론트엔드 과정이 시작되오니 React를 배우기 시작했습니다.
하지만 React를 활용하기 위해 JavaScript를 먼저 이해하면 좋으니 JavsScript 입문부터 다시 복습하고 있습니다.
다행히도 이번 유데미 강의에서 React를 학습하기 위한 JavaScript 내용이 포함되어 있으니 이번주는 JavaScript 다시 배우고 실습했습니다.

시간이 압박하니 변수와 상수 또는 자료형, 연산자 등 이미 많이 배워본 기본적인 내용을 조금만 실습했습니다. 그 다음, JavaScript 응용과 관련된 내응에 더욱 집중하여 많이 다루지 못했던 개념들을 파악하려고 노력했습니다. 특히나 최근 3~4주차에서 Node JS와 React JS 강의들을 들으면서 많이 사용하게 사용하게 된 spread 연산자, Promise, async/await, 그리고 API 호출 등을 사용하기에 좀 더 적응할 필요가 있으니 계속 복습하고 작은 프로그램들을 만들 예정입니다.

일단 이번 주의 목표는 React JS를 조금씩 다루면서 미니 프로젝트를 만들고, Vanilla JS를 통해 웹앱을 만드는 과정과 비교하여 React가 왜 필요한지또는 웹 개발에서 어떻게 활용되는지 분석하는 것입니다.

<br><br><br>

## Why React?
---
<br>

### Initial Concept

React는 다양한 페이지에서 공통적으로 사용될 것으로 예상되는 요소들을 가지고 각자 파일 또는 모듈을 제작해 놓고 필요에 따라 페이지에 컴포넌트를 가져오는 방식을 통해 똑같은 코드 작업을 반복하는 것의 필요성을 없앱니다. 따라서 코드를 재사용할 수 있으니 코드량도 줄이고 개발도 편리하게 해줄 수 있습니다. 특히 React는 Component 기반의 UI 라이브러리이므로 HTML 요소들을 모두 component로 만들어 재사용할 수 있도록 해주니 웹 개발에 사용하기가 편리합니다.

![](/posts/posts_images/udemy_req_react/why_react.png)


### Virtual DOM

우선, DOM(Document Object Model)은 브라우저가 HTML 문서 등을 해석하여 내요을 이해할 수 있도록 사용하는 객체 Tree 모델이라고 합니다. 하나의 HTML 문서를 읽고 화면에 나타낼 수 있도록 DOM을 계속 업데이트하면서 화면을 나타냅니다.

![](/posts/posts_images/udemy_req_react/dom.png)

변경사항이 있을 때마다 DOM을 업데이트하고 다시 렌더링하고 화면에 결과를 표시하는데, 작은 변화에도 계산량이 증가되니 비효율적입니다. 

하지만 React에서는 매번 계산하고 처리해야 하는 번거러움을 줄이기 위해 Virtual DOM 즉 가상의 DOM을 활용하고 있습니다. Virtual DOM을 통해 수정사항이 있을 때마다 매번 통째로 처리하고 화면에 나타내는 대신 변경사항이 생길 때 가상의 DOM을 만들고 그 DOM안에서 정보를 업데이트하고 모두 처리한 후 하나의 결과물로 합쳐서 화면에 나타내주는 기술입니다. state가 변경된 것을 인식하고, 원래 코드와 비교한 후 rendering을 다시 해주는 방식입니다. 즉, React는 Virtual DOM이라는 기술을 통해 처리 속도가 빨라지며 앱이나 프로그램의 성능을 향상시킬 수 있습니다.

![](/posts/posts_images/udemy_req_react/virtual_dom.png)


<br><br><br>

## INFOGRAPHICS
---
<br>

### Benefits Overview of React
![](/posts/posts_images/udemy_req_react/ReactJS-Framework-Benefits.png)

### Key Benefits or Advantages of Using React
![](/posts/posts_images/udemy_req_react/Key-benefits-of-ReactJS.png)

ref. Top 10 ReactJS Benefits For Your Web Project.


## CONCLUSION
---
<br>

요약을 해보면 디버깅의 또한 여러 라이브러리의 통합한 환경을 제공할 수 있음으로 프론트엔드 개발의 편리성을 높이는 도구로 사용되는 것이라고 배웠습니다. JavaScript를 기반으로 만들어진 프레임워크이지만 React를 활용하기 위해 따로 learning curve가 있고 Node JS와 React에서 다루는 또 다양한 개념이 있으니 React 환경에서 웹 개발을 원활하게 하기 전까지는 앞으로 배울 것이 많이 남았습니다.

이후에는 Node JS의 모듈 시스템을 배운 다음 JSX syntax와 React의 State와 Props를 더 자세히 배울 예정입니다. 최근에 만들었던 미니 프로젝트들에서 React Hook들과 SPA(Single Page Application)을 다뤄서 조금 이해했지만 더욱 깊이 배워야 할 필요가 있는 것 같습니다. React 학습을 통해 더 다양한 프로젝트를 만드는 것이 기대됩니다.

<br><br><br>

## REFERENCES
---
<br>

- Why Use React.
https://www.tatvasoft.com/blog/why-use-react/
- Top 10 ReactJS Benefits For Your Web Project.
https://solguruz.com/blog/top-10-reactjs-benefits/

<br><br><br>

<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프