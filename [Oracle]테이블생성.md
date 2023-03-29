# 오라클 테이블 만드는 방법 (CREATE, PK, INDEX, COMMENT)
## 1. 테이블 명 / 컬럼 명
> - 테이블, 컬럼 명의 길이는 30byte 문자 (Oracle 12c R2 부터는 128byte)
> - 문자(영문, 한글), 숫자, 특수문자(_, $, #)만 가능
> - 반드시 문자로 시작

## 2. 데이터 타입
> - NUMBER(4) : 4자리의 가변 길이 정수
> - NUMBER(7,2) : 7자리의 가변 길이 정수와 2자리의 가변길이 소수
> - VARCHAR2(10) : 10byte의 가변 길이 문자

## 3. 기본 값
> - 테이블에 값이 입력(INSERT) 될 때 값이 없으면 기본으로 생성되는 값
> - DEFAULT [값(문자, 숫자, 날짜)], 사용하지 않으면 생략 가능

## 4. NULL 허용 여부
> - 기본 값은 NULL 허용이며, NOT NULL 선언 시 해당 컬럼은 NULL 값을 허용하지 않음

## ※ 예제
> 테이블 생성
```
CREATE TABLE emp 
( 
    empno       NUMBER(4)	NOT NULL,
    ename       VARCHAR2(10),
    job         VARCHAR2(9),
    mgr         NUMBER(4),
    hiredate    DATE,
    sal         NUMBER(7,2),
    comm        NUMBER(7,2),
    deptno      NUMBER(2)
);
```
> 테이블 설명 (COMMENT)
```
ALTER TABLE emp ADD CONSTRAINT emp_pk PRIMARY KEY (empno);
```
> 컬럼 설명 (COMMENT)
```
COMMENT ON COLUMN emp.empno IS '사원번호';
```
> 인덱스 생성
> * CREATE INDEX [인덱스명] ON [테이블명]([컬럼명,컬럼명...])
```
CREATE INDEX emp_idx01 ON emp(job, deptno);
```
> 테이블 생성 (PK, COMMENT 포함)
```
CREATE TABLE emp 
( 
    empno       NUMBER(4)	NOT NULL,
    ename       VARCHAR2(10),
    job         VARCHAR2(9),
    mgr         NUMBER(4),
    hiredate    DATE,
    sal         NUMBER(7,2),
    comm        NUMBER(7,2),
    deptno      NUMBER(2),	
    CONSTRAINT emp_pk PRIMARY KEY (empno)
);

COMMENT ON TABLE emp IS '사원정보';

COMMENT ON COLUMN emp.empno IS '사원번호';
COMMENT ON COLUMN emp.ename IS '성명';
COMMENT ON COLUMN emp.job IS '직군';
COMMENT ON COLUMN emp.mgr IS '직속상사';
COMMENT ON COLUMN emp.hiredate IS '입사일';
COMMENT ON COLUMN emp.sal IS '급여';
COMMENT ON COLUMN emp.comm IS '보너스';
COMMENT ON COLUMN emp.deptno IS '부서코드';
```
