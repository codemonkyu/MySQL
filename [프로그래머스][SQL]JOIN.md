
### 프로그래머스 [MySQL] [JOIN] [오랜 기간 보호한 동물(1)]
#### Q.아직 입양을 못 간 동물 중, 가장 오래 보호소에 있었던 동물 3마리의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 시작일 순으로 조회해야 합니다.
---

```
SELECT animal_ins.NAME, animal_ins.DATETIME FROM animal_ins
LEFT JOIN animal_outs
ON animal_ins.ANIMAL_ID = animal_outs.ANIMAL_ID
WHERE animal_outs.ANIMAL_ID IS NULL
ORDER BY animal_ins.datetime 
LIMIT 3
```
#### * ANIMAL_INS 테이블과 ANIMAL_OUTS 테이블에서 NAME,DATETIME을 LEFT JOIN으로 JOIN해준다.
#### * 조건으로 각각의 테이블의 ANIMAL_ID를 비교하고 범위로 ANIMAL_OUTS.ANIMAL_ID가 비어있는 범위를 해준다. 왜냐하면 입양을 못간
#### * 동물은 ANIMAL_OUTS이라는 입양테이블에 정보가 없기 때문이다. 이후 보호시작일순으로 ORDER BY 해주고 LIMIT 3으로 3행만 조회한다.


### 프로그래머스 [MySQL] [JOIN] [보호소에서 중성화한 동물]
#### Q. 보호소에서 중성화 수술을 거친 동물 정보를 알아보려 합니다. 보호소에 들어올 당시에는 중성화되지 않았지만, 보호소를 나갈 당시에는 중성화된 동물의 아이디와 생물 종, 이름을 조회하는 아이디 순으로 조회하는 SQL 문을 작성해주세요.
---
```
select I.ANIMAL_ID, I.ANIMAL_TYPE, I.NAME FROM ANIMAL_INS AS I JOIN ANIMAL_OUTS AS O
WHERE I.ANIMAL_ID = O.ANIMAL_ID AND I.SEX_UPON_INTAKE != O.SEX_UPON_OUTCOME
ORDER BY ANIMAL_ID 
```
#### * INS와 OUTS를 조인한다.
#### * ID가 같은 레코드만 남도록 조건을 걸고 INTAKE와 OUTCOME의 성별의 다른 동물을 찾는다.
#### * 나온 동물을 ANIMAL_ID 순으로 정렬해준다.


### 프로그래머스 [MySQL] [JOIN] [없어진 기록 찾기]
### Q. 천재지변으로 인해 일부 데이터가 유실되었습니다. 입양을 간 기록은 있는데, 보호소에 들어온 기록이 없는 동물의 ID와 이름을 ID 순으로 조회하는 SQL문을 작성해주세요.
---
'''
SELECT O.ANIMAL_ID, O.NAME FROM ANIMAL_OUTS AS O
LEFT JOIN ANIMAL_INS AS I
ON O.ANIMAL_ID = I.ANIMAL_ID
WHERE I.ANIMAL_ID IS NULL
ORDER BY ANIMAL_ID
'''

#### * ANMAL_INS와 ANIMAL_OUTS 테이블에서 입양간 기록은 있는데 보호소에 들어온
#### * 기록이 없는 동물의 ID를 찾아주면된다. 
#### * ANIMAL_OUTS 테이블에서 ID와 NAME을 갖고오고 LEFT JOIN으로 INS테이블을 JOIN한다.
#### * 이후 각각 테이블의 ID를 비교해주고 INS테이블의 ID정보가 없는 정보를 조회하고 ANIMAL_ID순으로 나열



### 프로그래머스 [MySQL] [JOIN] [있었는데요 없었습니다]
### Q.관리자의 실수로 일부 동물의 입양일이 잘못 입력되었습니다. 보호 시작일보다 입양일이 더 빠른 동물의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 시작일이 빠른 순으로 조회해야합니다.
---
```
SELECT I.ANIMAL_ID, I.NAME FROM ANIMAL_INS AS I 
LEFT JOIN ANIMAL_OUTS AS O
ON I.ANIMAL_ID = O.ANIMAL_ID 
WHERE I.DATETIME > O.DATETIME
ORDER BY I.DATETIME ASC
```
#### * 보호시작일과 입양일을 비교하고 그중 입양일의 datetime이 더빠른 동물을 조회한다.
#### * ins와 outs 테이블을 left join하고 여기서 id가 같다는 조건에서 ins의 datetime이 빠른 동물을 조회한다.(보호시작일 입양일 보다 무조건 빠르기 때문이다.)
