# ORACLE 계정생성

## 1) cmd에서 접속하기
> sqlplus 로 접속하시면 user-name과 password가 나오는데<br>
> user-name은 system, password는 oracle 설치 시 입력하신 비밀번호로 입력해주시면 됩니다.<br>
> (password 입력할 때, cmd창에서 표시가 안되는게 정상입니다.)<br>
```
sh-4.2$ sqlplus           

SQL*Plus: Release 19.0.0.0.0 - Production on Mon Mar 27 16:29:25 2023
Version 19.9.1.0.0

Copyright (c) 1982, 2019, Oracle.  All rights reserved.

Enter user-name: system
Enter password: 
Last Successful login time: Wed Mar 22 2023 15:24:13 +09:00
```

## 2) 관리자권한으로 접속
> 정상적으로 접속을 하시면, 관리자 권한으로 접속해야합니다.<br>
```
SQL> conn/as sysdba
Connected.
```

## 3) 계정 생성
> [id] [pw]는 자신이 생각하는 id와 pw로 입력하시면 됩니다.<br>
> * create user [id] identified by [pw];<br>
```
SQL> create user hr identified by lbg111;
User created.
SQL>
```

## 4) 권한 부여
> 계정을 생성 한 후에 권한을 줘야합니다.<br>
> connect(접속 권한), resource(객체 및 데이터 조작 권한), dba를 설정했습니다.<br>
> * grant [권한] to [id];<br>
> * grant connect, resource, dba to [id];<br> 
```
SQL> grant connect, resource, dba to hr;
Grant succeeded.
SQL>
```

## 5) commit
> 지금까지의 변경 사항들을 적용합니다.
```
S
Commit complete.
```

## 6) 계정 생성 확인
> 아래 처럼 HR이 생성되어있는 걸 확인 할 수 있습니다.<br>
> * select * from all_users;<br>
```
SQL> select username from all_users where username='HR';

USERNAME
--------------------------------------------------------------------------------
HR

1 rows selected.

SQL> 
```

## + 계정 권한 취소
> * revoke [권한] from [id];
```
SQL> revoke connect, resource, dba to hr;

Revoke succeeded.
```

## + 계정 삭제
> * drop user [id] cascade;
```
SQL> drop user hr cascade;

User dropped.
```
