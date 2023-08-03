---
title: "[AI웹개발 취업캠프/정보통신산업진흥원(NIPA)] Day 13"
date: 2023-08-02
descripton: "Day 13 in AI+웹개발 취업캠프"
tags:
    - diary
---


## Today's Insight
---
<br>

회사에서 Framework를 많이 사용한다. 단, IT트렌드는 시대마다 바뀐다. 지금 어떤 트렌드를 배워도 어차피 몇 년이 지나면 배운 가치가 없어지는데 어떻게 한면 좋을까? 개발자로서 가지고 있어야 할 스킬은 뭔가 새로 나오면 내가 배울 수 있어야 한다.

"OS, 알고리즘...이거 언제 다 배우냐?"<br>
CS 개념 많이 알고 있으면 좋지만, 이 개념들 다 빨리 배우는 것이 중요하지 않고 회사에 들어가서 일을 할 수 있는 능력이 더 중요하다.

어떤 기술이 필요할 때 시간 비용을 생각해서 사용하는 방식을 생각해야 한다. 그저 배우는 것 뿐만 아니다.

어떤 트렌드가 뜰 경우 어떻게 빨리 배우냐 보다, 뭔가 어떤 목표가 있을 때 이것을 필요로 사용해야 되는 것인가 이러한 태도를 가지고 트렌드를 봐야 한다.

새로운 기술을 배울 때 생각하는 이유와 사용용도를 고려해야 한다.

DB는 다 비슷하다. 회사마다 다르게 사용하는 이유는 회사에서 하는 일에 따라 바뀐다. DB는 다른 기술이나 프레임워크처럼 만들거나 관리하는 서비스에 맞춰서 사용된다.

## 학습 목표
---
<br>

- 데이터베이스를 다루는 방법을 배운다.
- SQL 언어를 이해하고 프레임워크나 프로그래밍 언어와 함께 사용할 수 있어야 한다.

## 데이터베이스 SQL (Structured Query Language)
---
<br>

데이터베이스에서 데이터를 정의, 조작, 조절할 때 사용하는 언어

1. DDL (Data Definition Language)
	- 데이터를 정의하는 언어
2. DML (Data Manipulation Language)
	- 데이터를 조작하도록 하는 언어
3. DCL (Data Control Language)
	- 데이터를 조절하는 언어

![](/posts/posts_images/aiweb_day13/eb10ec7bd5107dcbeb9fd39f10775e97.png)

## Relational Database (관계형 데이터베이스) -- RDB, relational DB
---
<br>

- 테이블(table)로 이루어져 있는 데이터베이스
- 테이블은 key와 value의 관계를 나타낼 수 있다. 이러한 테이블을 통해 데이터의 종속성을 관계(relationship)로 표현하는 것이 이 데이터베이스의 특징이다.

## ERD (Entity Relationship Diagram)
---
<br>

#### ERD는 어디서 볼 수 있다?
학교에서 예로 보는 ERD가 아닌 실제 ERD는 회사 다닐 때말고 거의 볼 수 없는 것이다.
#### Entity (엔티티)
- 존재하는 것
- 사물, 사람 등 행위자 또는 개념적으로 표현할 수 있는 것
#### Relationship (관계)
엔티티스의 관계를 나타내는 것
1. 일대일(One-to-One) - 한개의 entity가 다른 entity에 1개를 가지는 관계
2. 일대다(One-to-Many) - 하나의 entity가 다른 entity를 1개 이상을 가지는 관계
3. 다대다(Many-to-Many) - 여러 개의 entity가 다른 entity를 1개 이상을 가지는 관계
#### Diagram (도표)
- Entities들의 관계들을 시각화하여 보여주는 도면(일종의 프로그램 설계 도면)

Example

한 사람이 하나의 주민 등록번호를 가지는 것은
일대일 관계인가요?

엔티티에서 관계라는 뭐가 엔티티가 공통적인 부분을 의미한다.

테이블과 테이블의 관계라기보단 필드와 레코드

남영관계는 일대일이다.

## 데이터베이스 사용하는 이유
---
<br>

- 데이터베이스가 코드보다 더 관리하기 쉽다.
- 이유 (다음은 줌강의에서 나온 답들의 정리)
	- 데이터가 더 많아지고 관계가 복잡해지면 가독성도 떨어지고, 관련된 데이터들을 한번에 수정하기 어렵다 (한번에 수정하기에 더 쉽다).
	- 데이터가 정제되어 있기 때문이다
	- 데이터베이스는 이미 데이터를 저장에 대해 용이하게 만들어져 있기 때문이다
	- 데이터들을 다른 프로그래밍 언어에도 호환할 수 있도록 하기 위한 것이다.
	- 코드를 사용하면 코드를 작성해야 되기 때문이다 (데이터를 저장하기에는 코드 변경을 자주 할 수 밖에 없다).

#### 강사님 설명
- 코드는 자주 바뀌고 데이터베이스는 테이블을 하나 만드는데 자주 바꾸지 않는다.
	- 데이터 일관성 유지, 안전성을 위해 잘 안 바뀐다.

- 프로그램을 만들 때 데이터 관계를 파악해서 관계 모델링을 먼저 한다.
	- 이유: 설계를 하기 위한 것이다. 즉, 설계도(diagram)를 먼저 만들어야 하기 때문이다.

- 즉, ERD는 회사의 프로그램 설계도이다.
	- 회사의 데이터가 포함되어 있으니 구글링해도 교육 자료에서 예시로 보여주는 ERD 외에는 공개된 실제 ERD를 인터넷에서 찾을 수 없다.

- 프로그래머들은 데이터베이스를 대부분 알고 있다
	- DB를 배우고 다른 프레임워크를 배운다.
	- 최소한 관계 데이터베이스를 알고 있어야 한다.


ERD는 table 하나를 의미할 수 있다.


## 관계형 데이터베이스 개요
---
<br>

![](/posts/posts_images/aiweb_day13/5be196757fe7350dca2819fb1121330c.png)

- entity를 key-value 형식으로 표현하고 mapping한다

ERD는 다양하게 만들 수 있지만 국제표준으로 IE 표기를 사용한다.

attribute - column data (테이블의 속성)
relation - 데이터 간 관계를 표기한다 (이미지 참고.)

한국은 주민번호가 있고, 다른 나라는 왜 주민번호가 없다 (또는 다른 것을 사용한다) 이유?

- 개인정보 유출 (한번 유출되면 치명적이다)
- 통제 가능성이 있다
- 국가가 개인을 감시할 수 있다

#### Primary Key (PK)
- 엔티티의 행(row)을 식별할 수 있는 index
- 중복 불가능
#### Foreign Key (FK) - 외래키
- 두 엔티티를 연결할 수 있는 attribute


## 실습
---
<br>
## Add MySQL to PATH

ref. https://bskyvision.com/entry/MySQL-%EC%9C%88%EB%8F%84%EC%9A%B0-PC%EC%97%90%EC%84%9C-MySQL-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95

```
C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe
```
<br>

Path 편집 <br>
![](/posts/posts_images/aiweb_day13/6ea9994b4f7693dd7e408f32aff8a991.png)

새로 만들기 > mysql bin 폴더 경로 넣고 확인 누르기

![](/posts/posts_images/aiweb_day13/9d9ec928d545e3fb373c4d4dbba76896.png)

```
C:\Windows\System32>mysql --version
mysql  Ver 8.0.34 for Win64 on x86_64 (MySQL Community Server - GPL)
```

#### ERROR 1045
- `mysql -u root` 명령어하고  같이 password를 입력하지 않으면 접속 불가능
- 해결방식 : `-p` 붙이고 password 요구할 때 입력하기

```
C:\Windows\System32>mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

![](/posts/posts_images/aiweb_day13/f80fcb46fb93f3d3904f8463e2f6c735.png)

비밀번호 변경 방법

```
mysql> alter user 'root'@'localhost' identified by '0000';
Query OK, 0 rows affected (0.03 sec)
```

![](/posts/posts_images/aiweb_day13/7ae5e115bbbcc60437eeb69cece695fb.png)

## HeidiSQL에서 local database 열기
---
<br>

ref. https://www.youtube.com/watch?v=56_cCdC279A
<br>
ref. https://www.inmotionhosting.com/support/server/databases/connecting-heidi-sql-database/

![](/posts/posts_images/aiweb_day13/53bbe1ade3c0f207d5b4aee102b677c1.png)

![](/posts/posts_images/aiweb_day13/3ba1b5e8f7d5187be9094e9530539b3e.png)

## 데이터베이스 생성
---
<br>

![](/posts/posts_images/aiweb_day13/2c9caa40b6ab0feb343c46f5a8ef7961.png)

undefined

백그라운드 설명 : MySQL은 `CREATE DATABASE` 명령어를 실행하고 myweb이라는 데이터베이스를 만든다.

![](/posts/posts_images/aiweb_day13/d685624a9903380fc881fa9b127b1f2a.png)

myweb 안에 테이블 생성

![](/posts/posts_images/aiweb_day13/47a3e9faf9b0f115990ae5fecf377f73.png)
![](/posts/posts_images/aiweb_day13/51eb783c6e1e8df59fb82f926a0029b6.png)


undefined

ID : column (INT : integer로 저장)
Name : (VARCHAR(30) : char를 30개까지 i.e. 문자열)
ReserveDate : DATE (날짜 자료유형)
RoomNum

열 추가

![](/posts/posts_images/aiweb_day13/42395fe2be6269013abf4aa8b8b4219d.png)

![](/posts/posts_images/aiweb_day13/7b270efcae4ecf3483e32bb7b42beac2.png)

변수 등 table에 넣을 데이터에 따라 table의 column 생성

그 다음, 저장 누르기

HeidiSQL 화면

![](/posts/posts_images/aiweb_day13/9e1d443a651af5d0845403206aac4371.png)

생성된 CREATE CODE

```mysql
CREATE TABLE `test` (
	`ID` INT(10) NULL DEFAULT NULL,
	`Name` VARCHAR(30) NULL DEFAULT NULL COLLATE 'utf8mb4_0900_ai_ci',
	`ReserveDate` DATE NULL DEFAULT NULL,
	`RoomNum` INT(10) NULL DEFAULT NULL
)
COLLATE='utf8mb4_0900_ai_ci'
ENGINE=InnoDB
;
```

데이터 column에서 확인 (Excel 방식대로 표시)

![](/posts/posts_images/aiweb_day13/8eba26f5062357cbcfbcdbc9ece1a0dd.png)

DBeaver 화면
![](/posts/posts_images/aiweb_day13/5b4575ee594e5b470faf4e17952e83b5.png)

Add data by making rows

![](/posts/posts_images/aiweb_day13/dc69696d5a274b1ce5ab40752dfaaa00.png)


Set Primary Key

![](/posts/posts_images/aiweb_day13/9bd438c4830c4ace52fe20a1b56f6426.png)

Relation 만들기. 
외래키 column으로 가서 Foreign Key 생성


![](/posts/posts_images/aiweb_day13/b71a837becf286fa6870d1a8f359242b.png)
![](/posts/posts_images/aiweb_day13/e91c4aafe539d36a9e6ca7271411ce57.png)
![](/posts/posts_images/aiweb_day13/fe43c2af674133e0d2b21eafe4e200ee.png)
![](/posts/posts_images/aiweb_day13/da63c2b44c8d08a521c309ced56163d7.png)
Foreign Key symbol 생성 확인

![](/posts/posts_images/aiweb_day13/0e6e255829be72d01e285ccb6d8bacd7.png)

<br>

## 결과
---
<br>

subjects table
![](/posts/posts_images/aiweb_day13/5b2817f6a1052bef03f05f2d635f475c.png)

students table

![](/posts/posts_images/aiweb_day13/a1dadd7188ef5d1c80a12899a19eaa9b.png)

students table안에서 만들었던 foreign key

![](/posts/posts_images/aiweb_day13/6c72b52fc695052f7b3bd71d851fa4cf.png)

subjects table 데이터 생성 (행 추가)

![](/posts/posts_images/aiweb_day13/be7470730fd19097432515dbba10d771.png)

students table에서 foreign key (ID)로 데이터 가져오기

![](/posts/posts_images/aiweb_day13/3e07b871676d0dc3d2b94e0c6c24fc7b.png)


DBeaver 화면

![](/posts/posts_images/aiweb_day13/3f7acdc403babbfd7e600de947bad9ca.png)

<br>
## Install DBeaver via chocolatey
---
<br>

![](/posts/posts_images/aiweb_day13/f1d10d87bb13e5210020da023ff3c154.png)
![](/posts/posts_images/aiweb_day13/469ee229cfc01c94f762c87a35970e83.png)
![](/posts/posts_images/aiweb_day13/76c0bd3561b710f95c9551123cc9cc9f.png)

![](/posts/posts_images/aiweb_day13/74f7dc5425ebe70e42b9e8ed74133f05.png)







## 과제 > Main Page DB 생성

우선 저는 메인 페이지에서 무슨 내용을 데이터베이스에 넣어야 하는지 먼저 결정해야 되는데 아래와 같이 생각을 좀 정리했습니다.

- Contact Me Form
	- 메인 페이지에서 Contact Me 폼이 있는데 거기서 웹사이트를 접속한 사람들이 저와 함께 협업하고 싶거나 연락하고 싶을 경우 사이트를 통해서 바로 메일을 보낼 수 있게 이름(Full Name), 이메일(E-mail), 그리고 간단한 메세지(Message)를 남길 수 있는 폼을 만든 것입니다.
	- 원래 폼을 작성하면 주어진 정보를 저장하지 않고 메일 형식을 자동으로 생성해서 제 이메일 주소로 발송하는 식으로 만들려고 했지만, 데이터베이스로 
- Works Page
	- 원래 메인 페이지를 포트폴리오 사이트로 사용할 예정이라서 메뉴에서 Works라는 섹션에서 제가 만든 프로젝트 등을 전시하기 위해 마련했습니다.
	- 이 섹션에 들어갈 프로젝트들을 계속 업데이트될 예정인데 큰 규모는 아니어도 한번 데이터베이스로 정리하면 더 깔끔할까 생각하고 있습니다.
- Blogs Page
	- 개인 블로그를 따로 md 파일 시스템으로 관리하고 있지만, 너무 많아질 수도 있으니 데이터베이스에 추가해서 제목과 날짜, 파일명 등으로 정리할 수 있는 가능성도 고려하고 있습니다.
	- 블로그 글 그리고 한 post마다 첨부할 사진, 관련 태그, 접속자가 남긴 댓글 등을 기록할 수 있는 데이터베이스를 만들 수 있는 것 같습니다.
	- 단, 현재 블로그 글 관리에 이미 시스템이 있으니 데이터베이스로 옮기는 방식이 더 유익할지 더 고민해 봐야 하기 때문에 오늘은 일단 간단한 데이터베이스만 만들어보겠습니다.

따라서 메인 페이지의 1) contact me 폼으로 입력받을 정보들, 그리고 2) works 섹션에 들어갈 프로젝트들에 대한 정보 (e.g. 프로젝트 이름, 완성한 기간 또는 날짜, 카테고리나 태그) 등, 3) blog 섹션에서 목록으로 나타낼 블로그 글들의 정보와 comment 정보를 정리해서 데이터베이스로 관리할 생각입니다.

<br>

## 참고할 자료.
---
<br>

- 포트폴리오나 블로그 사이트에 데이터베이스가 필요한 이유
	- https://www.quora.com/Should-I-use-a-database-for-a-portfolio-website
	- https://www.quora.com/Should-I-store-large-text-files-blog-post-in-a-database-or-in-a-file-system
- 워드프레스 블로그 데이터베이스 사용/관리하는 방법
	- https://wordpress.org/about/requirements/
	- https://www.wpbeginner.com/beginners-guide/beginners-guide-to-wordpress-database-management-with-phpmyadmin/
- 블로그 데이터베이스나 CMS (Content Management System)을 만드는 방법
	- https://www.youtube.com/watch?v=oIpyPyeNBUQ
- Content Database 필요한 이유
	- https://www.linkedin.com/pulse/you-need-content-database-stat-dorien-morin-van-dam/?trk=public_profile_article_view
- 실제로 portfolio DB의 ERD를 만들어본 분의 깃허브 repository
	- https://github.com/faizanfareed/Personal-portfolio-database-design-ERD-
### TODO.
1. HeidiSQL을 통해 웹사이트 데이터베이스 구성해보기
2. Entity, Relation 등을 구성하고 Primary Key, Foreigner Key를 정하기
3. ERD 생성 (DBeaver와 달리 HeidiSQL에서 ERD 생성 기능이 없으니 다른 툴 사용할 것)
4. 각 table과 column에 대한 설명을 별도의 테스트 파일에 작성
### NOTE.
매번 데이터베이스에서 데이터를 가져오면 메모리나 캐쉬 많이 사용돼서DB 사용하면 페이지 로드할 때 느려지는 것이 단점으로 예상되는데 일단 데이터 테이블 먼저 구성해보겠습니다.

## 1. DB 구성

#### Contact Form
- 검색해 보니 가장 긴 이메일의 문자수는 255개, 가장 긴 이름의 문자수는 747개로 나오네요 (신가하다! :O). 이에 따라 문자수 limit을 설정했습니다. 
	![](/posts/posts_images/aiweb_day13/858319b8ef413804f35df720530492f1.png)

#### Works
- 프로젝트 정보를 관리하기 위해 프로젝트 이름, 그리고 시작 날짜와 완성 날짜를 데이터에 포함합니다. 
- 각 프로젝트마다 시작 날짜는 항상 있고 아직 완성되지 않은 프로젝트 (i.e. ongoing project)는 완성 날짜를 NULL로 저장합니다.
- 프로젝트 이름의 경우 이름이 길 수 있으므로 VARCHAR(i.e. 문자열)으로 정해진 길이를 주는 것보다 TINYTEXT의 유형으로 저장합니다.
	![](/posts/posts_images/aiweb_day13/f7bcd3dfe54b1fcd82cb7867e4ae7f7c.png)

#### Blogs: Posts
- 블로그 post들에 대한 metadata를 포함하는 테이블을 만들었습니다.
	![](/posts/posts_images/aiweb_day13/d0c0f958a0166433e2bc11433579aa7f.png)
#### Blogs: Content
- 블로그 post 내용에 포함된 이미지, 텍스트, 이미지 링크 등을 기록하는 테이블을 만들었습니다
- 각 블로그 post의 내용은 `content_id` 에 따라 query 가능하게 만들었습니다.
- 내용의 각 요소 타입(image, text, url)은 `content_type`로 표시합니다. 
	![](/posts/posts_images/aiweb_day13/362cb366723f1098943f8a70d7c1c866.png)

Sample Content <br>
![](/posts/posts_images/aiweb_day13/sample_content.png)
<br>
데이터 관리를 단순화하기 위해, 또는 하나의 데이터베이스 안에 데이터의 무결성을 유지하기 위해 열이 많은 하나의 테이블을 사용하여 다양한 콘텐츠를 효율적으로 저장하고 관리할 수 있게 만들었습니다.

<br> 

#### Blogs: Comments
- 블로그 글에 달았던 각 comment의 metadata를 관리하기 위한 테이블을 만들었습니다.
- author_name의 기본값을 'user'로 설정했습니다.
	![](/posts/posts_images/aiweb_day13/06775ae4455f1f89e4e680e45da8e88c.png)

## 완성된 mypage schema
![](/posts/posts_images/aiweb_day13/bcb1f7d989838c5cffa4ee6419a6f981.png)

## 2. Primary Key, Foreign Key 설정

- 각 테이블에서 사용하는 `id`는 primary key로 설정했습니다
- foreign key는 테이블 간의 관계를 분석해서 모델링하고 나서 설정했습니다.

<br>

#### Blog : Posts
- Foreign Key 설정 (content_id : blog_content의 id 참고)
	![](/posts/posts_images/aiweb_day13/1d4c0542c49e73ff56613c0a3e0eeb74.png)

#### Blog : Content
- Foreign Key 설정 (blog_id : blog_posts의 id 참고)
	![](/posts/posts_images/aiweb_day13/9c103648e3b7ab372019273e7a7995ef.png)

#### Blog : Comments
- Foreign Key 설정 (blog_id : blog_posts의 id 참고)
	![](/posts/posts_images/aiweb_day13/478786b7b1f5bd37b3238ca321f63079.png)


## 3. ERD 생성

- MySQL Workbench : Reverse Engineering 기능
	- 2023.08.02. root와 연결하고 오늘 만든 myweb 데이터베이스에다 시도해보니 EER 다이어그램을 생성하는 기능이고 원래  내용이 나오지 않았네요... 빈 EER가 생성되었습니다...
- draw.io : 데이터베이스 Schema를 SQL 파일로 내보내서 draw.io에서 ERD 생성
	- HeidiSQL에서 schema를 SQL로 내보낸 후 draw.io에서 그 SQL 파일을 가져왔는데도 relation이 안 보였습니다...
	- 생성된 SQL 파일을 확인했더니 각 foreign key의 참고 내용이 제대로 포함되어 있는데... notation 차이 때문인지...

결국, DBeaver를 설치하고 ERD로 나타내서 relation을 확인했습니다.

![](/posts/posts_images/aiweb_day13/f8a73bb879323ac4f0c0263df6936659.png)

## 4. table과 column에 대한 설명

- `main_db_explanation.txt` 텍스트 파일 안에서 다음 내용을 작성했습니다.

```
TABLE. blog_posts
-- blog post들의 metadata DB

id : blog 글의 아이디
title : blog 글 제목
creation_date : blog 글을 생성한 날짜
tag : 블로그 글의 키워드나 태그 (블로그 글 카테고리를 만들 때 사용)
content_id : blog 내용에 해당되는 콘텐츠 아이디


TABLE. blog_comment
-- blog post에 유저들이 달았던 댓글 DB

id : 댓글 아이디
blog_id : 블로그 글 아이디 (foreign key) -- blog_posts의 id 참고
author_name : 댓글 단 사람의 이름
comment_text : 댓글 내영
comment_date : 댓글 단 날짜


TABLE. blog_content
-- blog post의 내용 DB

id : blog 콘텐츠 아이디
blog_id : blog 글 아이디
content_type : 콘텐츠의 자료 유형 (e.g. image, text, url)
content_text : 텍스트 내용 (콘텐트가 텍스트 유형이면 기입)
url_link : 이미지 url (콘텐츠가 이미지나 url 유형이면 기입)


TABLE. contact_form
-- contact form의 DB

id : contact 폼에 입력한 entry의 아이디
full_name : 내게 contact하고 싶은 유저의 이름
email : 내게 contact하고 싶은 사람의 수신 이메일 주소
message : 유저가 내게 전달하고 싶은 간단한 메세지 내용


TABLE. works
-- works 또는 프로젝트 섹션의 DB

id : 프로젝트 아이디
project_name : 프로젝트 이름
start_date : 프로젝트를 시작한 날짜
end_date : 프로젝트를 완성한 날짜
```


## TO IMPROVE

- DB를 잘 구성하기 위한 방법을 좀 더 익혀야 할 것 같습니다. 
	- 또한, 데이터베이스 사용의 장단점을 고려해서 언제 DB를 사용하는 것이 좋은지, 또 어떤 기능을 만들기 위해 DB를 어떻게 사용할 수 있는지 좀 더 자세히 알아봐야 할 것 같습니다.
- 포트폴리오 사이트의 디자인 또는 넣을 애니메이션이나 assets 등을 계획 중인데 데이터베이스를 넣어보니 추가적인 기능
- 각 entity의 기본값 생각해보기
	- e.g. id는 블로그 글이 나타날 때마다 AUTO_INCREMENT해야 하는지 고민해보기
- 추가로 Foreign Key를 만들 수 있는지 (서로 연결될 수 있는 테이블이 있는지) 확인
	- e.g. contact_form의 full_name은 author_name과 연결할지 고민해보기 (note. 댓글 달 때 username 말고 영문 본명을 사용할 경우)
- text와 image 콘텐츠를 서로 다른 table로 나누는 것이 더 좋을지 고민해보기
	- blog_text, blog_image인 형식으로 변경하면 좋을지 생각해보기



<br><br><br><br>

#### ——————————————————————————
본 후기는 정보통신산업진흥원(NIPA)에서 주관하는 <AI 서비스 완성! AI+웹개발 취업캠프 - 프론트엔드&백엔드> 과정 학습/프로젝트/과제 기록으로 작성 되었습니다.
#정보통신산업진흥원 #NIPA #AI교육 #프로젝트 #유데미 #IT개발캠프 #개발자부트캠프 #프론트엔드 #백엔드 #AI웹개발취업캠프 #취업캠프 #개발취업캠프 