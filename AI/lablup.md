Reservoir Sync Manual.pdf 을 분석 사용 할 수 있는 FeignClient 생성해줘
- 대상 FeignClient  
  Bulk Artifact Scan - 벌크 아티팩트 스캔
  Single Artifact Model Scan - 단일 아티팩트 모델 스캔
  Batch Scan Artifact Models - 배치 아티팩트 모델 스캔 (신규 추가)
  Get Artifact Metadata - 아티팩트 메타데이터 조회
  Import Artifact - 아티팩트 가져오기
  Search Artifact - 아티팩트 검색
  Cleanup Artifacts - 아티팩트 정리
  Cancel Import Artifact - 가져오기 취소
  Get Task Status - 작업 상태 조회
  Download Artifact - 아티팩트 다운로드
  Upload Artifact - 아티팩트 업로드
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

  첨부한 문서를 분석 사용 할 수 있는 FeignClient 누락없이 생성해줘 
- 대상 FeignClient  
  Bulk Artifact Scan - 벌크 아티팩트 스캔
  Single Artifact Model Scan - 단일 아티팩트 모델 스캔
  Batch Scan Artifact Models - 배치 아티팩트 모델 스캔 (신규 추가)
  Get Artifact Metadata - 아티팩트 메타데이터 조회
  Import Artifact - 아티팩트 가져오기
  Search Artifact - 아티팩트 검색
  Cleanup Artifacts - 아티팩트 정리
  Cancel Import Artifact - 가져오기 취소
  Get Task Status - 작업 상태 조회
  Download Artifact - 아티팩트 다운로드
  Upload Artifact - 아티팩트 업로드
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
  
  
첨부한 문서를 분석 생성된 FeignClient의 내용을 다시한번 점검해서 반영해줘 
- 대상 FeignClient  
   1) Scan Artifact - /v1/artifact-registries/scan
   2) Scan Single Artifact Model - /v1/artifact-registries/model/{model_id}
   3) Batch Scan Artifact Models - /artifact-registries/models/batch
   4) Search Artifacts - /artifact-registries/search
   5) Import Artifacts - /artifacts/import
   6) Cleanup Artifacts - /artifacts/revisions/cleanup
   7) Cancel Import Artifact - /artifacts/task/cancel
   8) Update Artifact - /artifacts/{artifact_id}
   9) Get Artifact Revision Readme - /artifacts/revisions/{artifact_revison_id}/readme
  10) Get Pr - esigned Download URL - /object-storages/presigned/download
  11) Get Presigned Upload URL - /object-storages/presigned/upload
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

1. 컨테이너 로그 조회 API
 
GET /session/{session_id}/logs 를 사용할 수 있습니다. 예시는 다음과 같습니다. 
request_body의 owner_access_key는 다른 사용자의 세션을 조회할 때 그 사용자의 access_key를 적어줄 때 사용합니다. 
멀티 노드 세션인 경우, kernel_id를 별도로 지정하여 서브 컨테이너의 정보를 가져오는 것도 가능합니다.
 
def get_session_log(pk):
    # Generate the authentication header
    method = "GET"
    date = datetime.now(tzutc())  # Should be UTC
    rel_url = f"/session/{pk}/logs"
    content_type = "application/json"
    hdrs, _ = generate_signature(
        method=method,
        version=API_VERSION,
        endpoint=API_ENDPOINT,
        date=date,
        rel_url=rel_url,
        content_type=content_type,
        access_key=ACCESS_KEY,
        secret_key=SECRET_KEY,
        hash_type=HASH_TYPE,
    )
 
    # Build request headers
    headers = {
        "User-Agent": "Backend.AI API Client",
        "Content-Type": content_type,
        "X-BackendAI-Version": API_VERSION,
        "Date": date.isoformat(),
        **hdrs,
    }
 
    request_body = {
        # "owner_access_key": "access-key-for-other-user",
        # "kernel_id": "for-multinode-container",
    }
 
    # Send request
    r = requests.get(API_ENDPOINT / rel_url[1:], headers=headers, json=request_body)
    return r.json()
 
 
2. 리소스 그룹별, 노드별 자원 할당량 조회 API
   리소스 그룹별 자원 할당량은 다음과 같은 쿼리로 조회할 수 있습니다. 
   Scaling_groups 하위 항목 중 agent_total_resource_slots_by_status 입니다.
 
    query = """
        query($is_active: Boolean) {
            scaling_groups(is_active: $is_active) {
                name
                description
                is_active
                created_at
                driver
                driver_opts
                scheduler
                scheduler_opts
                use_host_network
                wsproxy_addr
                wsproxy_api_token
                agent_total_resource_slots_by_status
            }
        }
    """
    query = textwrap.dedent(query).strip()
    variables = {
        "is_active": True
    }
    data = {"query": query, "variables": variables}
 
   노드별 자원 할당량은 다음 쿼리로 가능합니다. 
   available_slots가 총 보유 자원량, occupied_slots가 현재 할당된 양입니다.
 
    fields = [
        "id", "addr", "status", "scaling_group", "schedulable",
        "available_slots", "occupied_slots",
    ]
    query = """
        query(
            $limit: Int!, $offset: Int!, $filter: String, $order: String,
            $status: String, $scaling_group: String
        ) {
            agent_list(
                limit: $limit, offset: $offset, filter: $filter, order: $order,
                status: $status, scaling_group: $scaling_group
            ) {
                items { $fields }
                total_count
            }
        }
    """
    query = query.replace('$fields', ' '.join(fields))
    query = textwrap.dedent(query).strip()
    variables = {
        "limit": 50,
        "offset": 0,
        "filter": 'schedulable == true',
        "order": "id",
        "status": "ALIVE",
        "scaling_group": "default",
    }
    data = {"query": query, "variables": variables}
 