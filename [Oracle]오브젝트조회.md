| Object | Command  |
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
| column comment 쿼리|  select * from all_col_comments where table_name='테이블명'
