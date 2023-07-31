---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 9"
date: 2023-07-27
descripton: "Day 9 in AI+웹개발 취업캠프"
tags:
    - diary
---

# JavaScript : DOM Element, Web API 

# 과제
---
<br>

# 주제 1. DOM element 분석

HTML 문서 앞에 `<script>` 태그 내에 js코드를 작성했고, 문서가 로드 되기 전에 script의 element를 가져오지 못한 상태에서 console.log로 디버그하여 개발자도구에 확인해보았을때는 왜 element를 가져와졌는지 이유에 대해서 알아보기.

참고 코드는 아래에 첨부합니다.

```
<!DOCTYPE html>
<html lang=“ko”>
<head>
    <meta charset=“UTF-8">
    <title>JavaScript DOM Element</title>
    <script>
        //HTML 태그 이름을 이용한 선택
        console.log(‘aaa’)
        var selectedItem = document.getElementsByTagName(“li”);     // 모든 <li> 요소를 선택함.
        console.log(selectedItem)
        console.log(selectedItem.length)
        for (var i = 0; i < selectedItem.length; i++) {
            selectedItem.item(i).style.color = “red”;   // 선택된 모든 요소의 텍스트 색상을 변경함.
            console.log(selectedItem.item(i));
        }
    </script>
</head>
<body>
    <h1>HTML 태그 이름을 이용한 선택</h1>
    <ul>
        <li>첫 번째 아이템이에요!</li>
        <li>두 번째 아이템이에요!</li>
        <li>세 번째 아이템이에요!</li>
        <li>네 번째 아이템이에요!</li>
        <li>다섯 번째 아이템이에요!</li>
    </ul>
    <script>
        var selectedItem = document.getElementsByTagName(“li”);     // 모든 <li> 요소를 선택함.
        for (var i = 0; i < selectedItem.length; i++) {
            selectedItem.item(i).style.color = “red”;   // 선택된 모든 요소의 텍스트 색상을 변경함.
        }
    </script>
</body>
</html>
```

![](/posts/posts_images/aiweb_day9/elements.png)

HTML 문서가 로드되기 전에 `document.getElementsByTagName("li")`를 통해 elements가 fetch되는 이유는 JavaScript 코드 실행 순서와 HTML 파싱과 관련이 있다.

브라우저로 html 파일을 열고 브라우저가 `<script>` 태그를 읽게 되면 즉시 JavaScript 코드를 실행하기 시작한다. 따라서 `document.getElementsByTagName("li")`로 요소를 가져오는 코드가 전체 HTML 문서를 파싱하고 로드하기 전에 실행된다.

단, 코드가 일찍 실행되더라도 스크립트는 실제 `<ul>` 및 `<li>` 요소가 만나기 전에 실행되기 때문에 실행 시점에서 요소들이 DOM에 추가되지 않은 상태이다. `console.log()` 문은 여전히 요소들을 가져왔다는 것을 보여줄 것이지만, DOM에 완전히 로드되기 전이기 때문에 빈 NodeList 또는 요소의 완전한 표현이 아닐 수 있다.

동일한 코드를 `<body>` 섹션의 끝인 `</body>` 태그 바로 앞에서 실행하면, 전체 HTML 문서가 파싱되고 DOM에 요소가 존재할 때 스크립트가 실행된다. 따라서 요소를 가져오고 조작할 수 있다.

DOM에 아직 존재하지 않은 요소를 가져오는 가능성을 피하기 위해 일반적으로 DOM과 상호작용하는 JavaScript 코드를 `<body>` 섹션의 끝에 배치하거나 `DOMContentLoaded` 이벤트를 사용하여 스크립트가 실행되기 전에 DOM이 완전히 로드된 것을 확인하는 것이 좋다. 이렇게 하면 스크립트가 실행될 때 해당하는 요소가 DOM에 존재하는 것이 보장된다.


# 주제 2. Web API 사용

- OpenWeather API - 일기예보 정보 가져오는 API (Weather 위젯을 만들기 위해 사용할 API)
  https://openweathermap.org/api
- Inspiration - Tyler Galpin의 포트폴리오 사이트
  https://www.galp.in/
- Implementation References
	- ASMR Programming - Weather App With Javascript. https://youtu.be/iILFBGm_I9M
	- Build a Real-Time Weather App with JavaScript and OpenWeatherMap API. https://javascript.plainenglish.io/build-a-real-time-weather-app-with-javascript-and-openweathermap-api-bcf8111df1fe
	- Creating a Weather app in Node.js using the Openweathermap API. https://www.section.io/engineering-education/create-a-weather-app-in-nodejs-using-openweathermap-api/

## Sign-In

API를 사용하기 위해 로그인이 필요한 서비스 API입니다. 아직 계정이 없어서 먼저 회원가입~
Username, Email, Password 기입, 권한 동의, 사용용도 입력 등 회원가입 과정 끝나고 나서 로그인을 했습니다.

## About OpenWeather

나라 또는 어떤 시에 따라 일기예보 정보를 가져오는 API입니다. 데일리 또는 8일 일기예보, 온도, 습기, 자외선 등 현재 날씨 데이터 뿐만 아니라 과거 기상 데이터나 예상 날씨 데이터까지 알려줄 수 있습니다. 유료 서비스도 제공되고 있지만 이번에는 간단한 날씨 위젯(Weather Widget)을 만들기 위해 하루 1분에 약 60번의 API 호출을 허락하 무료 서비스를 이용해 보겠습니다. API 호출해서 위젯을 구현해 보고 전에 이미 만들었던 메인 페이지에 기능으로 추가하도록 하겠습니다.

![](/posts/posts_images/aiweb_day9/openweather_plan.png)

## Weather Widget 만들기 과정

### 메인 페이지 업데이트

우선 메인 페이지에서 날짜와 시간, 일기예보를 텍스트로 표시할 수 있도록 코드를 수정해서 공간을 만들었습니다.

```html
<div class="misc">
	<div class="date">July #, 2023</div>
	<div class="time">00:00</div>
	<div class="weather">The weather is ...</div>
</div>
```

![](/posts/posts_images/aiweb_day9/api_prep1.png)

![](/posts/posts_images/aiweb_day9/api_prep2.png)

### 자바스크립트 파일 만들기 - weather.js

자바스크립트 (.js) 파일 만들고 HTML 파일 안에서 `<script>` 태그를 사용하여 파일을 참고합니다.

![](/posts/posts_images/aiweb_day9/weather_js.png)

```html
<script src="weather.js"></script>
```

### 자바스크립트 파일 안에서 API 호출

우선 OpenWeather 홈페이지에서 시의 이름을 입력하여 데이터베이스에 포함되어 있는지 확인했습니다.
https://openweathermap.org/city/1835848

![](/posts/posts_images/aiweb_day9/openweather_city.png)

Seoul에 대한 날씨 데이터가 잘 나타나는 것을 확인했으니 이제 API를 호출해서 가져오면 될 것 같네요!
API를 호출하는 방식을 배우도록 가이드를 홈페이지 안에 제공된 가이드를 참고했습니다.
https://openweathermap.org/guide, https://openweathermap.org/appid

그 다음, API를 호출하기 위해 사용할 API Key를 확인하고 복사합니다.

![](/posts/posts_images/aiweb_day9/openweather_apikey.png)

`fetch()` 를 이용하여 API 호출해 보겠습니다. `city`와 `APIKey`라는 변수를 다로 선언하고 다음과 같이 API를 호출합니다.

```
fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${APIKey}`)
```

호출하는 API 링크를 접속하여 JSON 데이터 또는 내용이 제대로 나타나는지 한번만 확인!
(아래 내용은 실시간에 따라 변경됩니다.)

```json
{"coord":{"lon":126.9778,"lat":37.5683},"weather":[{"id":802,"main":"Clouds","description":"scattered clouds","icon":"03n"}],"base":"stations","main":{"temp":25.71,"feels_like":26.66,"temp_min":24.76,"temp_max":26.78,"pressure":1014,"humidity":89},"visibility":6000,"wind":{"speed":1.54,"deg":240},"clouds":{"all":40},"dt":1690745621,"sys":{"type":1,"id":8105,"country":"KR","sunrise":1690749266,"sunset":1690800144},"timezone":32400,"id":1835848,"name":"Seoul","cod":200}
```


## HTML 원소를 업데이트하는 함수 만들기

`querSelector`를 이용하여 HTML 파일 안에 만든 element들을 모두 select하고 JS 파일 안에서 접근할 수 있기 위해 객체를 변수에 저장합니다.

```js
const weatherElement = document.querySelector('.weather');
const highTempElement = document.querySelector('.high_temp');
const lowTempElement = document.querySelector('.low_temp');
const cityElement = document.querySelector('.city');
```

JSON 데이터를 참고하면서 HTML 원소들의 내용을 맞는 데이터로 변경하고 업데이트해줍니다.

```js
weatherElement.textContent = weatherData.weather[0].description;
highTempElement.textContent = `${Math.round(weatherData.main.temp_max)}°C`;
lowTempElement.textContent = `${Math.round(weatherData.main.temp_min)}°C`;
cityElement.textContent = city;
```

최종 함수는 다음과 같이 완성됩니다.

```js
function updateWeatherDetails(weatherData) {
    const weatherElement = document.querySelector('.weather');
    const highTempElement = document.querySelector('.high_temp');
    const lowTempElement = document.querySelector('.low_temp');
    const cityElement = document.querySelector('.city');

    weatherElement.textContent = weatherData.weather[0].description;
    highTempElement.textContent = `${Math.round(weatherData.main.temp_max)}°C`;
    lowTempElement.textContent = `${Math.round(weatherData.main.temp_min)}°C`;
    cityElement.textContent = city;
}
```


## fetch하고 할 일에 대해 코드 작성

API의 url을 접속해서 JSON 데이터를 가져온 후 HTML 원소들의 내용을 업데이트하는 함수를 부릅니다. 만약 데이터를 fetch하는 동안 에러가 발생하면 에러 내용을 콘솔창에 출력하도록 했습니다.

```js
fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${APIKey}`)
    .then(response => response.json())
    .then(json => {
        updateWeatherDetails(json);
    })
    .catch(error => {
        console.error('Error fetching weather data:', error);
    });
```


# Date & Time 표시

## HTML 파일에서 레이아웃 구성하기 

아까 준비한 텍스트 공간의 내용을 수정해서 글 사이에 month, day, year를 각자 표시할 수 있도록 `<span>` 요소를 추가합니다.

```html
<!--Date-->
<div class="date">
	On <span class="month">Month </span>
	<span class="day">#, </span>
	<span class="year">yyyy</span>
</div>

<!--Time-->
<div class="time_details">
	It's <span class="time">00:00</span>
	<span class="am_pm">AM/PM</span>
</div>
```

## 자바스크립트 파일 새로 만들기 - date_time.js

![](/posts/posts_images/aiweb_day9/date_time_js.png)

`date_time.js` 파일 안에서 현재 날짜와 시간 데이터를 가져오고 HTML 내용을 업데이트하는 함수를 구현해 보겠습니다.

우선 `querySelector`를 다시 사용해서 HTML에 있는 element들을 select하기

```js
const dateElement = document.querySelector('.date');
const timeElement = document.querySelector('.time');
const amPmElement = document.querySelector('.am_pm');
```

현재 날짜와 시간을 알 수 있도록 JavaScript에서 제공되는 Built-in 객체 `Date` 를 활용할 예정이니 쉽게 접근할 수 있도록 `now`라는 변수에 저장해 두겠습니다.

```js
const now = new Date();
```

`now.getMonth()` 는 당월을 숫자로 나타내기 때문에 array를 만들어서 각 월의 영어 이름을 모읍니다.
ref. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMonth

```js
const months = [
	'January', 'February', 'March', 
	'April', 'May', 'June', 
	'July', 'August', 'September',
	'October', 'November', 'December'
]
```

이 array를 참고하여 `now.getMonth()`에서 return할 값을 index로 가정하고 그 index에 해당하는 월의 이름을 가져오는 방식으로 당월을 표시할 것입니다. 아래와 같이 month, day, year를 표시했습니다.

```js
const monthElement = document.querySelector('.month');
monthElement.textContent = months[now.getMonth()];

const dayElement = document.querySelector('.day');
dayElement.textContent = `${now.getDate()},`;

const yearElement = document.querySelector('.year');
yearElement.textContent = now.getFullYear();
```

그 다음으로, AM 또는 PM을 표시하기 위해 현재 hour에 따라 정오(12시)가 지났는지 확인하는 방식을 사용했고, 시간을 12시간제(12-hour format)로 표시하도록 코드를 작성했습니다.

```js
let hours = now.getHours();
const amPm = hours >= 12 ? 'PM' : 'AM';
// change to 12-hour format
hours = hours % 12 || 12;
```

형식을 변경한 후 시간과 AM/PM에 해당하는 HTML 원소의 내용을 업데이트했습니다.

```js
timeElement.textContent = `${hours.toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')}`;
amPmElement.textContent = amPm;
```

이후 페이지를 접속하자마자 날짜 및 시간을 표시할 수 있도록 함수를 호출했고

```js
updateDateTime();
```

실시간으로 날짜 및 시간 데이터가 업데이트될 수 있도록 타이머를 추가했습니다.

```js
// update date and time every second
setInterval(updateDateTime, 1000);
```

<br><br>

# Final Output
---

![](/posts/posts_images/aiweb_day9/weather_date_time.png)

<br><br>

# TODO. 다른 API 추가

- 언어를 번역하는 API (esp. ENG, KOR)
	- translate-api
		- ref. https://www.npmjs.com/package/translate-api?activeTab=readme, https://github.com/yixianle/translate-api#readme
	- translatte
		- ref. https://github.com/extensionsapp/translatte
	- Google Translate API
		- ref. https://www.section.io/engineering-education/working-with-translate-api-in-nodejs/






<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프 