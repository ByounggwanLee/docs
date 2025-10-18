# 프롬프트 기법
1. FewShut
2. 역할지정기법
3. MarkDown기법
4. 후카츠 프롬프트 기법(형식 지정 기법)
5. Q&A기법
6. 이어쓰시 기법
7. 멀티 페르소나 기법
8. Chain of thoughts 기법
9. 할루시네이션을 활용한 기법
10. 할루시네이션 회피방법
```
# 프로젝트 생성
```
1. 디렉토리 생성
2. copilot-instructions.md 생성
3. copilot-instructions.md 기반 프로젝트 생성해줘
```
# FeignClient 생성
```
for api in  https://aip-stg.sktai.io/api/v1/data https://aip-stg.sktai.io/api/v1/agent https://aip-stg.sktai.io/api/v1/knowledge https://aip.sktai.io/api/v1/model https://aip-stg.sktai.io/api/v1/evaluation https://aip-stg.sktai.io/api/v1/management/safety_filter https://aip-stg.sktai.io/api/v1/finetuning https://aip-stg.sktai.io/api/v1/serving https://aip-stg.sktai.io/api/v1/model_gateway https://aip-stg.sktai.io/api/v1/agent_gateway https://aip-stg.sktai.io/api/v1/management/resource https://aip-stg.sktai.io/api/v1/management/history
do 
    name=$(basename $api | sed 's/_//g')
    # echo $name, $api
	echo "- URL($api/openapi.json)를 참조" | tee -a imsi.txt
    echo "  - Config, intercept는 /client/sktai/config, /client/sktai/intercept의 class를 참조하고 필요시 수정" | tee -a imsi.txt
    echo "  - Feign Client Interface는 접속 엔드포인트별로 Group화하여 /client/sktax/$name 디렉토리에 생성" | tee -a imsi.txt
    echo "  - dto는 /client/sktai/$name/dto/request, /client/sktai/$name/dto/response에 생성" | tee -a imsi.txt
	echo "    - static class는 /client/sktai/$name/dto에 일반 class로 생성" | tee -a imsi.txt
	echo "---" | tee -a imsi.txt
done
```
```
아래 URL을 분석하여
- URL: https://aip-stg.sktai.io/api/v1/agent/docs, https://aip-stg.sktai.io/api/v1/common/auth/docs, https://aip-stg.sktai.io/api/v1/data/docs,https://aip-stg.sktai.io/api/v1/knowledge/docs, https://aip.sktai.io/api/v1/model/docs,https://aip-stg.sktai.io/api/v1/evaluation/docs,https://aip-stg.sktai.io/api/v1/management/safety_filter/docs, https://aip-stg.sktai.io/api/v1/finetuning/docs, https://aip-stg.sktai.io/api/v1/serving/docs, https://aip-stg.sktai.io/api/v1/model_gateway/docs, https://aip-stg.sktai.io/api/v1/agent_gateway/docs, https://aip-stg.sktai.io/api/v1/management/resource/docs, https://aip-stg.sktai.io/api/v1/management/history/docs
- Config, intercept는 /client/sktai/config, /client/sktai/intercept의 class에 생성
- Inner Class생성금지
- 공통으로 사용하는 DTO나 Inner Class는 client/sktai/common/dto에 생성
- 분석한 URL별로 client/sktai/에 디렉토리를 생성
  - Feign Client Interface는 접속 엔드포인트별로 생성
  - dto는 dto디렉토리 생성 후 Request, Response에 각각 생성
```
# Feign기반 Controller, Service, DTO 생성
``` Bash
for data in `find ./data -name SktAi*.java`
do
	directory=`basename $(dirname $data)`
	srcfile=`basename $data`
	destfile=`echo $srcfile | sed s/SktAi//g | sed s/Client.java//g`
	
	# echo dir=$directory , srcfile=$srcfile, destfile=$destfile
	echo "---"
	echo "- File:$srcfile를 호출하는 아래의 프로그램을 생성 또는 수정"
	echo "  - JavaDoc과 OpenApi 주석 포함 생성"
  echo "    - controller에서 사용하는 dto는 client/sktai/**/dto/**는 사용금지"
  echo "    - /dto/data/request/에 suffix을 Request대신 Req로 생성"
	echo "    - /dto/data/response/에 suffix을 Response대신 Res로 생성"
  echo "  - Service와 Controller의 입력값은 $srcfile와 동일한 갯수로 생성"
  echo "  - Service Interface: /service/${directory}/${destfile}Service.java"
  echo "  - Service Impl: /service/${directory}/impl/Skt${destfile}ServiceImpl.java에 생성"
  echo "  - Controller: /Controller/${directory}/${destfile}Controller.java에 생성"
done
```
```
- File:SktAiDatasetClient.java를 호출하는 아래의 프로그램을 생성 또는 수정
  - JavaDoc과 OpenApi 주석 포함 생성
    - dto 생성시 dto내에 client/sktai/**/dto/**는 참조사용 금지(필요시 신규 생성)
    - /dto/data/request/에 suffix을 Request대신 Req로 생성
    - /dto/data/response/에 suffix을 Response대신 Res로 생성
  - Service와 Controller의 입력값은 SktAiDatasetClient.java와 동일한 갯수로 생성
  - Service Interface: /service/data/DatasetService.java
  - Service Impl: /service/data/impl/SktDatasetServiceImpl.java에 생성
  - Controller: /Controller/data/DatasetController.java에 생성
```
# 명명규칙
```
스프링부트 표준 명명규칙를 작성해줘
- Rest Controller Method, Mepping에 대해 Get,Post,Patch,Put, Delete등 상세하게
- Get의 경우 Get방식에 전체/단건/단수조건/복수조건 검색등에 대해 상세
- Controller, DTO, Service, Entity, Respository간에 명명규칙 관계에 대해
- Controller, DTO, Service, Feign DTO, FeignClient간에 명명규칙 관계에 대해
- [업무그룹]별로 디렉토리를 생성 후 파일생성
- 좋은예시/나쁜예시 포함
- DTO는 Request와 Response 분리하여 Suffix로 Req, Res로 표기 하도록
- FeigneClient는 /client/skai/[업무그룹]/ 
- FeignClient DTO는 /client/skai/[업무그룹]/dto( Request, Response 분리)
- 목차를 만들고 링크 포함해서
```

# 개발표준
```
# 프로젝트 문서를 아래내용을 참조하여, 개발표준.md를 현행화 해주세요.

1. 프로젝트 개요 및 AI 코딩 접근 방식
   - 이 Spring Boot 프로젝트의 핵심 비즈니스 목적과 해결하려는 문제는 무엇인가요? 
   - 특히, 프로젝트 개발에 AI 코딩(예: GitHub Copilot, ChatGPT 등)이 어떤 방식으로, 어느 정도 활용되었는지 명확히 설명해 주세요. 
   - AI가 생성한 코드와 수동으로 작성된 코드 간의 역할 분담 및 통합 전략에 대해서도 기술해 주세요.

2. 아키텍처 및 모듈 구조
   - 프로젝트의 전체적인 아키텍처 다이어그램을 제공하고, 각 Spring Boot 모듈(서비스, 라이브러리 등)의 역할과 책임을 명확히 설명해 주세요. 
   - 특히, AI가 생성한 코드가 주로 어느 계층(Controller, Service, Repository, DTO 등)에 위치하며, 각 모듈 간의 데이터 흐름과 상호작용 방식을 구체적으로 보여주세요.

3. 핵심 기능 설명 및 AI 코드 연관성
   - 이 프로젝트의 주요 핵심 기능 5가지를 식별하고, 각 기능별로 비즈니스 로직의 흐름을 상세히 설명해 주세요. 
   - 각 기능 구현에 AI가 생성한 코드가 어떤 특정 부분에서 기여했으며, 해당 AI 생성 코드가 어떤 역할을 수행하는지 구체적인 코드 예시와 함께 설명해 주세요.

4. AI 생성 코드 품질 및 검토 가이드라인
   - AI가 생성한 코드에 대한 코드 품질 기준 및 검토 가이드라인을 제시해 주세요. 예를 들어, 가독성, 성능 최적화, 보안 취약점 점검, 비즈니스 로직의 정확성 검증 등 AI 생성 코드에 대해 특별히 주의해야 할 사항은 무엇인가요? 
   - 코드 리뷰 과정에서 AI 생성 코드를 어떻게 다루어야 하는지에 대한 절차도 포함해 주세요."

5. 데이터 모델 및 엔티티 관계
   - 프로젝트에서 사용되는 주요 데이터 모델(JPA 엔티티 등)과 그들 간의 관계를 ERD(Entity Relationship Diagram)와 함께 설명해 주세요. 
   - 각 엔티티의 핵심 필드와 제약 조건을 명시하고, AI가 데이터베이스 스키마 또는 쿼리 생성에 기여한 부분이 있다면 언급해 주세요.

6. 개발 환경 및 필수 도구
   - 프로젝트 개발을 위한 **필수 개발 환경(Java 버전, Spring Boot 버전, IDE, 빌드 도구 등)**을 명확히 명시하고, 
   - 프로젝트 빌드 및 실행을 위한 상세한 절차를 제공해 주세요. 
   - AI 코딩에 사용된 특정 플러그인이나 도구 설정이 있다면 함께 설명해 주세요."

7. 종속성 관리 및 외부 연동
   - 프로젝트의 주요 외부 라이브러리 및 프레임워크 종속성(pom.xml 또는 build.gradle 기반)을 설명하고, 각 종속성의 역할에 대해 간략히 설명해 주세요. 
   - 외부 서비스(REST API, 메시지 큐 등)와의 연동 방식 및 사용된 Feign Client 또는 WebClient 설정에 대해 기술해 주세요.

8. 테스트 전략 및 AI 코드 테스트
   - 이 프로젝트의 **테스트 전략(단위 테스트, 통합 테스트, 인수 테스트)**을 설명하고, 
   - 각 테스트 유형별로 AI가 생성한 코드에 대한 테스트는 어떻게 수행되었는지 구체적인 사례를 들어 설명해 주세요. 
   - 코드 커버리지 목표 및 CI/CD 파이프라인에서의 테스트 자동화 여부도 명시해 주세요."

9. 배포 및 운영 가이드
   - 프로젝트를 운영 환경에 배포하기 위한 상세한 절차를 제공하고, 애플리케이션의 주요 설정(application.yml 등) 및 환경 변수에 대해 설명해 주세요. 
   - 운영 중 발생할 수 있는 잠재적 문제(로그 분석, 성능 병목, AI 모델 관련 오류 등)와 그 해결 방안을 포함한 운영 가이드를 작성해 주세요.

10. AI 코딩 시 주의사항 및 향후 개선 방향
   - 이 프로젝트 개발 과정에서 AI 코딩으로 인해 발생했던 주요 문제점이나 어려움은 무엇이었나요? (예: 비효율적인 코드, 보안 취약성, 유지보수의 어려움 등) 
   - 이러한 문제들을 어떻게 해결했으며, 
   - 향후 프로젝트의 유지보수, 확장, 또는 새로운 기능 개발 시 AI 코딩을 활용하는 데 있어 개발자들이 특별히 주의해야 할 사항과 개선 방향에 대해 제안해 주세요.
```
