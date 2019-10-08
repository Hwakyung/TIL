## 19_10_08 Database

데이터베이스의 구성요소

- 개체와 그들이 가지는 속성, 그리고 개체 사이의 관계

RDBMS:관계데이터베이스 관리 시스템

스키마 : 데이터베이스에서 자료의 구조, 표현방법, 관계등을 정의한 구조

PK:고유값이 존재



DDL:테이블,스키마 

데이터 검색(select) => read



``` python

$ sqlite3 test.sqlite3
SQLite version 3.29.0 2019-07-10 17:32:03
Enter ".help" for usage hints.
sqlite> .databases
main: C:\Users\student\sqlite\test.sqlite3
sqlite> .mode csv
sqlite> .import hellodb.csv examples
sqlite> SELECT * FROM examples;
1,"길동","홍",600,"충청도",010-2424-1232


sqlite> .headers on
sqlite> .mode column
sqlite> SELECT * FROM examples;
id          first_name  last_name   age         country     phone
----------  ----------  ----------  ----------  ----------  -------------
1           길동          홍           600         충청도         010-2424-1232
sqlite>
```
- 00_intro
``` sqlite
-- 데이터베이스 생성
.database

-- csv파일을 읽어오기 
.mode csv
.import hellodb.csv examples

--예쁘게 보기
.headers on
.mode column

--테이블 조회 (sql문법은 세미콜론을 붙어야함)
SELECT * FROM examples;
```
- 01_DDL
``` sqlite
-- DDL(데이터 정의 언어)
-- 구조를 정의
CREATE TABLE classmates(
    id INTEGER PRIMARY KEY,
    name TEXT
);
-- 테이블 목록 조회
.tables
-- 스키마 조회
.schema classmates
-- 테이블 삭제
DROP TABLE classmates;
.tables
-- 예제
CREATE TABLE classmates(
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INT,
    address TEXT
);
.tables
.schema classmates
```
- 02_CRUD
``` sqlite
CREATE TABLE classmates (
    -- id INTEGER PRIMARY KEY,
    name TEXT,
    age INT,
    address TEXT
);

--CREATE
INSERT INTO classmates (name, age,address)
VALUES ('최화경',26,'광주');


SELECT * FROM classmates; 

--CREATE
INSERT INTO classmates (name,address)
VALUES ('최화경','광주');

SELECT * FROM classmates; 

INSERT INTO classmates --순서가 있고 데이터 3가지 있을 때, 생략 가능
VALUES ('홍길동',30, '서울');

SELECT rowid,* FROM classmates; --rowid primary id를 자동 생성 시켜주는 키워드


--------------------------------------------------------
DROP TABLE classmates;

.tables
-- primary key를 쓸 때는 integer를 사용해야함

-- 기본으로 사용하는 rowid사용
CREATE TABLE classmates (
    name TEXT NOT NULL,
    age INT NOT NULL,
    address TEXT NOT NULL
);

INSERT INTO classmates(name,age, address)
VALUES ('최화경',24,'서울');

SELECT rowid, * FROM classmates;

DROP TABLE classmates;

.tables

CREATE TABLE classmates (
    name TEXT NOT NULL,
    age INT  NOT NULL,
    address TEXT  NOT NULL);

INSERT INTO classmates (name,age,address)
VALUES ('홍길동',30,'서울'), ('김철수',23,'대전'),('박나래',23,'광주'),('박요셉',29,'구미');

-- SELECT rowid, * FROM classmates;

-- OFFSET은 ~번째 부터 LIMIT 몇 개만 가져오는지 where column=value; 특정한 값만 가져오기 위해서
-- SELECT rowid, name FROM classmates LIMIT 1 OFFSET 2;
-- SELECT rowid, name FROM classmates WHERE address= '서울';

-- distinct 는  중복없이 값을 가져오는 것
-- SELECT DISTINCT age  from classmates;

-- rowid를 기준으로 삭제
DELETE FROM classmates WHERE rowid = 4;
INSERT INTO classmates VALUES('김이박',20,'대전');
UPDATE classmates SET name='홍길동',age=24,address='제주도' WHERE rowid=4;
SELECT rowid, * FROM classmates;

DROP TABLE classmates;

```

