# SQL 요약

**INSERT : 새로운 데이터 삽입**

**SELECT : 저장되어 있는 데이터 조회**

**UPDATE : 저장되어 있는 데이터 갱신**

**DELETE : 저장되어 있는 데이터 삭제**



```mysql
# 테이블 전체 조회 / 특정 테이블의 레코드(행) 정보를 반환
SELECT * FROM 테이블 이름;


# id와 함께 조회 / rowid는 primary key 속성을 가짐
SELECT rowid, * FROM 테이블 이름;


# INSERT / 특정 테이블에 레코드를 삽입
INSERT INTO 테이블 이름 (컬럼1, 컬럼2, ...) VALUES (값1, 값2, ...)
INSERT INTO examples (name, address) VALUES ('Nick', 'Seoul')


# 특정 컬럼 조회
SELECT 컬럼1, 컬럼2, ... FROM 테이블이름;
SELECT rowid, name FROM example


# LIMIT(원하는 수만큼 데이터 조회)
SELECT 컬럼1, 컬럼2, ... FROM 테이블이름 LIMIT 숫자;


# OFFSET(특정 부분에서 원하는 수 만큼 데이터 조회) / 파이썬 슬라이싱 처럼 생각 [숫자:]
SELECT 컬럼1, 컬럼2, ... FROM 테이블이름 LIMIT 숫자 OFFSET 숫자;


# WHERE(특정 데이터 조건 조회)
SELECT 컬럼1, 컬럼2, ... FROM 테이블이름 WHERE 조건;
SELECT rowid, name FROM example WHERE age=25;
SELECT rowid, name FROM example WHERE age>=25;
SELECT rowid, name FROM example WHERE age>=25 AND address='서울';


# DISTINCT / 특정 컬럼을 기준으로 중복없이 가져오기
SELECT DISTINCT 컬럼 FROM 테이블 이름;
SELECT DISTINCT age FROM example;


# DELETE / 중복 없는 값으로 삭제하기(rowid)
DELETE FROM 테이블이름 WHERE 조건;
DELETE FROM example WHERE rowid=5;


# UPDATE / 중복 불가능한 조건에서 수정하기
UPDATE 테이블이름 SET 컬럼1=값1, ... WHERE 조건;
UPDATE example SET name='nick' WHERE rowid=5;


# Sqlite Aggregate Functions
SELECT COUNT(*) FROM 테이블이름;
SELECT COUNT(컬럼) FROM 테이블이름;
SELECT AVG(컬럼) FROM 테이블이름;
SELECT SUM(컬럼) FROM 테이블이름;
SELECT MIN(컬럼) FROM 테이블이름;
SELECT MAX(컬럼) FROM 테이블이름;
SELECT COUNT(컬럼) FROM 테이블이름 WHERE 조건;
SELECT AVG(컬럼) FROM 테이블이름 WHERE 조건;
SELECT SUM(컬럼) FROM 테이블이름 WHERE 조건;
SELECT MIN(컬럼) FROM 테이블이름 WHERE 조건;
SELECT MAX(컬럼) FROM 테이블이름 WHERE 조건;


# LIKE / % : 해당 자리에 문자열이 있을 수도, 없을 수도 있음 / - : 해당 자리에 반드시 문자가 있어야 함
SELECT * FROM 테이블 WHERE 컬럼 LIKE '와일드카드패턴';
SELECT * FROM users WHERE phone_number LIKE '%-1234-%';
SELECT * FROM users WHERE phone_number LIKE '_10-1234-%';


# ORDER BY / 조회 결과 집합을 정렬
SELECT * FROM 테이블 ORDER BY 컬럼 ASC;
SELECT * FROM 테이블 ORDER BY 컬럼1, 컬럼2 DESC;
SELECT * FROM example ORDER BY age ASC LIMIT 10; # 오름차순 정렬, 상위 나이 10개


# GROUP BY / 행 집합에서 요약 행 집합
SELECT 컬럼1, aggregate_function(컬럼2) FROM 테이블 GROUP BY 컬럼1, 컬럼2;
SELECT first_name, COUNT(*) FROM users GROUP BY first_name; # 각각의 이름이 몇 명씩 있는지 조회


# ALTER / 테이블 이름 변경, 테이블에 새로운 column 추가 및 이름 수정
ALTER TABLE 기존테이블이름 RENAME TO 새로운테이블이름;
ALTER TABLE 테이블이름 ADD COLUMN 컬럼이름 데이터타입 설정;
```

* 출처[https://github.com/rudolphython]