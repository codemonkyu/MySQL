
### 프로그래머스 [MySQL] [SUM,MAX,MIN] [최댓값 구하기]
---
#### Q. 가장 최근에 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.

```
SELECT MAX(datetime)
from ANIMAL_INS
```

---
### 프로그래머스 [MySQL] [SUM,MAX,MIN] [최솟값 구하기]
---
#### Q.동물 보호소에 가장 먼저 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.

```
SELECT min(datetime)
from animal_ins
```

---
### 프로그래머스 [MySQL] [SUM,MAX,MIN] [동물 수 구하기]
---
#### Q. 동물 보호소에 동물이 몇 마리 들어왔는지 조회하는 SQL 문을 작성해주세요.

```
SELECT count(*) from ANIMAL_INS
```

#### 1. COUNT(ANIMAL_ID)도 가능하다.

---
### 프로그래머스 [MySQL] [SUM,MAX,MIN] [중복 제거하기]
---
#### Q. 동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 SQL 문을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 중복되는 이름은 하나로 칩니다.

```
select count(distinct name) as count
    from animal_ins
```

#### 1. distinct name으로 이름을 구별 , count()로 이름 몇개인지 파악
#### 2. as count로 표시
