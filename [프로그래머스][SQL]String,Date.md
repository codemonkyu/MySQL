### 프로그래머스 [MySQL] [string,date] [루시와 엘라찾기]
#### Q. 동물 보호소에 들어온 동물 중 이름이 Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물의 아이디와 이름, 성별 및 중성화 여부를 조회하는 SQL 문을 작성해주세요.
---

```
SELECT animal_id, name, sex_upon_intake from animal_ins
    where name in ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
    order by ANIMAL_ID ASC
```

### 프로그래머스 [MySQL] [string,date] [이름에 el이 들어가는 동물 찾기]
#### Q. 보호소에 돌아가신 할머니가 기르던 개를 찾는 사람이 찾아왔습니다. 이 사람이 말하길 할머니가 기르던 개는 이름에 'el'이 들어간다고 합니다. 동물 보호소에 들어온 동물 이름 중, 이름에 "EL"이 들어가는 개의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 이름 순으로 조회해주세요. 단, 이름의 대소문자는 구분하지 않습니다.
---

```
SELECT ANIMAL_ID, NAME 
FROM ANIMAL_INS
WHERE NAME like "%el%" and animal_type = 'dog'
ORDER BY NAME ASC
```
* like "%문자%"를 통해 원하는 단어가 사용된 이름 조회

### 프로그래머스 [MySQL] [string,date] [중성화 여부 파악하기]
#### Q. 보호소의 동물이 중성화되었는지 아닌지 파악하려 합니다. 중성화된 동물은 SEX_UPON_INTAKE 컬럼에 'Neutered' 또는 'Spayed'라는 단어가 들어있습니다. 동물의 아이디와 이름, 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 중성화가 되어있다면 'O', 아니라면 'X'라고 표시해주세요.
---

```
SELECT animal_id, name, case when sex_upon_intake like "%neutered%" or sex_upon_intake like "%spayed%" 
then 'O'
else 'X' end as '중성화'
from animal_ins
order by animal_id
```
* case구문은 삼항연산자랑 비슷, when조건 then 참일경우 else 거짓일경우 마지막 end로 닫아준다.

### 프로그래머스 [MySQL] [string,date] [오랜 기간 보호한 동물(2)]
#### Q. 입양을 간 동물 중, 보호 기간이 가장 길었던 동물 두 마리의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 기간이 긴 순으로 조회해야 합니다.
---
```
SELECT o.animal_id, o.name from animal_outs as o, animal_ins as i
where i.animal_id = o.animal_id
order by o.datetime - i.datetime desc
limit 2
```
* date타입끼리는 기본적인 연산이 가능하다

### 프로그래머스 [MySQL] [string,date] [DATETIME에서 DATE로 형 변환]
#### Q.ANIMAL_INS 테이블에 등록된 모든 레코드에 대해, 각 동물의 아이디와 이름, 들어온 날짜1를 조회하는 SQL문을 작성해주세요. 이때 결과는 아이디 순으로 조회해야 합니다.
---
```
SELECT ANIMAL_ID, NAME, date_format(datetime,"%Y-%m-%d") as 날짜
from animal_ins
order by animal_id
```
* %Y(4자리 연도), %y(2자리 연도), %m(월), %d(일), %H(24시간), %h(12시간), %i, %s


