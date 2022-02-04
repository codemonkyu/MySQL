
### 프로그래머스 [MySQL] [SELECT] [모든 레코드 조회하기]
#### Q. 동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.
---

```
select * from ANIMAL_INS
```
#### * 테이블의 모든 데이터를 출력 


### 프로그래머스 [MySQL] [SELECT] [역순 정렬하기]
#### Q. 동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.
---

```
SELECT NAME, DATETIME from ANIMAL_INS order by ANIMAL_ID desc
```
#### * oder by 기준 asc(default) / desc


### 프로그래머스 [MySQL] [SELECT] [아픈 동물 찾기]
#### Q. 동물 보호소에 들어온 동물 중 아픈 동물의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.
---

```
SELECT ANIMAL_ID, NAME from ANIMAL_INS
    where intake_condition = 'sick';
```
#### * WHERE_condition(조건식);


### 프로그래머스 [MySQL] [SELECT] [어린 동물 찾기]
#### Q. 동물 보호소에 들어온 동물 중 젊은 동물의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.
---

```
SELECT animal_id, name from animal_ins
    where intake_condition != 'aged';
```


### 프로그래머스 [MySQL] [SELECT] [동물의 아이디와 이름]
#### Q. 동물 보호소에 들어온 모든 동물의 아이디와 이름을 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.
---

```
SELECT animal_id, name from animal_ins 
order by animal_id ASC
```

#### * order by 기준 asc(오름차순), desc(내림차순)


### 프로그래머스 [MySQL] [SELECT] [여러 기준으로 정렬하기]
#### Q. 동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.
---
```
SELECT ANIMAL_ID, NAME, DATETIME 
from ANIMAL_INS 
order by name asc, datetime desc
```


### 프로그래머스 [MySQL] [SELECT] [상위 n개 레코드]
#### Q.동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문을 작성해주세요.
---
```
SELECT name 
from ANIMAL_INS
order by datetime
limit 1
```

#### * LIMIT 1을 통해 datetime의 상위 1개의 결과만 조회한다.

