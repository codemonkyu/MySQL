
### 프로그래머스 [MySQL] [GROUP BY] [고양이와 개는 몇 마리 있을까]
---
#### Q. 동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이를 개보다 먼저 조회해주세요.

```
select animal_type, count(animal_type) as count
    from animal_ins
    group by animal_type
    order by animal_type asc
```

#### * select animal_type 으로 cat과 dog을 조회하고 count한다
#### * animal_type을 group by로 해서 cat과 dog로 구분해준다.

---
### 프로그래머스 [MySQL] [GROUP BY] [동명 동물 수 찾기]
---
#### Q. 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.

```
SELECT name, count(name) as count
    from animal_ins
    group by name having count(name) > 1
    order by name asc
```

#### * animal_ins으 name을 그룹화하고 having count(name)로 두번 이상 쓰인 것만 조회하도록 합니다.

---
### 프로그래머스 [MySQL] [GROUP BY] [입양 시각 구하기(1)]
---
#### Q. 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.

```
SELECT hour(datetime) as hour, count(hour(datetime)) as count
    from ANIMAL_OUTS
    where hour(datetime) >= 9 and hour(datetime) <= 19
    group by hour(datetime)
    order by hour(datetime)
```

