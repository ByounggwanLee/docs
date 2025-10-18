Feign Spec을 분석하여 FeignClient를 생성해줘
- Feign Spec
```
HOST_NAME=http://eval-public-shinhan.datumo.com
 
# 로그인 API를 호출하여 JSON Response 내 accessToken 필드에 있는 Access Token을 $ACCESS_TOKEN 변수로 저장
# jq가 설치되어 있지 않다면 curl 명령어만 실행 후 accessToken 필드의 값을 복사해서 저장하면 됩니다.
ACCESS_TOKEN=$(curl -X POST ${HOST_NAME}/api/v2/login \\
  -H 'Content-Type: application/json' \\
  -d '{ "loginId": "shinhan_admin", "password": "shinhanadmin12!" }' | jq -r '.accessToken')
 
# Task GET API 호출 (검색어가 없는 경우)
curl -X GET "${HOST_NAME}/api/task-list?projectId=1&category=JUDGE&page=1&pageSize=12" \\
  -H "Authorization: Bearer $ACCESS_TOKEN"
 
# Task GET API 호출 (검색어가 있는 경우)
curl -X GET "${HOST_NAME}/api/task-list?projectId=1&category=JUDGE&page=1&pageSize=12&search=RAGAS" \\
  -H "Authorization: Bearer $ACCESS_TOKEN"
  
# 호출결과
{
  "totalDataCount": 151,
  "totalPageCount": 16,
  "tasks": [
    {
      "id": "EVALUATION-435",
      "displayId": "1",
      "name": "테스트 Task",
      "description": "테스트 Task에 대한 설명입니다.",
      "createdAt": "2025-09-19T09:40:11.291286",
      "redirectUrl": "<http://eval-public-shinhan.datumo.com/evaluation-task/?projectId=435&isModelProject=true>"
    }
  ]
}
```
- service: client.datumo.api.service
  - 환경설정(application.yml)을 참조 금지
- client : client.datumo.api
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.datumo.config에 생성
  - config,intercept사용하는 Dto는 client.datumo.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.datumo.api.dto.request
  - response:  client.datumo.api.dto.response
  
- service: client.lablup.api.service
  - 환경설정(application.yml)을 참조 금지
- client : client.lablup.api
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.lablup.config에 생성
  - config,intercept사용하는 Dto는 client.lablup.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.lablup.api.dto.request
  - response:  client.lablup.api.dto.response