---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 2"
date: 2023-07-19
descripton: "Day 2 in AI+웹개발 취업캠프"
tags:
    - diary
---

<br>

# 자기소개 피드백 + Daily 인사이트

### "IT 기술의 한계"
IT : 알면 알고, 모르면 모름.
다 될 것 같지만 못하는 것도 있다. (한계가 있음)
어떤 것을 만들 수 있는지, 못 만드는지 스스로 알고 판단해야 한다.

### "지금은 많이 요구하는 시대"
요즘 역량을 보고 뽑는 회사가 많아졌다.
남들과 다른 차별점을 가지고 있어야 한다.

### "모르면 모르고, 알면 왜 이걸 알아야 돼 (어떻게 알고 있고 어떻게 적용하지?)"
자기계발 및 기초다지기에는 지식을 아냐 모르냐 구별할 수 있는 실력이 있어야 한다.

### "목표지향적이어야 한다"
목표를 정하고, 그 목표를 이루고 싶은 이유를 생각하며 필요한 것들에 대한 경계(boundary)를 세워야 한다.

### "현실적인 문제만 다룰 것!"
"입사해서 알려준 사람 없다"
"누군가 잡아가는 책임이 없다"
"나랑 내 동료가 같이 잡아 나가야 된다"

배워서 들어간다
"우리가 가르쳐주는데 너가 왜 돈을 받아?"
일할 줄 알아야 함!
아무도 대신해 주지않음. 아무도 일을 시키지 않음 (미리 일을 시키는 회사가 좋음).

### "Deep Learning 쓰는 이유"

너무 복잡하고 큰 데이터 / 다른 데이터와 연결거리 전혀 못 찾으면 Deep Learning 사용
--> 이만큼 복잡한 데이터를 가지고 있는 회사 별로 없음 -- 비정형 회사
내가 뭘 하고 싶은 서비스를 구체적으로 생각해야 함

<br>

# HTML & CSS
<br>

## HTML (Hypertext Markup Language)
![](/posts/posts_images/aiweb_day2/html_open_close_tags.png)

Hypertext == Text
open tag : HTML element의 시작점
closing tag : HTML element의 끝점

## Markup Language
- markup된 언어 (markup: 문서를 작성하는 데 필요한 format)
- 특성 : 규칙을 설명하는 언어
- e.g. XML, XHTML

## CSS (Cascading Style Sheet)
CSS == stylesheet

## HTML Element
![](/posts/posts_images/aiweb_day2/html_element.png)

## HTML 문서구조

```html
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>HTML Intro</title>
</head>

<body>
	<h1>여러분을 환영합니다!</h1>
</body>

</html>
```

`<!DOCTYPE html>`
- 현재 문서가 html5라고 표시
- 예전에 HTML1~4와 HTML5와 구별 (요즘은 HTML5로 표준화)
- 브러우저가 문서를 HTML5라고 인식할 수 있게 만드는 tag
- 요즘 안 써도 되지만 --> 규칙!

`<html lang="ko">`
- 언어마다 컴퓨터가 언어를 인식하는 방식이 다름
- 요즘 unicode로 통일 표현

`<head>`
- html 문서의 metadata / meta information (포함된 정보)를 포함 
	- metadata == 데이터의 데이터 (데이터 자체를 설명할 수 있는 data)
	- 내 정의 : 데이터의 속성들을 표시하는 세부적인 정보

`<meta>, <title>`
- 안 써도 html 읽을 수 있지만, 규칙으로 써야 함 (for indication and readability)

<br>

# 실습

github repo clone하기 (Git BASH 사용) > VS Code에서 intro.html 열기

```
git clone https://github.com/Seoul-ICT/Seoul-ICT-Web-Base
```

![](/posts/posts_images/aiweb_day2/prac1.png)


- intro_2.html 생성

![](/posts/posts_images/aiweb_day2/prac2.png)

- intro_2.html 드래그해서 브러우저에 드랍 (html 여는 방식 중 하나)
  OR VS Code 파일 탐색기에서 드래그하고 브라우저에 드랍
  (issue. VS Code에서 브로우저 중간 공간에 드랍하면 about:blank#blocked 페이지 나왔는데 타이틀바/메뉴바 공간에 드랍해보니 정상으로 페이지 나왔음)

![](/posts/posts_images/aiweb_day2/prac3.png)

- intro_2.html 내용 확인

![](/posts/posts_images/aiweb_day2/prac4.png)

- 주석 -- 메모 쓰기 위한 기능
  `<!-- 내용 -->` 이런 식으로 주석 달기
  note. 언어마다 주석 달기 처리가 다름

![](/posts/posts_images/aiweb_day2/prac5.png)

![](/posts/posts_images/aiweb_day2/prac6.png)

![](/posts/posts_images/aiweb_day2/prac7.png)

![](/posts/posts_images/aiweb_day2/prac8.png)


`<p>`가 같은 줄에 표시하는 이유?
- `<p>` tag은 문단을 구별하지 않음
- `<br>` tag 등을 통해 문단을 표현해야 줄바꿈 가능


## TEST - 이상한 짓

`<p>` tag 없이도 텍스트 나오네?
![](/posts/posts_images/aiweb_day2/prac9.png)

개발자 도구 열기

![](/posts/posts_images/aiweb_day2/prac10.png)

소스 볼 수 있고, 페이지 안에 있는 이미지, 파일 등을 다운받을 수 있음
Web : 누구나 접속할 수 있음 --> 데이터 숨길 수 없음
개발자가 데이터 숨기는 방식 : 암호화/난독(조금 변형시켜서 보내기), HTTP 쪽에서 blocking



Formatting
- 글의 format / 글꼴 변경

![](/posts/posts_images/aiweb_day2/prac11.png)
![](/posts/posts_images/aiweb_day2/prac12.png)

`<b>`와 `<strong>` tag 차이
- `<b>` : Bold Text
- `<span>` : Important Text
screen reader에서 강조하느냐 안하느냐의 차이


`<span>` 등
HTML tag 다양하게 학습할 것!

![](/posts/posts_images/aiweb_day2/prac13.png)

w3schools.com/html/html_formatting.asp

## HTML Layout

`<body>` tag안의 내용 - basic layout i.e. ***Legacy*

## Legacy

![](/posts/posts_images/aiweb_day2/legacy.png)

`header`
- 웹사이트 logo, 메뉴, 오른쪽에 profile

`nav`
- navigation - 웹사이트 탐색 메뉴

`main`
- 무슨 서비스 제공할 건지 (e.g. article, etc.)

`footer`
- 회사 관련된 정보
- portfolio : 개인정보 처리 방식, 기본 운영규칙,  socials, etc.
- 서비스와 관련되지 않은 정보

기타 (Bootstrap library tags, etc.)
- `<textarea>` : 텍스트가 표시되는 공간
- `<div>` :  의미의 시작점과 끝나는 점 알려주는 tag
...

<br>

# 과제 > HTML Legacy Template

목적. Main Page 레이아웃 템플릿 구성해보기!

#### Wireframe
---
![](/posts/posts_images/aiweb_day2/Wireframe%20-%20Legacy%20Layout.png)

#### Color & Font
---
![](/posts/posts_images/aiweb_day2/Desktop%20-%201.png)

#### Output
---
![](/posts/posts_images/aiweb_day2/legacy_output.png)


### Source Code
---

https://github.com/ganyunhee/ai_webdev/tree/main/html_css/legacy

<br>

# Misc

### Issue

`Refused to apply style from 'http://127.0.0.1:5500/html/legacy.css' because its MIME type ('text/html') is not a supported stylesheet MIME type, and strict MIME checking is enabled.`

- 해결 : legacy.css 파일을 html 파일과 같은 폴더로 이동

### Terminology

SEO(Search Engine Optimization)
- public하게 open되는 웹 브라우저

### 사용한 Google Fonts

- https://fonts.google.com/specimen/Victor+Mono
- https://fonts.google.com/noto/specimen/Noto+Sans+KR
- https://fonts.google.com/specimen/Montserrat


<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프 