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
  - SELECT를 여러 개 쓰면 GROUP BY에도 동일하게 적어줘야 한다.
  - **CLOB 자료형은 데이터가 너무 커서 GROUP BY를 할 수 없다.**
- [x] HAVING
  - 집계가 끝난 이후 조건 검사를 하는 WHERE절이라 생각하자.
  
## 부조회(서브쿼리)(하의 질의)
- [x] 작성 순서, 실행 순서가 있는데 이를 바꿀 때 사용한다.
  1. WHERE절에 들어가야 하는 서브쿼리 : 비교할 때(평균과 같은 것, 조회수 최대값과 같은 것, 글을 작성한 적이 있는 사람 등
  2. FROM : 컬럼이 추가되어야 하는 집합
  3. SELECT : 반복되는 레코드마다의 값으로 비교해서 얻어야 하는 것
    - 서브쿼리를 SELECT에 쓰는 것은 좋지 않다.

## ALL, ANY
- ex) HIT < All(1, 2, 4, 6, 7)
  - 1,2,4,6,7 안에 있는 값보다 큰 조회수들
- ex) HIT < ANY(1, 2, 4, 6, 7)
  - 1,2,4,6,7 안에 있는 값중 ㅇ
  
## JOIN
- [x] **누가 주인공인지 생각하고 주인공한테 아우터 조인을 사용하자!** 
  - 곁다리로 붙는 애들은 주인공이 아니다. 
  - 주인공은 모든 컬럼, 모든 레코드가 다 나와야한다. 
  - 자식이 붙여지려면 집계되어서 붙여져야 한다.
  - **여러개를 조인할 때는 결과값이 주인이 되고 새로 조인을 하는 대상이 자식이 되어야 한다**
- [x] JOIN(INNER JOIN)
  - 이너조인은 관계가 있는 것들이 합쳐지는 연산이다.(가장 기본적인 조인)
  - 자식을 뽑고자 부모가 끼어들어간 것이기 때문에 결과는 무조건 자식이 기준이 기준이다.
  - 조인을 한 이후의 행의 개수는 자식에 맞춰진다.
- [x] LEFT/RIGHT/FULL JOIN(OUTER JOIN)
  - 아우터조인은 이너조인을 포함하면서 left/right/full을 할 수 있다.
  - 주인공 쪽에는 아우터를 꼭 쓴다.

## VIEW
- [x] 합쳐놓은 테이블이 있는 것처럼 읽기 전용인 가상의 테이블
  - **테이블을 합치는 작업에서 WHERE, ORDER BY는 넣을 수 없다**
  
  
## UNION
- [x] UNION
  - 같은 것을 합치면 하나는 사라진다.
- [x] UNION ALL
  - 같은 것이어도 사라지지 않고 합친다.
- [x] MINUS(여집합)
  - UNION을 했을 때와 반대의 결과이다.
  - 같은 것은 사라지고 다른 것만 출력된다. (첫 번째꺼가 기준임)
- [x] INTERSECT(교집합)
  - 같은 것만 출력한다.
