---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 3&4"
date: 2023-07-21
descripton: "Day 3&4 in AI+웹개발 취업캠프"
tags:
    - diary
---

# 학습내용 정리
<br>

## Day 3
---

### 색깔의 표현

- RGB (r, g, b)
    - red, green, blue 값으로 색깔을 표현할 수 있다
- RGBA (r, g, b, a)
    - red, green, blue, alpha
    - alpha는 opacity(투명도)를 표현한다
- HEX (#FFFFFF)
    - hexadecimal(16진수)로 표기한다
    - 0~9 -> A~F 범위 -- 0(Black), F(White)
    - 0에 가까울수록 해당 색깔이 <b>어두워짐</b>, F에 가까울 수록 해당 색깔이 <b>밝아짐</b>
        
        - 예) HEX to RGB 표현
            > #FF0000 --> rgb(255, 0, 0)
            <br>
            > #00FF00 --> rgb(0, 255, 0)
            <br>
            > #0000FF --> rgb(0, 0, 255)

참고. https://blog.naver.com/PostView.naver?blogId=kobawoo9&logNo=221887937211

<br>

### 속성 우선순위
- `<style>`에 있는 내용보다 inline style 우선순위

    ```
    <style>
        ul {
            list-style : none;
        }
    </style>
    ```

    위 코드처럼 `<style>` 태그 안에 있는 내용보다는
    아래 코드 처럼 `inline` 또는 해당 태그 안에서 정의한 CSS style 정보가 우선순위가 더 높아 먼저 적용한다.

    ```
    <ul style="list-style: circle;">
    ```

<br>

### `<table>` 구현 방식

- columns, rows 형식으로 데이터를 표현

`<th>` == "table heading"

- row heading / 제목

`<tr>` == "table row"

- 해당 제목의 항목

`<td>` == "table data"

- 해당 제목의 항목 개수만큼 데이터 추가

Code Sample

```
<body>
    <table style="width:100%">
        <tr style="background-color:lightgrey">
            <th>가격</th>
            <th>이름</th>
            <th>시총</th>
        </tr>
        <tr>
            <td>71,000</td>
            <td>삼전</td>
            <td>600조</td>
        </tr>
        <tr>
            <td>오징어</td>
            <td>고등어</td>
        </tr>
    </table>
</body>
```

**설명**

> 1행(tr[0]) : 제목(th 모음)
<br>
> 2행(tr[1]): 데이터(td 모음)
<br>
> ...
<br>
> n행(tr[n]): 데이터(td 모음)
<br>

테이블로 한 화면을 표현하는 경우?
e.g. investing.com 주식 데이터 시각화

NOTE. 테이블을 만들기 전 어떤 데이터들을 key, 속성으로 잡을지 정할 것!

<br>

## HTML Form 요소
- 다양한 타임의 input 요소를 사용하여 사용자로부터 입력받을 수 있다
- HTML에거 사용할 수 있는 대표적인 input 요소의 타입
- 사용자 데이터 입력받을 수 있게 형식을 만

### `<form>`

```
<form action="page_address" method="get|post"></form>
```

데이터를 입력해서 어디론가 보낼 때 사용하는 형식
e.g. Login Form

데이터 입력 방식 : get
데이터 전송 방식 : post (encoding 방식)


1. Text(Textbox)
2. Password
3. Radio
4. Checkbox
	여러 개 옵션 선택할 수 있도록 사용하는 요소
5. File
	파일 첨부/입력으로 받을 수 있도록 사용하는 요소
6. Select
7. Textarea
8. Button
9. Submit
10. Fieldset

```
<form action="form.js", method="get", onsubmit="submitForm(event)">
    <label>사용자: </label><input type="text" name="username"><br>
    <label>비밀번호: </label><input type="password" name="password">
```

데이터를 form.js로 보냄
get 방식으로

`name` : 해당 데이터 이름

submit 누르게 되면 데이터를 하나의 폼으로 발송

<br>

## Internal Stylesheet vs. External Stylesheet

![](/posts/posts_images/aiweb_day3_4/css_stylesheet.png)


## 강사 Daily 인사이트

#### ID 선택자 왠만하면 쓰지 않을 것! Class 사용!
- Class 분류 잘해야 함
#### class명 notation (convention)
- 의미 있는 이름 : 들어 있을 내용 예상할 수 있게 (e.g. main, container, etc.)
- camelCase X --> underscore 사용!

<br>

## Day 4
---
<br>

### CSS class selector(선택자)
- 특정 집단(class)의 여러 요소를 한 번에 선택할 때 사용한다.
- 동일한 class 이름을 가지는 요소들을 모두 선택해준다.

<br>

### CSS Text 속성

- 속성 리스트
    - color
    - direction
    - letter-spacing
    - word-spacing
    - text-indent
    - text-align
    - text-decoration
    - text-transform
    - line-height
    - text-shadow
    - unicode-bidi
    - vertical-align
    - white-space

참고. codingfactory.net/10648

<br>

## CSS Link

- visited
- hover
- focus

<br>

## CSS 크기 단위 (Units)

> %, em, px, cm, mm, inch ...

- 백분율 단위 - %
    - 기본 크기 : 100%
    - 이에 대한 상대적인 크기를 설정한다
- 배수 단위 - em
    - 해당 font의 기본 크기 : 1em
    - 이에 대한 상대적인 크기를 설정한다
- Pixel 단위 - px
- Viewport Width, Viewport Height - vw, vh
	- 보이는 높이, 보이는 너비를 100%로 두고 값을 지정한다
    - text보다 box model에 사용한다


<br>

### 외부 링크에서 font 첨부 방법
- `<link>` 태그 안에 링크 첨부
- 폰트 사이트 안내에 따라 주어진 Font API 활용

### Font 변경 방법

- Example 1) serif, sansserif
```
    .serif {
        font-family: "Times New Roman", Times, serif;
    }

    .sansserif {
        font-family: Arial, Helvetica, sans-serif;
    }
```

- Example 2) 나눔고딕
```
    .nanum-godic {
        font-family: 'NanumBarunGothic';
        font-weight: normal;
        font-style: normal;
    }
```

#### 한국어 무료 폰트 사이트
- Google Fonts - https://fonts.google.com
- 네이버 폰트 - https://hangeul.naver.com/font/nanum, https://clova.ai/handwriting/list.html
- 눈누 - https://noonnu.cc/
- 공유마당 - https://gongu.copyright.or.kr/gongu/bbs/B0000018/list.do?menuNo=200195#none
- 우아한형제들(배달의만족) - https://www.woowahan.com/fonts
- 카페24 - http://www.fonts.cafe24.com
- 한글마을 - https://www.koreafont.com
- asiafont(font 통합패키지) - https://www.asiafont.com

참고. https://www.elancer.co.kr/blog/view?seq=82

<br>

### CSS box model

Box Model 개념
- 모든 HTML 요소는 box 모양으로 구성됨
- 이것을 box model이라고 부름

Box Model 요소
- `content`
	- text, image 들어 있는 box의 실질적인 내용 부분
- `padding`
	- 내용과 테두리 사이의 간격
	- 눈에 보이지 않음
- `border`
	- 내용과 패딩 주변을 감싸는 테두리
- `margin`
	- 테두리와 이웃하는 요소 사이의 간격
	- 눈에 보이지 않음

<br>

### HTML block, inline 개념

```
display: block;
display: inline;
display: inline-block;
...
```

- display
    - HTML의 모든 요소는 각각의 기본 display 속성값을 가지고 있다
    - block
        - 언제나 새로운 line에서 시작한다
        - 해당 line의 모두 너비를 차지한다
    - inline
        - 새로운 line에서 시작하지 않는다
        - 요소의 너비도 해당 line 전체가 아닌 해당 HTML 요소의 내용만큼 차지한다

    - inline-block
        - 해당 요소 자체는 inline 요소처럼 동작한다
        - 해당 요소 내부에서는 block 요소처럼 동작한다
        - inline 요소와 비슷하지만 너비와 높이를 설정할 수 있다
        - block 요소처럼 margin을 이용하여 여백을 지정할 수 있다

<br>

## display: none; display: hidden

- 사용자에게 보이는 내용 숨기기/보여주기 설정

```
p.none { display: none; }
p.hidden { display: hidden; }
```

<br>

## position 지정 방식

```
div {
	position: relative;
}

div {
	position: static;
}
```

#### Relative position
- 다른 원소 위치에 따라 움직일 수 있으면 움직임

#### Static position
- 해당 위치에 고정하도록 함
- default(기본값)으로 지정됨

#### Absolute position
- relative처럼 이동
- 상위 부모 tag 안에 있으면 같이 움직이도록
  (상위 부모 뭐 있는지 확인하고 사용)

<br>

## CSS selector

#### 자손 선택자 decendant(parent) selector
- 해당 요소 하위 요소 중에서 특정 타입의 요소를 모두 선택

```
div p {
	...
}
```


#### 자식 선택자 child selector
- 해당 요소 ***바로 밑***에 존재하는 요소 중에서 특정 타입의 요소를  모두 선택

```
div > p {
	...
}
```

#### 사용 예시

```
form > input {...}
form > input:checked {...}
```

<br>

## CSS Pseudo-class

> dynamic-pseudo class (동적 의사 클래스)
- describes a certain action done to an element
	- link *
	- visited
	- hover
	- active
	- focus
> UI element states pseudo-class (상태 의사 클래스)
- describes state of an element
	- checked
	- enabled
	- disabled
> structural-pseudo class (구조 의사 클래스)
- first-child : parent tag 하위에 있는 첫번째 tag/자식
- nth-child
- first-of-type
- nth-of-type : 몇변째 있는 자식이냐

#### 사용 예시

- 어떤 원소의 자식 select

```
<body>
    <div class="first">
        <p>first의 child (1)</p>
        <p>first의 child (2)</p>
        <div class="second">
            <p>second의 child (1)</p>
            <p>second의 child (2)</p>
        </div>
    </div>
</body>
```

```
div.first {...}
div.second{...}
```


<br>

# 과제>Main Page 만들기

Source. https://github.com/ganyunhee/ai_webdev/tree/main/html_css/stylized

## Part I (Day 3)
---
<br>

## Google Fonts 링크 첨부

- Day 2(Legacy File)에서 추가한 Font 첨부 방법 설명
- Google Fonts > Font 선택 > Font 추가 기능 사용

Code Sample
- Google Fonts API Link 첨부, Font Library 첨부
- 사용한 Font : Montserrat, Victor Mono
```
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR&family=Victor+Mono&display=swap">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Montserrat:wght@400;700;800&display=swap">
```

<br>

## 템플릿 Cleanup, 이미지 첨부

- Navigation Menu Overflow 이슈 해결
    - font-size 및 padding 조절
- 웹사이트 구성에 사용한 Border 숨기기
    - comment out border CSS
- Section에 image 추가

```
<img src = "link_to_image">
```

<img src="/posts/posts_images/aiweb_day3_4/main_home.png" style="box-shadow: 4px 4px 20px rgb(252, 252, 252, 0.3)">

<br>

## Part II (Day 4) 
---
<br>

## Navigation Menu 각 Entry에 Link 추가

- `HOME` : 홈페이지로 돌아가기
- `BLOG` : 블로그 페이지로 가기 (todo)
- `WORKS` : 프로젝트 목록 페이지로 가기 (todo)
- `SOURCE` : GitHub 프로필로 가기
- `NEWSLETTER` : Newsletter 구독 페이지로 가기

## Blog 페이지 만들기

- NOTE. Blog 페이지 완성되면 Hugo Template 사용하여 만든 개인 블로그 대체할 것
    - 이유. Hugo 사용하기에는 디자인 리소스 파일 만들 때 이슈가 많이 발생함 (e.g. 웹페이지 깨짐, 404 Not Found 에러)
        - 여러 이슈가 발생하는 이유는 Hugo Template 만든 분의 resource generator 문제인지, GitHub Pages의 문제인지 현재 정확히 알아볼 수 없음. (계속 기록하고 업데이트 예정)
        - 이슈를 해결해도 안심이 안 되고 하나하나 해결하기에는 시간이 많이 걸리기 때문에 더 안전한 사이트 스스로 만들 예정.

<img src="/posts/posts_images/aiweb_day3_4/main_blog.png" style="box-shadow: 4px 4px 20px rgb(252, 252, 252, 0.3)">


## Newsletter form 만들기

<img src="/posts/posts_images/aiweb_day3_4/main_newsletter.png" style="box-shadow: 4px 4px 20px rgb(252, 252, 252, 0.3)">

## Button에 Hover Effect 추가

- #### Newsletter form 안에 'Submit' 버튼 위에 커서를 맴돌면 버튼의 background 색깔과 font 색깔이 변경된다.

<img src="/posts/posts_images/aiweb_day3_4/main_newsletter_buttoneffect.png" style="box-shadow: 4px 4px 20px rgb(252, 252, 252, 0.3)">

<br>


# TODO
    - `CSS 선택자, pseudo-class 사용 연습`
    - `CSS 포지션(static, relative, absolute) 지정방식 사용 연습`
    - `CSS Positioning (flexbox, align-items, justify-content) 연습`
    - `CSS 크기 단위(vh, vw, em, rem 등) 차이 분석`

<br>

# NEXT WEEK : JavaScript


<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프 