---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 14"
date: 2023-08-03
descripton: "Day 14 in AI+웹개발 취업캠프"
tags:
    - diary
---

<br>
## DB 만들다가 나온 문제들
---
<br>

- 데이터베이스를 어떻게 구성해야 데이터를 완벽하게 관리할 수 있을지 방법을 몰랐다.
	- 각 entity의 기본값을 어떻게 설정하는지 많이 고민했다.
	- HeidiSQL이나 DBeaver의 기능 숙지할 필요가 있었다.
	- 테이블 간 관계 모델링, 또는 Primary Key, Foreign Key 설정 등 잘하는 방법을 모른다.

<br>

## DB 만들 때 강사님의 조언
---
<br>

Foreign Key를 알아야 데이터베이스 생각하면서 코딩할 수 있다.
단, 실무에서 DB 수정할 것이 많을 수 있으니 Foreign Key를 잘 사용하지 않을 수 있다.

<br>
## DB REVIEW
---
<br>

지난 강의에 했던 것들 정리를 하자면...

- local 데이터베이스를 만들었다
- DBeaver나 HeidiSQL을 통해 로컬 데이터베이스를 열고, 로컬 서버와 잘 연결되어 있는지 connection을 테스트하여 확인했다.
- DB안에 table과 column을 만들었다.
- 정리하고 싶은 데이터를 table과 column에 저장했다.

<br>

## 학습 목표
---
<br>

- 실질적으로 데이터를 저장할 수 있는 방법을 배운다 (CRUD - Create Read Update Delete).
- 데이터베이스 안에 있는 데이터를 조회하는 방법을 배운다.
- 데이터베이스 안에 있는 테이블을 조합하는 방식을 배운다.

<br>

## SQL 기본 문법
---
<br>

실행하고자 하는 명령어를 입력하고 ENTER 누르면 명령어를 실행한다.

#### 데이터 생성

```sql
INSERT INTO
```

<br>

## SQL 편집기 사용
---
<br>

데이터베이스 선택  > 오른쪽 클릭 > 새 SQL 편집기

![](/posts/posts_images/aiweb_day14/11a3b8553fca4771fe8c67ef65a91b5e.png)

#### NOTE. 주석 - '##' 사용

이 SQL script 파일 내용을 수정할 때마다 저장해야 한다.

<br>

#### 데이터 불러오기

SQL 작성할 때 소문자보다 대문자로 쓰는 것을 선호한다.

테이블명과 column명을 대소문자 구분한다.

SQL을 작성하기 위해 syntax를 외워야 한다.

<br>

#### ISSUE. DBeaver에서 SQL 대문자를 자동으로 소문자로 변경한다. <br>
ref. https://stackoverflow.com/questions/42004796/how-to-switch-the-capitals-characters-transform-in-dbeaver, https://soo02.tistory.com/24

해결방식. Preferences에서 Auto-formatting 기능 끄기

![](/posts/posts_images/aiweb_day14/8c75cf31eda4f3450c2e5f51c378970a.png)

윈도우 > 설정 > 편집기 > Code Editor > Convert keyword case 끄기 > Apply 또는 Apply and Close


데이터베이스에 있는 데이터를 모두 select하고 가져오기

![](/posts/posts_images/aiweb_day14/6a8e772cc93fa3777db7ff0026b73f2e.png)

```sql
SELECT * FROM test
```

위 명령을 입력하고 `Ctrl+Enter` 눌러서 SQL script를 실행한다.

`*` 의 의미 : Wildcard
- 패턴을 추론하는 문자
- 가능한 모든 걸 매칭하는 문자

예약한 호텔 방 번호(RoomNum) 데이터 가져오기

![](/posts/posts_images/aiweb_day14/5e958415ac8b27aca99a2b7385fffe63.png)

```sql
SELECT RoomNum FROM test
```

예약한 호텔 방 번호(RoomNum)과 이름(Name) 데이터 가져오기

![](/posts/posts_images/aiweb_day14/7b2ff948597db71a31e2d5266310525f.png)

```sql
SELECT RoomNum, Name FROM test
```

#### NOTE. SQL Exercise 사이트 참고 <br>
ref. https://www.w3schools.com/sql/exercise.asp?filename=exercise_select1



데이터를 만들어보기 (데이터를 추가하는 방법)

- 데이터를 테이블에 추가하는 것이다.

![](/posts/posts_images/aiweb_day14/99fa032b4971ad8dbb84b26166b891df.png)

```sql
INSERT INTO table(field1, field2, field3, ...)
VALUES (data_value1, data_value2, data_value3, ...)
```
	이 방법 더 선호한다!

```sql
INSERT INTO table
VALUES (data_value1, data_value2, data_value3, ...)
```
	이 방법을 선호하지 않는 이유 :
	모는 컬럼에 값이 들어가야 해서 
	실수로 값을 빼먹을 때 곤란하다

data_value(데이터 값)으로 entity를 써도 상관없다.
INSERT로 데이터를 만들 때 data_value의 순서를 곡 지켜야 한다


![](/posts/posts_images/aiweb_day14/c5a10bae0cb3c89ea5764575be65cda6.png)

NOTE. 어떤 내용/라인을 선택해서 실행하면 그 부분만 실행할 수 있다. 

데이터가 추가된 것을 확인한다.

```sql
SELECT * FROM test
```

![](/posts/posts_images/aiweb_day14/aba0de3cba08886ce69f30053827921b.png)

<br>

## 데이터 업데이트
---
<br>

기존 데이터를 변경하려면 `UPDATE`를 사용한다.
단, 이미 데이터베이스에 있는 데이터가 무엇인지 알고 있어야 한다.

```sql
UPDATE table
SET field1=data_value1, field2=data_value2
WHERE field=data
```

- `UPDATE` : 테이블을 업데이트한다
- `SET` : 데이터를 설정한다
- `WHERE` : 컬럼 어떤 데이터를 가지고 있는지

예시)
```sql
UPDATE Users SET phoneNum='010-1234-3000'
WHERE ReserveDate = '2023-08-01'
```

![](/posts/posts_images/aiweb_day14/b6351a44fccf81b56ec7ebd857bb19d8.png)

<br>

## 데이터 삭제해보기
---
<br>

- DELETE는 특정값을 지울 수 없다. 특정값을 지우려면 UPDATE를 통해 값을 NULL로 변경해야 한다.

데이터베이스 아닌 테이블에서 데이터를 삭제한다

```
DELETE FROM table
WHERE field=data_value
```

![](/posts/posts_images/aiweb_day14/3df5467402d2353d9f50bebe40d4502d.png)

데이터 삭제되었는지 확인한다.

![](/posts/posts_images/aiweb_day14/dd1048a0be6ea63b4e474b9f056aaa28.png)

alias(별칭) 사용하기
- `as` 를 사용한다, 또는 별칭을 바로 옆에 쓴다

```sql
SELECT * FROM test t*
```

```sql
SELECT * FROM test as t*
```

SELECT에다 조건 또는 필터를 넣는 방법
- `SELECT ~ FROM`을 `WHERE`와 함께 사용

```sql
SELECT data FROM table
WHERE condition
```

![](/posts/posts_images/aiweb_day14/a80b2e954833e76aef54c5076d812d6c.png)

예시)
```sql
SELECT music FROM test t
WHERE age BETWEEN 20 AND 39 AND gender='female'
```

데이터를 정렬해보기

```sql
SELECT ~ FROM
ORDER BY ...
```

![](/posts/posts_images/aiweb_day14/7a9f7c0ad1815daf85f8fbd2af66016a.png)

내림차 순으로 정렬해보기

```sql
ORDER BY ... DESC
```

![](/posts/posts_images/aiweb_day14/1767aae899751dc90ce5e2874372e160.png)

그룹 함수 (aggregate function) - 집계

1. count() - record의 총 개수
2. min(), max() - 최소값, 최대값
3. SUM() - 합계
4. AVG() - 평균

집계가 가능한 데이터는 정량적인 데이터이어야 한다.
e.g. 나이 평균, id(index)수

![](/posts/posts_images/aiweb_day14/bb0d60fc915d42b43339c64393ada35d.png)

![](/posts/posts_images/aiweb_day14/cabf2f3f2b06fb64815652134a8e7aca.png)

![](/posts/posts_images/aiweb_day14/0bd97d3fa19adac445942603db989d35.png)

![](/posts/posts_images/aiweb_day14/5aa60c689f317d9e0f441fa686fabe04.png)

![](/posts/posts_images/aiweb_day14/7c93c7cde372c7d8333cd973c7589cae.png)

![](/posts/posts_images/aiweb_day14/a6407f55aea37d7aa3a3cfd834f7e286.png)

<br>

## SQL 타입, 연산자, 함수
---
<br>

![](/posts/posts_images/aiweb_day14/bb338d8d42b4e745ec47ee1f9a7125a5.png)

#### 숫자 타입
- Integer (정수)
- Fixed-point (고정 소수점)
- Floating-point (부동 소수점)
- Bit-value (비트값)


1. CHAR vs. VARCHAR
2. BINARY vs. VARBINARY
3. BLOG vs. TEXT
4. ENUM
5. SET

#### 날짜와 시간 타입

DATE, DATETIME, TIMESTAMP

#### 연산자, 비교 연산자

NOTE. 날짜도 비교연산자로 비교 가능하다.
날짜도 저장할 때 숫자로 표시된다.

![](/posts/posts_images/aiweb_day14/1bf035f0e168b4b28908ea1db0889f76.png)

- 가장 많이 사용하는 연산자 : IS NULL, IS NOT NULL
  어떤 데이터의 값이 null인지 아닌지 확인하기 위해 활용되는 연산자들이다.
- IN, NOT IN : 어떤 것이 리스트에 존재하는지 아닌지 확인할 때 쓰는 연산자이다.

<br>

## SQL 제약조건과 다중테이블연산
---
<br>

- `NOT NULL` : NULL 값을 가지면 안 된다
- `UNIQUE` : 단 하나의 unique한 값만 허용한다
- `PRIMARY KEY` : unique한 값이면서 테이블의 Primary Key 역할을 한다
- `FOREIGN KEY`: 외부 테이블을 참고하는 Foreign Key 역할을 한다
- `DEFAULT` : NULL 값이 들어오면 자동으로 default로 채워준다


<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프