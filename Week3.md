# SQL_ADVANCED 3주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=1YmWy-7-OhQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=10
https://www.youtube.com/watch?v=tuQFkzjqEGw&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=11
https://www.youtube.com/watch?v=IOCsreDYqFE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=12
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_3rd_TIL

### 4장 SQL 고급 문법
#### 01. MySQL의 데이터 형식
#### 02. 두 테이블을 묶는 조인
#### 03. SQL 프로그래밍 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. MySQL의 데이터 형식

<!-- MySQL의 데이터 형식에 관해 배우게 된 점을 적어주세요. -->

> **확인문제: 다음 보기에서 데이터 형식의 변환에 사용되는 함수를 2개 고르세요.**

보기는 아래와 같습니다.
```
CONVERT() / DATA() / CAST() / MOVE() / TYPE() / SUM() / AVG() / CURRENT_DATE()
```

```
CONVERT(), CAST() 
```


## 2. 두 테이블을 묶는 조인

<!-- 두 테이블을 묶는 조인에 관해 배우게 된 점을 적어주세요. -->
1. INNER JOIN (가장 기본)
양쪽 테이블에 모두 존재하는 데이터만 조회하기 때문에 공통 데이터만 출력됨. 
```
SELECT *
FROM 학생 A
INNER JOIN 성적 B
ON A.학번 = B.학번;
```


2. LEFT JOIN
왼쪽 테이블 기준 + 오른쪽은 있으면 붙임
```
SELECT *
FROM 학생 A
LEFT JOIN 성적 B
ON A.학번 = B.학번;
```
ex) 학생은 모두 나오고, 성적 없으면 NULL

3. RIGHT JOIN
오른쪽 테이블 기준
```
SELECT *
FROM 학생 A
RIGHT JOIN 성적 B
ON A.학번 = B.학번;
```
ex) 성적은 모두 나오고, 학생 정보 없으면 NULL

4. FULL OUTER JOIN
양쪽 테이블 모두 포함시켜서, 한쪽 테이블에만 있어도 전부 출력됨. 
```
SELECT *
FROM 학생 A
FULL OUTER JOIN 성적 B
ON A.학번 = B.학번;
```

5. CROSS JOIN
모든 경우의 수 (곱집합)
```
SELECT *
FROM 학생
CROSS JOIN 과목;
```
학생 × 과목 모든 조합 생성하기 때문에, 데이터 많으면 폭발적으로 증가함을 유의해야 함.   


> **확인문제: 다음 SQL은 회원으로 가입만 하고, 한 번도 구매한 적이 없는 회원의 목록을 조회하는 쿼리입니다. 빈칸에 들어갈 가장 적절한 구문을 고르세요..**

```sql
SELECT DISTINCT M.mem_id, B.prod_name, M.mem_name, M.addr
  FROM member M
    LEFT OUTER JOIN buy B
    ON M.mem_id = B.mem_id
  __________
  ORDER BY M.mem_id;
```
보기는 아래와 같습니다.
```
1. JOIN B.prod_name IS NULL
2. LIMIT B.prod_name IS NULL
3. HAVING B.prod_name IS NULL
4. WHERE B.prod_name IS NULL
```
```
4번
현재 leftjoin으로 member M테이블과 buy B 테이블을 묶어줬기 때문에 멤버는 있는데 두 테이블에 모두 있는데 구매기록이 없는 경우는 null인 상태로 합쳐지게 됨.
그렇기에 해당 테이블의 출력조건을 where로 prod_name이 null인 경우로 설정하게 된다면 한번도 구매한 적 없는 회원목록 조회가 가능해짐
(나머지 답들이 틀린 이유)  
1. JOIN ... → 문법적으로 틀림
2. LIMIT ... → 개수 제한, 조건 아님
3. HAVING ... → 그룹 함수 이후 사용 (여기선 부적절)
```

## 3. SQL 프로그래밍 

<!-- IF문, CASE문, WHILE문, 동적 SQL에 관해 배우게 된 점을 적어주세요. -->
**IF**
```
IF 조건 THEN
   실행문
ELSE
   실행문
END IF;
```

**Case**: select문 안에서 조건별 값 치환 가능  
```
CASE
  WHEN 조건 THEN 값
  ELSE 값
END
```
> when이 보통 케이스문 내부에서 이렇게 같이 사용됨.

**While**: 반복적 처리를 SQL내에서 진행 가능  
```
WHILE 조건 DO
   실행문
END WHILE;
```

**동적 SQL(Dynamic SQL)**: 쿼리를 문자열로 만들어 실행하는 방식  
- 상황에 따라 SQL 구조 자체를 바꿀 수 있음  
```
SET @sql = 'SELECT * FROM ' + 테이블명;
PREPARE stmt FROM @sql;
EXECUTE stmt;
```

> **확인문제: 다음은 CASE 문의 형식입니다. 빈칸에 들어갈 가장 적절한 명령어를 보기에서 고르세요..**

```sql
CASE
    (1) 조건 THEN
        SQL문장들1
    ELSE
        SQL문장들4
END (2);
```

보기는 아래와 같습니다.
```
WHEN / THEN / CURRENT / DATE / TIME / IF / END IF / CASE
```

```
여기에 답을 적어주세요!
(1) WHEN
(2) CASE
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week3_db;

-- 2. 사용할 데이터베이스 선택
USE week3_db;

-- 3. 기존 테이블 삭제 (초기화용)
DROP TABLE IF EXISTS orders;
DROP TABLE IF EXISTS customers;

-- 4. 테이블 생성 (조인 실습용)
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(20),
    signup_date_str VARCHAR(8) 
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,           
    order_date_str VARCHAR(8), 
    amount_str VARCHAR(10)     
);

-- 5. 데이터 삽입
INSERT INTO customers VALUES
(1, '진아', '20240218'),
(2, '혜인', '20230302'),
(3, '규서', '20220315'),
(4, '규영', '20210401'),
(5, '철원', '20230909'),
(6, '예운', '20240201'),
(7, '민서', '20220320'),
(8, '광윤', '20240105'); -- 주문 없는 고객(외부 조인용)

INSERT INTO orders VALUES
(101, 1, '20240220', '12000'),
(102, 1, '20240303', '30000'),
(103, 2, '20240111', '15000'),
(104, 3, '20221201', '9000'),
(105, 5, '20231111', '20000'),
(106, 7, '20220707', '5000'),
(107, 99, '20240210', '7000'); -- 고객 테이블에 없는 customer_id (외부 조인용)
```

## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.
<img width="576" height="439" alt="image" src="https://github.com/user-attachments/assets/85eefcbc-8c62-439e-ac82-355d2d73c399" />
<img width="757" height="660" alt="image" src="https://github.com/user-attachments/assets/7c6ade98-102b-4245-bfc1-e3f0424bfacf" />
> 테이블 생성 완

1. **데이터 형식 변환**
   - orders 테이블의 `order_date_str`을 DATE 형식으로 변환하여 조회하시오.
   (힌트: STR_TO_DATE 사용)
<img width="1045" height="757" alt="image" src="https://github.com/user-attachments/assets/8ab47cc7-d27c-473b-a92d-0f84a0006cca" />


2. **데이터 형식 변환**
   - orders 테이블의 `amount_str`을 숫자형으로 변환하여 조회하시오.
<img width="713" height="616" alt="image" src="https://github.com/user-attachments/assets/3242ab7f-4680-4d0e-847e-b0e7f3c39f7b" />
*alter를 활용하여 amount_str의 형식을 변환하기  


3. **내부 조인 (INNER JOIN)**
   - customers와 orders를 customer_id 기준으로 내부 조인하여
     고객 이름(name)과 주문 번호(order_id)를 함께 조회하시오.
<img width="751" height="725" alt="image" src="https://github.com/user-attachments/assets/a4bebfc8-cf79-4a7a-b58a-c84050ddd547" />
겹치는 걸 가져와야 하니까 inner join 사용  


4. **외부 조인 (LEFT JOIN)**
   - customers를 기준으로 LEFT JOIN을 수행하여,
     주문이 없는 고객도 함께 조회하시오.
<img width="794" height="796" alt="image" src="https://github.com/user-attachments/assets/5b3e230d-d48a-4b80-97b1-4598ce0062a1" />


5. **스토어드 프로시저 (IF문 사용)**
   - 입력받은 금액이 10000 이상이면 '고액 주문',
     그렇지 않으면 '일반 주문'을 출력하는
     프로시저를 생성하시오.
   - 생성 후 CALL로 실행 결과를 확인하시오.
<img width="1030" height="607" alt="image" src="https://github.com/user-attachments/assets/0487f280-72bf-4925-a02a-e6f4e7f11808" />
<img width="801" height="393" alt="image" src="https://github.com/user-attachments/assets/b81bcc2f-b786-44a8-a40a-c1a275c10c15" />
<img width="612" height="333" alt="image" src="https://github.com/user-attachments/assets/61854d66-7c4e-461d-a91b-a987ffc2c2fa" />


<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->


### 🎉 수고하셨습니다.







