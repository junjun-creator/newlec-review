## 모델링(개념 모델링 이후 논리 모델링 시)
- 관계(릴레이션)이 1:n은 테이블을 갖지 못하고 n쪽으로 들어간다. n쪽으로 들어갈때는 관계명과 관계의 컬럼명이 같이 들어간다.
- 등록자가 누군지도 들어간다.
- 1:n이면 n이 자식이다. 1쪽이 먼저 만들어지기 때문에(데이터가 1쪽에 먼저 들어간다, ex. 회원이 있어야 게시글을 작성할 수 있다, 게시글이 있어야 댓글이 가능하다)
- m:n은 무조건 사이에 엔티티가 들어간다
- 대시 관계는 비식별관계, 실선은 식별관계

## 선 바꾸기
- Model - Model Properties - Notation
  - Logical/Physical 둘다 IE로 바꿔주기
- 선을 더블클릭 No Null로 바꾸면 0:n은 안되고 1:n이 된다(비회원은 글을 작성할 수 없고 회원만 글을 작성할 수 있다면!)

## 키
- [x] 기본키(Primary Key, 주키, 대표키)
- [x] 후보키
  - 테이블이 갖고 있던 컬럼 중에 기본키에 속하지 않는 모든 것들
  - 어떤 대상을 맞출 수 있는 힌트같은 것들
- [x] 대리키
  - 테이블에 속하지 않은 것들(ID, Code 등)
- [x] 복합키(슈퍼키)
- [x] 외래키


## 정규화
- [x] 1정규화
  - 하나의 속성에 두 개 이상의 값이 들어가냐? -> 들어가면 제1 정규화 필요
    - 하나의 컬럼(속성)에는 하나의 값(단일 값)을 갖도록 하는 과정
  - (erwin)분리되는 테이블은 자식으로

- [x] 2정규화
  - 

- [x] 3정규화
  - primary key가 아닌 속성들 중에서 중복이 일어날 수도 있는 것을 분리하는 과정
  - 속성에 새것이 아닌 또 올드버전이 들어와 있는가
    - 모든 속성은 이행적 함수 종속이 되지 말아야 한다.
  - (erwin)분리되는 테이블은 부모로
  - 키는 중복이 가능하다.
  
- [x] 함수적 종속이란?
  - 특정 키로부터 얻어낼 수 있는 속성
- [x] 이행적 함수 종속이란?
  - 다른 테이블의 키에 종속되어 있는 속성


## 제약조건
- 제약을 거는 이유는 무결성한 DB를 이용하기 위함이다.
- **도메인, 엔티티, 릴레이션** 제약조건으로 나뉜다.
- [x] 도메인
  - 테이블을 CREATE할 때 제약을 걸어준다.
  - NOT NULL은 꼭 채워야 한다.
  - 조회수, 등록일자같은 사용자가 입력하지 않지만 꼭 필요한 것들은 DEFAULT 제약조건을 사용한다. DEFAULT를 사용할 때는 NOT NULL을 사용하지 않는다.
    - 등록일자는 기본값으로 SYSTIMESTAMP를 적어준다.
  - CHECK조건은 양수, 음수, 패턴 등

- [x] 엔티티
  - PRIMARY KEY
    - CONSTRAINT NOTICE_ID_PK PRIMARY KEY(ID),
    - NOT NULL + UNIQUE = PRIMARY KEY

## 날짜 함수
- 현재 날짜를 뽑아낼 때는 SYSDATE 함수를 사용한다. 
  - SELECT SYSDATE FROM DUAL; -> 20/12/08(디폴트 값)
- 시, 분, 초까지 뽑아낼 때는 SYSTIMESTAMP 함수를 사용한다.
  - SELECT SYSTIMESTAMP FROM DUAL; -> 20/12/08(디폴트 값)
  
## 자동으로 ID AUTO_INCREMENT 방법
- SELECT EVENT_ID_SEQ.NEXTVAL FROM DUAL;
  - EVENT_ID_SEQ는 시퀀스이다.


## 산술연산자
- SELECT HIT + 1 FROM NOTICE;
- 문자에 숫자를 더하면 'invalid number' 에러가 난다

## 문자열 더하기 연산자
- || : 숫자를 문자열로 변환해서 더한다.
- + : 문자열을 숫자로 변환해서 더한다.

## 비교연산자
- [x] =, !=, ^=, <>, >, <, >=, <=, IS NULL, IS NOT NULL
  - !=, ^=, <> 모두 같지 않다는 의미이다. 
  - ANSI라는 기구에서 표준 SQL을 만들었는데 <>를 표준으로 사용하지만, 우리는 !=를 사용해야 한다. 역사적으로 깊기에.
  - 비교 연산자는 **WHERE 절**에서 사용한다.

## 관계연산자
- [x] NOT, AND, OR, BETWEEN, IN

## 패턴연산자
- [x] LIKE, %, _
  - SELECT * FROM MEMBER WHERE NAME LIKE '수%';
    - MEMBER 테이블에서 '수'로 시작하는 이름을 뽑는다. 글자 수의 제한은 없다.
  - SELECT * FROM MEMBER WHERE NAME LIKE '수_';
    - MEMBER 테이블에서 '수'로 시작하는 두 글자의 이름을 뽑는다.
  - SELECT * FROM MEMBER WHERE NAME LIKE '%수%';
    - MEMBER 테이블에서 '수'가 포함되는 이름을 뽑는다.

## 정규표현식
- [x] REGEXP_LIKE
  - WHERE REGEXP_LIKE(컬럼명, 
  - 여자 주민등록번호를 뽑을 때
    - SELECT * FROM MEMBER WHERE REGEXP_LIKE(BIRTHDAY, '^\d{6}-[24]\d{6}$');
  - 1980년대 5,7,9월생
    - SELECT * FROM MEMBER WHERE REGEXP_LIKE(BIRTHDAY, '^198\d-0[579]-\d{2}$');
- [x] REGEXP_REPLACE
  - 오라클 내장함수가 이 함수를 대체할 수 있다.
- [x] REGEXP_INSTR
  - 오라클 내장함수가 이 함수를 대체할 수 있다.
- [x] REGEXP_SUBSTR
  - 오라클 내장함수가 이 함수를 대체할 수 있다.

## ROWNUM 그리고 행 제한하기
- SELECT ROWNUM, * FROM MEMBER;
  - 이건 에러가 난다. * 은 모든 것을 의미하는데 ROWNUM을 같이 뽑으려고 하면 모든 것을 뽑는다는 것에 ROWNUM 때문에 위반이 된다.
- [x] ROWNUM의 맹점
  - SELECT ROWNUM, MEMBER.* FROM MEMBER WHERE ROWNUM **BETWEEN 1 AND 5**;
    - 이건 잘 나온다.
  - SELECT ROWNUM, MEMBER.* FROM MEMBER WHERE ROWNUM **BETWEEN 6 AND 10**;
    - 아무것도 출력이 되지 않는다.
    - ROWNUM은 FROM절이 아니라 WHERE절이 끝난 ROWNUM이 부여가 된다.
  - 서브쿼리로 해결하기
    - SELECT * FROM (SELECT ROWNUM NUM, MEMBER.* FROM MEMBER) WHERE NUM BETWEEN 1 AND 5;
      - NUM 별칭을 만든 이유는 바깥 SELECT문에서 ROWNUM을 사용하면 서브쿼리의 ROWNUM을 사용하는 것이 아니라 자기 자신의 ROWNUM을 사용하기 때문이다.
  
## SELECT절의 작성 및 실행 순서
- [x] 작성 순서
  - SELECT -> FROM -> WHERE -> GROUP BY -> HAVING -> ORDER BY
- [x] 실행 순서
  - FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY
## DISTINCT
- [x] 중복된 값을 제거한다.
  - SELECT DISTINCT HIT FROM NOTICE;
    - 중복된 조회수를 제거하고 추출한다.
    
## 집계함수(sum, min, max, count, avg)
- [x] SELECT COUNT(EMAIL) FROM MEMBER;
  - null이 있는 컬럼은 카운트하지 않는다.
  - count(\*)보다는 count(ID)로 검색하는 것이 낫다.
- [x] GROUP BY
- [x] HAVING
  - 집계가 끝난 이후 조건 검사를 하는 WHERE절이라 생각하자.
  
## 부조회(서브쿼리)
- [x] 작성 순서, 실행 순서가 있는데 이를 바꿀 때 사용한다.
  1. WHERE절에 들어가야 하는 서브쿼리 : 비교할 때(평균과 같은 것, 조회수 최대값과 같은 것, 글을 작성한 적이 있는 사람 등
  2. FROM : 컬럼이 추가되어야 하는 집합
  3. SELECT : 반복되는 레코드마다의 값으로 비교해서 얻어야 하는 것
