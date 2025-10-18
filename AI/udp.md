1. Dataset 검색 API
   - 요청 : 
   "curl -X POST  ""http://APIGWIP:PORT/portal/udp/api/datasetcard/search"" \
      -d ""search_word=검색어&dateset_card_type=DATESET"""	
   - 응답 :   
   "{
       ""total_count"": 1,
       ""page"": 1,
       ""result_lists"": [
           {
               ""dataset_card_id"": 1,
               ""dataset_card_name"": ""규정"",
               ""dataset_cd"": ""rgl"",
               ""dataset_name"": ""규정"",
               ""origin_system_cd"": ""sb"",
               ""origin_system_name "": ""S-Basic"",
               ""dataset_card_type"": ""DATASET"",
               ""dataset_summary"": ""신한은행 자금이체약정서의 2025년 최신 개정판으로 업무에 참고하세요."",
               ""preview"": ""데이터셋 미리보기"",
               ""metadata"": ""메타1, 메타2,메타3"",
               ""download_path"": """"
           }
       ]
   }"										

2. Dataset별 문서검색 API
  - 요청
  "curl -X POST  ""http://APIGWIP:PORT/portal/udp/api/documents/lists"" \
     -d ""dateset_cd=rgl&doc_mod_start=20251001&doc_mod_end=20251001&origin_metadata_yn=N"""										
  - 응답
  "{
      ""total_count"": 1,
      ""page"": 1,
      ""result_lists"":[
          {
              ""doc_summary"": ""신한은행 자금이체약정서의 2025년 최신 개정판으로 업무에 참고하세요."",
              ""origin_metadata"": {
                  ""doc_exe_dt"": ""20150925"",
                  ""parsed_token_cnt"": """",
                  ""doc_type_nm"": ""일부개정"",
                  ""doc_dataset_cd"": ""rgl"",
                  ""docmap_nm"": ""업무기준"",
                  ""orgl_file_ext"": ""HWP"",
                  ""parsed_token_algol"": """",
                  ""pop_link"": ""http://172.23.192.126:18080/mmw//api.jsp?apiType=TCDTPOPP&contId=2006040200360000&contSid=0009"",
                  ""category3 "": ""수신"",
                  ""title"": ""제28절 Mint 정기예금(2014.06.13 판매중지)"",
                  ""uuid"": ""doc03_sbrgl20060402003600000009"",
                  ""doc_refer_nm"": ""S-basic"",
                  ""category5 "": ""제5장 거치식예금"",
                  ""orgl_file_path"": ""/nbsdata/sbasic/legas42_dev/cont/2006/04/02/00360000/0009/NATI0023/"",
                  ""attach_pdoc_uuid"": """",
                  ""attach_file_size"": ""0"",
                  ""org_nm"": ""개인솔루션부"",
                  ""attach_array_uuids"": [
                      ""doc03_sbrgl20060402003100000009"",
                      ""doc03_sbrgl20060402003200000009"",
                      ""doc03_sbrgl20060402003300000009""
                  ],
                  ""orgl_link"": ""http://172.23.192.126:18080/mmw//svnrNormInqyDown1010.do?mappingId=/svnrNormInqyDown1010.do&genActiontypeCd=2ACT1010&contId=2006040200360000&fileSno=00000108"",
                  ""attach_file_type"": """",
                  ""timestamp"": ""2024-10-07 02:05:46"",
                  ""doc_array_keywords"": [
                      ""키워드1"",
                      ""키워드2"",
                      ""키워드3""
                  ],
                  ""doc_dataset_nm"": ""규정"",
                  ""doc_summary"": ""신한은행 자금이체약정서의 2025년 최신 개정판으로 업무에 참고하세요."",
                  ""author"": ""김영진"",
                  ""category1"": ""SB"",
                  ""doc_indexed_date"": ""45908765324074"",
                  ""ended_date"": ""20191231"",
                  ""trfm_file_ext"": """",
                  ""category2 "": ""업무기준"",
                  ""modified_date"": ""20191228"",
                  ""category4 "": ""제2편 예금각론"",
                  ""doc_refer_cd"": ""sb"",
                  ""doc_path_anony"": ""/sb/rgl/03/doc03_sbrgl20060402003600000009/v1/01/anony_doc03_sbrgl20060402003600000009.md"",
                  ""cont_id "": ""2006040200360000"",
                  ""attched_file_yn"": """",
                  ""doc_status"": """",
                  ""parsing_algol"": """",
                  ""created_date"": ""20191228"",
                  ""attach_yn"": ""N"",
                  ""parsed_file_size"": """",
                  ""status"": ""C""
              },
              ""last_mod_date"": ""20191228"",
              ""doc_uuid"": ""doc03_sbrgl20060402003600000009"",
              ""dataset_name"": ""규정"",
              ""create_date"": ""20191228"",
              ""doc_path_anony_md"": ""/sb/rgl/03/doc03_sbrgl20060402003600000009/v1/01/anony_doc03_sbrgl20060402003600000009.md"",
              ""dataset_cd"": ""rgl"",
              ""attach_parent_doc_uuid"": """",
              ""doc_array_keywords"": [
                  ""키워드1"",
                  ""키워드2"",
                  ""키워드3""
              ]
          }
      ]
  }"										
3. Dataiku Scenario 실행
  - 요청
  "curl -X POST ""http://APIGWIP:PORT/udp/dataiku/public/api/projects/DOCUSEETEST/scenarios/DAILY_TEST/run""
    -H ""Authorization: Bearer $Bearer_Token""
    -H ""Content-Type: application/json""
  - 응답
    -d ""{\""scenarioParam1\"": \""value1\"", \""scenarioParam2\"": \""value2\""}"""										
  {"projectKey":"DOCUSEETEST","scenarioId":"DAILY_TEST","trigger":{"id":"manual","type":"manual","name":"API run","delay":0,"active":false},"runId":"2025-10-01-15-39-56-668","timestamp":1759300796667,"cancelled":false,"params":{"scenarioParam1":"value1","scenarioParam2":"value2"},"triggerAuthCtx":{"userGroupLevelPermissions":{"admin":false,"mayManageUDM":false,"mayCreateProjects":true,"mayCreateProjectsFromMacros":true,"mayCreateProjectsFromTemplates":true,"mayCreateProjectsFromDataikuApps":true,"mayWriteUnsafeCode":true,"mayWriteSafeCode":true,"mayCreateAuthenticatedConnections":false,"mayCreateCodeEnvs":true,"mayCreateClusters":false,"mayCreateCodeStudioTemplates":false,"mayDevelopPlugins":true,"mayEditLibFolders":false,"mayManageCodeEnvs":true,"mayManageClusters":false,"mayManageCodeStudioTemplates":false,"mayViewIndexedHiveConnections":false,"mayCreatePublishedAPIServices":false,"mayCreatePublishedProjects":true,"mayWriteInRootProjectFolder":false,"mayCreateActiveWebContent":true,"mayCreateWorkspaces":true,"mayShareToWorkspaces":true,"mayCreateDataCollections":true,"mayPublishToDataCollections":true,"mayManageFeatureStore":false},"via":[],"authSource":"PERSONAL_API_KEY","realUserLogin":"deviku","userGroups":["data_team"],"userProfile":"FULL_DESIGNER","apiKey":{"user":"deviku","expiresOn":0,"id":"434rEUu6yce0bQ3D","label":"Personal for deviku","description":"","createdOn":1758516599613,"createdBy":"deviku"}}}										

4. Dataiku Scenario 실행 상태 조회 
  - 요청	
  "curl -X GET ""http://APIGWIP:PORT/udp/dataiku/public/api/projects/DOCUSEETEST/scenarios/DAILY_TEST/light""
     -H ""Authorization: Bearer $Bearer_Token""
     -H ""Content-Type: application/json"""	
  - 응답	 
  {"type":"step_based","active":false,"unavailable":false,"automationLocal":false,"triggerDigestItems":[],"reporterDigestItems":[],"markedAsTest":false,"triggerDigest":"","nextRun":0,"running":true,"start":1759300796669,"projectKey":"DOCUSEETEST","id":"DAILY_TEST","name":"DAILY_TEST","tags":[],"lastModifiedOn":0,"createdOn":0}										

5. KT Embedding Inference
  - 요청
  curl -X POST "http://APIGWIP:PORT/gaf/embedding/kt/score"
    -H "Content-Type: application/json"
    -d "{\"texts\": [\"검색 질의인 경우\"], \"text_type\": \"query\"}"	
  - 응답	 
  {
    "embeddings": [
      [1,2,3,4,5,6,7,8],
  	...
    ],
    "inputTokens": 8
  }

udp.txt을 분석해서 내용을 기반으로 FeignClient를 생성해줘
- config, client는 clent.ione.config.* 와 clent.ione.apikey을 참조해서 생성
- service: client.udp.${name}.service
  - 환경설정(application.yml)을 참조 금지
- client : client.udp.${name}
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.udp.config에 생성 또는 수정
  - config,intercept사용하는 Dto도 client.udp.common.dto에 생성 또는 수정
- dto: feign client에 정의된 이름과 동일하게 생성 또는 수정
  - request:  client.udp.${name}.dto.request
  - response:  client.udp.${name}.dto.response
  
일라스틱서치 feign client 를 param 2~4개을 Get, Post 방식으로 개발해줘
- config, client는 clent.ione.config.* 와 clent.ione.apikey을 참조해서 생성
- service: client.elastic.search.service
  - 환경설정(application.yml)을 참조 금지
- client : client.elastic.search
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.elastic.config에 생성 또는 수정
  - config,intercept사용하는 Dto도 client.elastic.common.dto에 생성 또는 수정
- dto: feign client에 정의된 이름과 동일하게 생성 또는 수정
  - request:  client.elastic.search.dto.request
  - response:  client.elastic.search.dto.response