http://52.79.33.28:9090/apiplatform/apigtw/swagger-ui/v3/api-docs/default 내용을 기반으로 기존 생성한 FeignClient를 수정
- 특히 DTO 부분을 정확히 확인
- service: client.ione.${name}.service
  - 환경설정(application.yml)을 참조 금지
- client : client.ione.${name}
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.ione.config에 생성 또는 수정
  - config,intercept사용하는 Dto도 client.ione.common.dto에 생성 또는 수정
- dto: feign client에 정의된 이름과 동일하게 생성 또는 수정
  - request:  client.ione.${name}.dto.request
  - response:  client.ione.${name}.dto.response
  
  
API Common - Gateway 등록된 API 정보
- GET /admin/intf/v1/system/api/list.idt - [API-COM-001] API 목록 조회
- GET /admin/intf/v1/system/api/{apiId}/get.idt - [API-COM-002] API 정보 조회
- POST /admin/intf/v1/system/api/publish/api/regist.idt - [API-COM-003] API 등록
- PATCH /admin/intf/v1/system/api/publish/api/update.idt - [API-COM-004] API 수정
- POST /admin/intf/v1/system/api/publish/api/delete.idt - [API-COM-005] API 삭제
- GET /admin/intf/v1/system/api/svrgrp/list.idt - [API-COM-006] API 서버 그룹 목록 조회
- GET /admin/intf/v1/system/api/svrgrp/{apiSvrGrpId}/get.idt -[API-COM-007] API 서버 그룹 정보 조회
- POST /admin/intf/v1/system/api/workGrp/regist.idt - [API-COM-008] 업무 코드 등록
- GET /admin/intf/v1/system/api/workGrp/list.idt - [API-COM-009] 업무 코드 조회
- POST /admin/intf/v1/system/api/workGrp/delete.idt - [API-COM-010] 업무 코드 삭제
- PUT /admin/intf/v1/system/api/workGrp/update.idt - [API-COM-011] 업무 코드 수정
- POST /admin/intf/v1/system/api/publish/{infWorkSeq}/rePub.idt - [API-COM-012] 작업 재 요청
- POST /admin/intf/v1/system/api/publish/{infWorkSeq}/cancle.idt - [API-COM-013] 작업 요청 취소
- GET /admin/intf/v1/system/api/publish/api/list.idt - [API-COM-014] 작업 요청 결과 목록 조회
- GET /admin/intf/v1/system/api/publish/api/{infWorkSeq}/get.idt - [API-COM-015] 작업 요청 결과 조회


Open API Key - Gateway 등록된 API 호출시 사용될 API Key 관리는 11개로 구성 되어야 하는데 확인해줘
1. GET /admin/intf/v1/system/auth/apikey/list.idt - [API-KEY-001] Open API Key 목록 조회
2. GET /admin/intf/v1/system/auth/apikey/{openApiKey} - [API-KEY-002] Open API Key 단건 조회
3. POST /admin/intf/v1/system/auth/apikey.idt - [API-KEY-003] Open API Key 신규 발급
4. PATCH /admin/intf/v1/system/auth/apikey.idt - [API-KEY-004] Open API Key 수정
5. POST /admin/intf/v1/system/auth/apikey/delete.idt - [API-KEY-005] Open API Key 삭제
6. PATCH /admin/intf/v1/system/auth/apikey/renew.idt - [API-KEY-006] Open API Key 갱신
7. POST /admin/intf/v1/system/auth/apikey/regen.idt - [API-KEY-007] Open API Key 재발급
8. PATCH /admin/intf/v1/system/auth/apikey/reschedule.idt - [API-KEY-008] Open API Key 유효기간 재설정
9. PATCH /admin/intf/v1/system/auth/apikey/addScope.idt - [API-KEY-009] Open API Key scope추가
10. GET /admin/intf/v1/system/auth/portal/api.idt - [API-KEY-010] (ione portal solution) 포탈용 API 목록
11. GET /admin/intf/v1/system/auth/statistic.idt -[API-KEY-011] (ione portal solution) 파트너 및 그룹 API 요청 통계 조회


Ratelimit 관리 - Ratelimit 관련 설정 관리는 5개로 구성 되어야 하는데 확인해줘
GET /admin/intf/v1/system/ratelimit/policy/list.idt - [API-LMT-001] Ratelimit정책 목록 조회
GET /admin/intf/v1/system/ratelimit/page/policy.idt - [API-LMT-002] Ratelimit정책 목록 Pagination 조회
PUT /admin/intf/v1/system/ratelimit/policy.idt - [API-LMT-003] Ratelimit정책 추가/수정/삭제
POST /admin/intf/v1/system/ratelimit/apikey/config.idt - [API-LMT-004] API KEY 정책 추가/수정/삭제
POST /admin/intf/v1/system/ratelimit/apikey/replenish.idt - [API-LMT-005] API KEY 정책 limit 충전


어드민 사용자 관리 - 어드민 사용자 관리 API는 5개로 구성 되어야 하는데 확인해줘
GET /admin/intf/v1/system/adm/list.idt - [API-ADM-001] 사용자 목록 조회
GET /admin/intf/v1/system/adm/{id}/details.idt - [API-ADM-002] 사용자 정보 조회
POST /admin/intf/v1/system/adm/regist.idt - [API-ADM-003] 관리자 생성
PUT /admin/intf/v1/system/adm/update.idt - [API-ADM-004] 관리자 수정
POST /admin/intf/v1/system/adm/delete.idt - [API-ADM-005] 관리자 삭제


통계정보 조회 - 통계정보 조회 API는 5개로 구성 되어야 하는데 확인해줘
GET /admin/intf/v1/system/statistic/api.idt - [API-STS-001] API 호출 통계
GET /admin/intf/v1/system/statistic/apiGroup.idt - [API-STS-002] API ID 별 호출 통계
GET /admin/intf/v1/system/statistic/apiKey.idt - [API-STS-003] API KEY 호출 통계
GET /admin/intf/v1/system/statistic/apiKeyGroup.idt - [API-STS-004] API KEY 별 호출 통계
GET /admin/intf/v1/system/statistic/ratelimit/apiKey.idt - [API-STS-005] API KEY RateLimit 호출 통계
GET /admin/intf/v1/system/statistic/{statisticType}/stat.idt - [API-STS-006] 통계 유형별 RateLimit 호출 통계



