## SQL

자료 출처 : https://youtu.be/JE9OptIgFlY [SQL 기초 강의 - [AI 기업 데이터분석가] - 메타코드]

### SQL이란?

- structured Query Language, 구조화 질의어
- 관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리하기 위해 설계된 특수목적의 프로그래밍 언어
- 관계형 데이터베이스 관리 시스템에서 자료의 검색과 관리, 데이터베이스 스키마 생성과 수정, 데이터베이스 객체 접근 조정 관리를 위해 고안

--------------

### 데이터 불러오기  (SELECT)

```mysql
# 특정 컬럼을 불러올 때
select 컬럼이름1, 컬럼이름2
from 테이블 이름
```

```mysql
# 모든 컬럼을 불러올 때
select *
from 테이블

# sql은 대소문자를 구분하지 못한다.
```

``` mysql
# 중복 제거된 컬럼을 조회
select distinct	컬럼이름1, 컬러이름2
from 테이블 이름
```

```mysql
# 컬럼에 별명을 붙여서 조회
select 컬럼이름1 (as) 별명1, 컬럼이름2 (as) 별명2
from 테이블 이름
```

```mysql
# 결과 행 개수 제한하여 조회
select 컬럼이름1, 컬럼이름2
from 테이블 이름
limit N	
```



### 데이터 필터링 (WHERE)

```mysql
select 컬럼이름1, 컬러이름2
from 테이블 이름
where 조건1	
```

|                          비교연산자                          |                             설명                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| =<br/><> , !=<br/><<br/><=<br/>><br/>>=<br/>BETWEEN<br/>IS NULL | 같음<br/>같지 않음<br/>보다 작음<br/>보다 작거나 같음<br/>보다 큼<br/>보다 크거나 같음<br/>지정된 두 값 사이에 있음<br/>Null 값임 |

```mysql
# 숫자형 데이터 조건 걸기
select *
from 테이블 이름
where 비교컬럼이름 = 숫자
```

```mysql
# 문자형 데이터 조건 걸기
select *
from 테이블 이름
where 비교컬럼이름 = '문자'
```

```mysql
# 여러조건을 모두 만족하는 데이터 조회하기
select *
from 테이블 이름
where 조건1 AND 조건2
```

```mysql
# 여러조건을 하나 이상 만족하는 데이터 조회하기 
select *
from 테이블 이름
WHERE 조건1 OR 조건2
```

```mysql
# 여러조건을 하나 이상 만족하는 데이터 조회하기2
select *
from 테이블 이름
WHERE 비교컬럼이름 (NOT) IN (조건1, 조건2)
```

```mysql
# 특정한 패턴을 가지는 값을 조회할 때
select *
from 테이블 이름
WHERE 컬럼이름 LIKE
패턴
```

| LIKE Operator |           Description            |
| :-----------: | :------------------------------: |
|      ‘a%      |            ‘a’로 시작            |
|     ‘%a’      |           ‘a’로 끝나는           |
|    ‘%sl%'     |          ‘sl’이 포함된           |
|     ‘_m%'     |       두번째 글자가 ‘m’인        |
|    'a_%_%'    | ‘a’로 시작하고 글자수가 3개 이상 |
|     ‘t%a'     |   ‘t’로 시작하고 ‘a’로 끝나는    |



### 데이터 정렬하기(ORDER BY)

```mysql
# 오름차순으로 정렬하여 조회
SELECT *
FROM 테이블이름
ORDER BY 컬럼이름1 (ASC)    # ascending 오름차순
```

```mysql
# 내림차순으로 정렬하여 조회
SELECT *
FROM 테이블이름
ORDER BY 컬럼이름1 DESC    # decending 내림차순
```



### 여러가지 함수(CASE WHEN)

```mysql
SELECT CASE WHEN 조건1 THEN 결과값1
WHEN 조건2 THEN 결과값2
ELSE 결과값3
END
FROM 테이블이름
```

```mysql
SELECT 함수(컬럼이름1), 함수(컬럼이름2)
FROM 테이블이름
```



- 집계 함수

SUM() : 합계

COUNT() : 행 개수

MIN() :  최소

MAX() : 최대

AVG() : 평균

- 숫자함수

TRUNCATE(,n) : 소수점 n자리까지 표시

ROUND(,n) : 소수점 자리 지정하여 반올림
CEIL() : 올림

FLOOR() : 내림

ABS() : 절대값

SIGN() : 양수면 1, 음수면 -1, 0이면 0 (시그모이드)

- 문자함수

LENGTH() : 문자열 길이 반환

TRIM() : 앞, 뒤 공백 제거

UPPER(), LOWER() : 모두 대/소문자로

LEFT(,n) : 왼쪽에서 n번째

RIGHT(,n) : 오른쪽에서 n번째

REPLACE() : 특정 패턴 찾아서 변경

LPAD(), RPAD() : 특정 글자 반복

SUBSTRING() : 특정 위치에서 자르기
CONCAT() : 문자 붙이기

CONCAT_WS() :  문자사이에 값 넣기

- 날짜함수

CURDATE() : 현재 날짜 반환
CURTIME() :현재 시간 반환
NOW() : 현재 날짜&시간 반환
YEAR() : 연도 반환
MONTH() : 월 반환
DAY() : 일 반환
LAST_DAY() : 해당 월의 마지막 일
WEEKDAY() : 요일 값 반환(월요일 : 0)
DAYNAME() : 요일 이름 반환

ADDDATE() :시간/날짜 더하기
SUBDATE() : 시간/날짜 빼기
DATEDIFF() : 두 시간/날짜 일 차이
TIMEDIFF()  : 두 시간/날짜 시간 차이

- DATE_FORMAT() - 명령어는 대소문자 구분
  %Y : 4자리 년도
  %y : 2자리 년도
  %M : 긴 월(영문)
  %b : 짧은 월(영문)
  %W : 긴 요일 이름(영문)
  %a : 짧은 요일 이름(영문)
  %i : 분
  %T : hh:mm:SS
  %m : 숫자 월 ( 두자리 )
  %c :  숫자 월(한자리는한자리)
  %d : 일자 (두자리)
  %e : 일자(한자리는 한자리)
  %I : 시간 (12시간)
  %H : 시간(24시간)
  %r : hh:mm:ss AM,PM
  %S : 초



### 데이터 그룹화

```mysql
# 특정 컬럼을 기준으로 그룹화
SELECT 그룹화_기준_칼럼이름1, 그룹화_기준_칼럼이름2, 집계함수
FROM 테이블이름
GROUP BY 그룹화_기준_칼럼이름1, 그룹화_기준_칼럼이름2
```

```mysql
# 그룹화 & 요약한 컬럼을 기준으로 조건 걸기
SELECT 그룹화_기준_칼럼이름1, 그룹화_기준_칼럼이름2, 집계함수
FROM 테이블이름
GROUP BY 그룹화_기준_칼럼이름1, 그룹화_기준_칼럼이름2
HAVING 집계함수 조건
```



### 데이터 분할 & 분석(순위함수)

```mysql
# 순위함수를 이용하여 순위 매기기
SELECT 컬럼이름, 순위함수() OVER (ORDER BY 컬럼이름)
FROM 테이블이름
```

순위함수

RANK() : 중복 순위 적용, 다음 순위가 중복 순위 적용 후 순위
				Ex) 1, 2, 2, 4
DENSE_RANK() : 중복 순위 적용, 다음 순위는 중복 순위 적용 +1
				Ex) 1, 2, 2, 3

```mysql
# 이전 행, 다음 행 가져오기
SELECT 컬럼이름, 이동함수(컬럼이름, offset) OVER (ORDER BY 컬럼이름)
FROM 테이블이름
```

이동함수

LAG() 이전 행 가져오기
LEAD() 다음 행 가져오기

```mysql
# partition by
SELECT 컬럼이름, 함수() OVER (PARTITION BY 컬럼이름 [ORDER BY 컬럼이름])
FROM 테이블이름
```

```mysql
# Frame절
SELECT 컬럼이름, 함수() OVER (ORDER BY 컬럼이름
							ROWS BETWEEN [FRAME절] AND [FRAME절])
FROM 테이블이름
```

Frame절 명령어

CURRENT ROW : 현재 로우
n PRECEDING :  n번째 뒤의 로우
n FOLLOWING : n번째 앞의 로우
UNBOUNDED PRECEDING : 가장 첫번째 로우
UNBOUNDED FOLLOWING : 가장 마지막 로우

### 테이블합치기

```
# join (옆으로 합침)
SELECT 컬럼이름1, 컬럼이름2
FROM 테이블이름1 JOIN 테이블이름2
ON 테이블이름1.컬럼A = 테이블이름2.컬럼A
```

join 종류

INNER JOIN : 사실상 교집합

LEFT JOIN : LEFT를 기준으로 LEFT나타내고 RIGHT의 LEFT와 교집합부분을 나타내줌

RIGHT JOIN : LEFT JOIN의 반대 개념이라고 보면 됨

```
#Union (아래로)
 union all : 아래로 통째로 붙임
 union : 아래로 붙이되 중복 허용하지 않음(위 기준으로 중복되지 않은 것만 아래로 합침)
```



### 서브쿼리

```mysql
# 다중 열 테이블 서브쿼리
SELECT 서브쿼리이름.칼럼1, 서브쿼리이름.컬럼2
FROM (서브쿼리) 서브쿼리이름
```

```mysql
# 단일 열 혹은 단일 값 서브쿼리
SELECT 칼럼1, 칼럼2
FROM 테이블이름
WHERE 칼럼1 in (서브쿼리)
```

### 임시테이블

```mysql
# view 생성
CREATE VIEW 뷰이름
AS (쿼리)
```

```mysql
# 삭제
drop view 뷰이름
```

```mysql
# with로 임시테이블 생성
WITH 임시테이블이름 AS(
임시테이블쿼리
)
임시테이블을 사용하는 메인쿼리
```



### 테이블 핸들링

```mysql
테이블 생성
CREATE TABLE 테이블이름 (
컬럼이름1 데이터타입,
컬럼이름2 데이터타입
);
```

```mysql
# 테이블 제거
DROP TABLE 테이블이름;
```

```mysql
ALTER TABLE 테이블이름
RENAME TO 바꿀테이블이름, 							← 테이블 이름
변경
ADD COLUMN 추가컬럼이름 데이터타입 				 ← 컬럼 추가
CHANGE COLUMN 기존컬럼이름 바꿀컬럼이름 데이터타입, 	 ← 컬럼 이름 변경
CHANGE COLUMN 컬럼이름 컬럼이름 바꿀데이터타입 , 	  ← 데이터타입 변경
DROP COLUMN 컬럼이름 ; 							 ← 컬럼 삭제
```

```mysql
# 특정 컬럼 데이터를 추가
INSERT INTO 테이블이름
(컬럼이름1, 컬럼이름2)
VALUES(입력값1, 입력값2); 
```

```mysql
# 전체 컬럼의 데이터를 추가
INSERT INTO 테이블이름
VALUES(입력값1, 입력값2, 입력값3);
```



```mysql
# 데이터 삭제
DELETE FROM 테이블이름
WHERE 조건; 
```

```mysql
# 데이터 수정
UPDATES 테이블이름
SET 컬럼이름1 = 입력값1, 컬럼이름2 = 입력값2
WHERE 조건;
```

핸들링 제약조건

- AUTO_INCREMENT : 행 추가 되면 자동으로 1씩 증가(Numbering)
- NOT NULL : NULL 값 불허용

- UNIQUE : 열에 있는 모든 값들은 중복되면 안됨

- PRIMARY KEY : 해당 열이 Primary Key가 된다는 뜻.(Not null & Unique)

- DEFAULT : 사용자가 지정하지 않으면 입력되는 기본 값