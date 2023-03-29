## 1. Object 조회 Query
| 조회Object | Query  |
|:--|---------|
| User 확인|  select * from all_users;|
| 등록된 User 목록 보기|  select username, user_id from dba_users order by username;|
| User가 소유한 모든 테이블 보기|  select table_name from user_tables;|
| 사용자 정보 확인|  select username, default_tablespace,temporary_tablespace from dba_users;|
| 오브젝트 조회|  select * from all_objects where object_name like '명';|
| 테이블 조회|  select * from all_tables where table_name like '명';|
| 시퀀스 정보 보기|  select * from user_sequences;|
| 시노님 조회|  select * from all_synonyms where synonym_name='명';|
| 테이블 인덱스 정보 조회|  select * from all_ind_columns where table_name='테이블명';|
| 테이블의 컬럼 정보 조회|  select * from all_tab_columns where table_name='테이블명';|
| table comment 쿼리|  select * from all_tab_comments where table_name='테이블명';|
| column comment 쿼리|  select * from all_col_comments where table_name='테이블명'|
| 테이블 생성 스크립트 확인|SELECT TO_CHAR(DBMS_METADATA.GET_DDL('TABLE','테이블')) SCRIPT FROM DUAL;|
| 인덱스 생성 스크립트 확인|SELECT TO_CHAR(DBMS_METADATA.GET_DDL('INDEX','INDEX_NM')) SCRIPT FROM DUAL;|
| 프로시저 생성 스크립트 확인|SELECT TO_CHAR(DBMS_METADATA.GET_DDL('PROCEDURE','PROC_NM')) SCRIPT FROM DUAL;|
| 시퀀스 생성 스크립트 확인|SELECT TO_CHAR(DBMS_METADATA.GET_DDL('SEQUENCE','SEQ_NM')) SCRIPT FROM DUAL;|
## 2. 생성스크립트 파일로 저장하기
```
set pagesize 0
set long 90000
set feedback off
set echo off 

spool board.sql 

SELECT DBMS_METADATA.GET_DDL('TABLE', U.OBJECT_NAME) FROM USER_OBJECTS U WHERE OBJECT_TYPE='TABLE';
SELECT DBMS_METADATA.GET_DDL('INDEX', U.OBJECT_NAME) FROM USER_OBJECTS U WHERE OBJECT_TYPE='INDEX';
SELECT DBMS_METADATA.GET_DDL('SEQUENCE', U.OBJECT_NAME) FROM USER_OBJECTS U WHERE OBJECT_TYPE='SEQUENCE';
SELECT DBMS_METADATA.GET_DDL('PROCEDURE', U.OBJECT_NAME) FROM USER_OBJECTS U WHERE OBJECT_TYPE='PROCEDURE';

spool off
```
