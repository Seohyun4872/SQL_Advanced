# SQL_ADVANCED 2주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=_JURyg_KzHE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=7
https://www.youtube.com/watch?v=6qkPy7RfLqQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=8
https://www.youtube.com/watch?v=WWAFAm9op2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=9
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_2nd_TIL

### 3장 SQL 기본 문법
#### 01. 기본 중에 기본 SELECT ~ FROM ~ WHERE
#### 02. 좀 더 깊게 알아보는 SELECT문
#### 03. 데이터 변경을 위한 SQL문


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 기본 중에 기본 SELECT ~ FROM ~ WHERE

<!-- 기본적인 SQL 문법에 관해 배우게 된 점을 적어주세요. -->

<!-- 이번 챕터에서 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 3~4장 제출해 주세요. -->

<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->

> **확인문제: 다음 SQL문의 빈칸에 들어갈 WHERE절의 문법으로 틀린 것을 고르세요.**

```sql
SELECT *
FROM table_name
WHERE ________;
```

보기는 아래와 같습니다.
```
1. mem_number == 4
2. mem_number >= 4
3. mem_number <= 4
4. mem_number = 4
```

```
1번  
SQL에서는 비교 연산자에 ==를 사용하지 않고, 그냥 = 를 사용함!!(파이썬 등과 헷갈리지 말기!!)
```


## 2. 좀 더 깊게 알아보는 SELECT문

<!-- ORDER BY절과 GROUP BY절에 관해 배우게 된 점을 적어주세요. -->
**order by**
Order by 절은 select랑 같이 보통 쓰이면서, 조회결과가 일정한 기준의 순서로 출력되도록 하는 함수  
특정컬럼을 기준으로 오름차순은 ASC, 내림차순은 DESC를 사용하고 아무것도 없으면 default로 ASC로 출력됨.  
```
EX) SELECT *  
FROM student  
ORDER BY grade ASC, name ASC;  
> 성적을 기준으로 오름차순 정렬을 먼저하고, 그 중 동일 성적이 있다면 이름 기준으로 오름차순 정렬하도록 출력하는 것  
```

**GROUP BY**
GROUP BY절은 단순히 결과를 정렬하는 것이 아니라, 같은 값을 가진 행들을 하나의 그룹으로 묶는 기능임.  
그룹으로 묶어줘야 하기에 order by랑은 다르게 주로 집계함수들(SUM, AVG, MIN 등)과 함께 보통 사용됨.  
```
EX)
SELECT department, COUNT(*)  
FROM employee  
GROUP BY department;  
> department가 같은 행들끼리 묶어서 각 부서별 몇명이 있는지 계산  
> 즉, 개별 행이 아닌 그룹별 요약결과를 group by를 통해 확인 가능한 것.  
```

> **확인문제: 다음 표는 주요 집계함수를 정리한 것입니다. 각 설명에 해당하는 올바른 함수명을 기호에 맞게 작성하세요.**

| 함수명 | 설명 |
|--------|------|
| SUM() | 합계를 구합니다. |
| (ㄱ) | 평균을 구합니다. |
| (ㄴ) | 최소값을 구합니다. |
| MAX() | 최대값을 구합니다. |
| (ㄷ) | 행의 개수를 셉니다. |
| (ㄹ) | 행의 개수를 셉니다 (중복은 1개만 인정). |

```
여기에 답을 적어주세요!
(ㄱ) AVG()
(ㄴ) MIN()
(ㄷ) COUNT()
(ㄹ) COUNT(DISTINCT __ )
```


## 3. 데이터 변경을 위한 SQL문

<!-- INSERT문, UPDATE문, DELETE문에 관해 배우게 된 점을 적어주세요. -->
```
INSERT: 새로운 데이터를 데이터베이스에 저장할 때 사용함.
INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);
```
```
UPDATE: 이미 저장되어 있는 기존 데이터를 수정할 때 사용  
UPDATE table_name
SET column1 = value1
WHERE condition;
> SET으로 수정할 값을 지정하고, WHERE 조건을 사용하여 특정 행만 수정하게 조건을 걸어두는 건데 where을 쓰지 않을 시 모든 행이 수정될 수 있음.
```
```
DELETE: 테이블에 저장된 데이터를 삭제할 때 사용  
DELETE FROM table_name  
WHERE condition;  
> 테이블 구조는 그대로 남음. 
```

> **확인문제: 다음이 설명하는 SQL이 무엇인지 쓰세요.**

```
* 데이터를 삭제합니다.
* DELETE와 동일한 효과를 내지만 속도가 무척 빠릅니다.
* 삭제 후에 빈 테이블이 남아 있습니다.
```

```
TRUNCATE  
TRUNCATE TABLE table_name; 의 형태로 사용

특징    
* 모든 행을 빠르게 삭제  
* DELETE보다 성능이 빠름  
* 테이블 구조(컬럼, 테이블)는 유지  
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week2_db;

-- 2. 사용할 데이터베이스 선택
USE week2_db;

-- 4. 테이블 생성
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(20),
    major VARCHAR(30),
    grade INT,
    age INT,
    gpa DECIMAL(3,2),
    admission_year INT
);

-- 5. 데이터 삽입
INSERT INTO students VALUES
(1, '진아', 'Statistics', 1, 19, 3.85, 2024),
(2, '혜인', 'Computer Science', 2, 20, 3.20, 2023),
(3, '규서', 'Business', 3, 22, 2.95, 2022),
(4, '규영', 'Statistics', 4, 23, 3.60, 2021),
(5, '철원', 'Economics', 2, 21, 3.75, 2023),
(6, '예운', 'Computer Science', 1, 19, 3.10, 2024),
(7, '민서', 'Statistics', 3, 22, 3.45, 2022);
```
## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.

1. 모든 학생의 정보를 조회하시오.

   
2. 전공이 'Statistics'인 학생을 조회하시오.
4. 현재 students 테이블에 존재하는 서로 다른 전공의 개수를 구하시오.
5. 나이가 20 이상이고 GPA가 3.5 이상인 학생을 조회하시오.
6. students 테이블에 본인의 정보를 직접 INSERT 하시오. (INSERT 실행 후, 데이터가 정상적으로 추가되었는지 확인할 수 있도록 조회 결과까지 포함하여 캡처하시오.)

<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->

### 🎉 수고하셨습니다.







