# 윈도우 소켓 프로세스 확인 및 강제종료 방법
## 1. 윈도우 소켓 프로세스 확인
> netstat : 프로토콜 통계와 현재 TCP/IP 네트워크 연결을 표시<br>
>  > -a    모든 연결 및 수신 대기 포트를 표시합니다. <br>
>  > -n    주소 및 포트 번호를 숫자 형식으로 표시합니다. <br>
>  > -o    각 연결의 소유자 프로세스 ID를 표시합니다. <br>
> * netstat -ano | findstr :포트번호
```
C:\Users\lbg12>netstat -ano | findstr :8080
  TCP    0.0.0.0:8080           0.0.0.0:0              LISTENING       38556
  TCP    [::]:8080              [::]:0                 LISTENING       38556
```
## 2. 강제종료
>  taskkill : 프로세스 ID(PID) 또는 이미지 이름으로 작업을 종료<br>
>  >  /PID  프로세스_ID      종료할 프로세스의 PID를 지정<br>
>  >  /F                    프로세스를 강제로 종료<br>
> * taskkill /pid proceess번호 /f
```
C:\Users\lbg12>taskkill /pid 38556 /f
성공: 프로세스(PID 38556)가 종료되었습니다.
```
