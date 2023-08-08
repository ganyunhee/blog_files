---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 16"
date: 2023-08-07
descripton: "Day 16 in AI+웹개발 취업캠프"
tags:
    - diary
---

# CONTENTS SUMMARY
---
<br>

- [학습 목표](#학습-목표)
- [REVIEW](#review)
- [실습 > Node JS를 통해 간단한 서버 만들기](#실습--node-js를-통해-간단한-서버-만들기)
- [과제 > addHTML.js 실행, clock.html 커스터마이징](#과제--addhtmljs-실행-clockhtml-커스터마이징)

<br><br><br>

# 학습 목표
---
<br>

React를 학습하기 전에 Node JS를 통해 프로그램레 기능을 추가하기 위한 모듈을 내보내고 가져오기 학습 및 실습한다.

<br><br><br>

# REVIEW
---
<br>

시작하기 전에 JavaScript의  가지 개념을 먼저 다시 살펴봤습니다. 객체와 배열에 대한 개념부터 시작하였고, map과 filter 함수의 차이 등을 복습했습니다. 그 다음 더 객체 리터럴, 구조 분해 할당, JSON(JavaScript Object Notation) 포맷 등 Node JS를 사용하기 위한 필수적인 개념에 대한 학습을 했습니다.

<br><br><br>

# 실습 > Node JS를 통해 간단한 서버 만들기
---
<br>

Node JS 환경에서 자바크스립트 문서를 작성하고 실행하는 연습을 했습니다.
그 다음, npm을 통해 JSON 파일을 생성하여 서버 프로그램과 함께 사용할 morgan 모듈을 내보내고 가져오는 연습을 했습니다.

<br>

## node-app-mod
> main.js, mod1.js, mod2.js 파일들 포함
<br>

여러 파일을 하나의 프로그램으로 구동 시키기 위해 모듈을 사용합니다.

<br>

## node-app-package
> package.json, addMorgan.js, addHTML.js, clock.HTML 파일 등 포함
<br>

app과 관련된 파일들을 이 폴더 안에 모으고, 아래 명령어를 실행하여 node 프로젝트를 초기화시킵니다.

```
npm init -y
```

실행 후 node 프로잭트를 운영하기 위해 사용될 JSON(package.json) 파일이 생성됩니다.
이 JSON파일 안에 있는 정보를 확인하고 필요에 따라 수정합니다.
e.g. author에다 본인 이름을 기입, MIT license 사용할 시 license에다 'MIT' 기입, 사용할 모듈들의 이름을 keywords 안에 기입 등

<br>

## 노드 서버 만들기

<br>

### 서버는 무엇인가?

서버는 데이터를 보내주는 역할을 합니다.
서비스를 제공하기 위한 주체이니 "server"라는 이름을 가지게 되었습니다.

노드 서버를 실행하기 위해 다음 명령을 실행했습니다.

```
node index.js
```

<br>

### JSON 파일 수정

author, license, module dependencies에 대한 정보를 수정했습니다.


<br><br><br>

# 과제 > addHTML.js 실행, clock.html 커스터마이징
---
<br>

## 1. addHTML.js 실행

```
node addHTML.js
```

위 명령어를 통해 addHTML.js를 실행해서 서버를 열고 브라우저 안에서 열었습니다.

하지만 clock.html에서 변경사항이 있을 때마다 매번 브라우저에서 웹페이지를 새로고침 해야 했었습니다.

매번 새로고침 하기가 번거롭다 보니 결국 clock.html을 VS code의 Live Server로 실행해보고 잘 작동하는 것을 확인하고 나서 계속 라이브로 보면서 작업했습니다.

<br><br><br>

## 2. clock.html 커스터마이징

JavaScript나 CSS 파일을 따로 HTML 문서와 함께 연동시키는 서버 기능을 아직 구현하지 못했기 때문에 커스터마이징은 HTML 문서의 `<style>`와 `<script>` 태그들 안에 있는 코드를 수정했습니다.

먼저 폰트와 색깔을 변경하고, light와 dark 테마를 추가했습니다.

<!--Insert font, theme colors-->

그리고 나서 날짜를 보기 편하게 영문식으로 표시하도록 변경했습니다.
저번에 일기예보 API를 구현했을 때처럼 `January, February, ...` 등 영문으로 번역된 월 이름들을 모아서 리스트를 만들고 `getMonth()` 함수가 return하는 숫자에 따라 해당 월의 이름을 표시하도록 했습니다. `date`도 ordinal number `1st, 2nd, 3rd, 4th, ..., 11th, 12t, 13th, ... , 21st, 22nd, 23rd`로 표시하도록 suffix(-st, -nd, -rd)를 넣었습니다.

그리고 테마를 변경할 수 있기 위해 스의치를 넣어봤습니다. UIverse라는 사이트에서 스위치 컴포넌츠를 가져와서 색깔 편집하고 웹페이지 위쪽에 오른쪽 정렬헤서 표시했습니다.

코드는 다음과 같이 완성되었습니다.

```html
  <div class="toggle-switch">
    <label class="switch-label">
      <input type="checkbox" class="checkbox">
      <span class="slider"></span>
    </label>
  </div>
  <div class="clock">
    <div id="today" class="today"></div>
    <div id="time" class="time"></div>
  </div>
```

```js
    const todayDiv = document.getElementById('today');
    const timeDiv = document.getElementById('time');

    // getTime 함수
    function getTime(){
      let now = new Date();
      let year = now.getFullYear();
      let month = now.getMonth() + 1;
      let date = now.getDate();
      let hour = now.getHours();
      let minute = now.getMinutes();
      let second = now.getSeconds();

      // month 리스트
      const months = [
        'January', 'February', 'March', 
        'April', 'May', 'June', 
        'July', 'August', 'September',
        'October', 'November', 'December'
      ]

      hour = hour < 10 ? `0${hour}` : hour;
      minute = minute < 10 ? `0${minute}` : minute;
      second = second < 10 ? `0${second}` : second;

      // day를 ordinal number로 표시 (suffix 넣기)
      date = date.toString();
      date_end_char = date.slice(-2);
      
      // if 1 or 11 : 1st, 11th
      if(date_end_char == '1') {
        date = `${date}st`;
        if (date_end_char == '11') {
          date = `${date}th`;
        }
      }
      
      // if 2 or 12 : 2nd, 12th
      if (date_end_char == '2') {
        date = `${date}nd`;
        if (date_end_char == '12') {
          date = `${date}th`;
        }
      }

      // if 3 or 13 : 3rd, 13th
      if (date_end_char == '3') {
        date = `${date}rd`;
        if (date_end_char == '12') {
          date = `${date}th`;
        }
      }

      else {
        date = `${date}th`
      }

      const amPm = hour >= 12 ? 'PM' : 'AM';

      todayDiv.textContent = `${months[month]} ${date}, ${year}`;
      timeDiv.textContent = `${hour}:${minute}:${second}\r${amPm}`;

      const toggleSwitch = document.querySelector('.checkbox');
      const clock = document.querySelector('.clock');

      function changeTheme() {
        const body = document.body;
        const backgroundColor = toggleSwitch.checked ? '#fdf6e3' : '#002b36';
        const borderColor = toggleSwitch.checked ? '10px solid #eee8d5' : '10px solid #073642';
        const shadowColor = toggleSwitch.checked ? '10px 10px 0px 0px #eee8d5' : '10px 10px 0px 0px #073642';
        const textColor = toggleSwitch.checked ? '#93a1a1' : '#586e75';
        body.style.backgroundColor = backgroundColor;
        clock.style.backgroundColor = backgroundColor;
        clock.style.boxShadow = shadowColor;
        clock.style.border = borderColor;
        clock.style.color = textColor;
      }

      toggleSwitch.addEventListener('change', () => {
        changeTheme();
      });

      changeTheme();
    }

    // setInterval 메소드
    getTime()
    setInterval(getTime, 1000);
```

<br>

## OUTPUT

source. https://github.com/ganyunhee/ai_webdev/blob/main/js_ts/0807_clock_js/clock_output.gif

<br><br><br>

## TO IMPROVE

`clock.html`에서 돌아가는 gif처럼 간단한 moving CSS 애니메이션이나 화면 배경에서 시간마다 바뀌는 영상들을 추가해서 좀 더 꾸미고 싶었지만 여러 일 때문에 시간이 부족하다 보니 나중에 여유로워지면 추가할 생각입니다. 또한, 오늘은 Node JS module을 간단하게 사용하는 방법을 배웠으니 앞으로 더욱 익숙해지고 Node JS로 더 복잡한 프로그램들을 만들 수 있기 위해 계속 학습해보도록 하겠습니다.

<br><br><br>

<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프