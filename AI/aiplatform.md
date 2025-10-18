safetyfilter, https://aip-stg.sktai.io/api/v1/management/safety_filter
https://aip-stg.sktai.io/api/v1/management/safety_filter/openapi.json의 내용중 paths별로 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.safetyfilter.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.safetyfilter
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.safetyfilter.dto.request
  - response:  client.sktai.safetyfilter.dto.response
---
finetuning, https://aip-stg.sktai.io/api/v1/finetuning
https://aip-stg.sktai.io/api/v1/finetuning/openapi.json의 내용중 paths별로 서비스 를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.finetuning.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.finetuning
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.finetuning.dto.request
  - response:  client.sktai.finetuning.dto.response
---
https://aip-stg.sktai.io/api/v1/serving/openapi.json의 내용중 paths별로 서비스를  사용 할 수 있는 FeignClient를 생성
- service: client.sktai.serving.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.serving
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.serving.dto.request
  - response:  client.sktai.serving.dto.response
---
https://aip-stg.sktai.io/api/v1/model_gateway/openapi.json의 내용중 paths별로 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.modelgateway.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.modelgateway
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.modelgateway.dto.request
  - response:  client.sktai.modelgateway.dto.response
---
https://aip-stg.sktai.io/api/v1/agent_gateway/openapi.json의 내용중 paths별로 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agentgateway.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agentgateway
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agentgateway.dto.request
  - response:  client.sktai.agentgateway.dto.response
---
https://aip-stg.sktai.io/api/v1/management/resource/openapi.json의 내용중 paths별 로 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.resource.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.resource
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.resource.dto.request
  - response:  client.sktai.resource.dto.response
---
https://aip-stg.sktai.io/api/v1/management/history/openapi.json의 내용중 paths별로 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.history.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.history
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.history.dto.request
  - response:  client.sktai.history.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/model-benchmark/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/model-benchmark-results/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/model-benchmark-tasks/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/model-benchmark-logs/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/rag-evaluation/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/rag-evaluation-results/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/rag-evaluation-tasks/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/rag-evaluation-logs/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/evaluations/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/evaluation-results/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/evaluation-tasks/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/evaluation-logs/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/evaluation/openapi.json의 내용중 paths: /api/v1/auth/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.evaluation.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.evaluation
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.evaluation.dto.request
  - response:  client.sktai.evaluation.dto.response
---
https://aip-stg.sktai.io/api/v1/common/auth/openapi.json의 내용중 paths: /api/v1/auth/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- controller: client.sktai.controller  
- service: client.sktai.auth.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.auth
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- request dto:  client.sktai.auth.dto.request
- response dto:  client.sktai.auth.dto.response

https://aip-stg.sktai.io/api/v1/common/auth/openapi.json의 내용중 paths: /api/v1/auth/* 의 서비스를 사용 할 수 있는 FeginClient를 생성
- client : client.sktai.auth
- request dto:  client.sktai.auth.dto.request
- response dto:  client.sktai.auth.dto.response
- config(공통사용): client.sktai.config
- intercept(공통사용): code.client.sktai.intercept

https://aip-stg.sktai.io/api/v1/common/auth/openapi.json의 내용중 paths: /api/v1/auth/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.auth.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.auth
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.auth.dto.request
  - response:  client.sktai.auth.dto.response
---
https://aip-stg.sktai.io/api/v1/common/auth/openapi.json의 내용중 paths: /api/v1/projects/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.auth.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.auth
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.auth.dto.request
  - response:  client.sktai.auth.dto.response
---
https://aip-stg.sktai.io/api/v1/common/auth/openapi.json의 내용중 paths: /api/v1/users/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.auth.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.auth
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.auth.dto.request
  - response:  client.sktai.auth.dto.response  
---
/api/v1/agent/health/*
/api/v1/agent/tool/tools/*
/api/v1/agent/prompting/Inference-Prompts/*
/api/v1/agent/prompting/Few-Shots/*
/api/v1/agent/agent/apps/*
/api/v1/agent/agent/graphs/*
/api/v1/agent/common/Permissions/*
/api/v1/agent/default/*

https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/health/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/tool/tools/*의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/prompting/Inference-Prompts/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/prompting/Few-Shots/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/agent/apps/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/agent/graphs/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/common/Permissions/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
https://aip-stg.sktai.io/api/v1/agent/openapi.json의 내용중 paths: /api/v1/agent/default/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.agent.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.agent
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.agent.dto.request
  - response:  client.sktai.agent.dto.response
---
datasets
generations
datasources
processors
generators

https://aip-stg.sktai.io/api/v1/data/openapi.json의 내용중 paths: /api/v1/datasets/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.data.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.data
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.data.dto.request
  - response:  client.sktai.data.dto.response
---
https://aip-stg.sktai.io/api/v1/data/openapi.json의 내용중 paths: /api/v1/generations/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.data.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.data
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.data.dto.request
  - response:  client.sktai.data.dto.response
---
https://aip-stg.sktai.io/api/v1/data/openapi.json의 내용중 paths: /api/v1/datasources/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.data.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.data
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.data.dto.request
  - response:  client.sktai.data.dto.response
---
https://aip-stg.sktai.io/api/v1/data/openapi.json의 내용중 paths: /api/v1/processors/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.data.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.data
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.data.dto.request
  - response:  client.sktai.data.dto.response
---
https://aip-stg.sktai.io/api/v1/data/openapi.json의 내용중 paths: /api/v1/generators/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.data.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.data
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.data.dto.request
  - response:  client.sktai.data.dto.response
---
vectordbs
queries
chunk_stores
tools
repos
custom_scripts

https://aip-stg.sktai.io/api/v1/knowledge/openapi.json의 내용중 paths: /api/v1/vectordbs/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.knowledge.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.knowledge
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.knowledge.dto.request
  - response:  client.sktai.knowledge.dto.response
---
https://aip-stg.sktai.io/api/v1/knowledge/openapi.json의 내용중 paths: /api/v1/queries/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.knowledge.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.knowledge
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.knowledge.dto.request
  - response:  client.sktai.knowledge.dto.response
---
https://aip-stg.sktai.io/api/v1/knowledge/openapi.json의 내용중 paths: /api/v1/chunk_stores/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.knowledge.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.knowledge
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.knowledge.dto.request
  - response:  client.sktai.knowledge.dto.response
---
https://aip-stg.sktai.io/api/v1/knowledge/openapi.json의 내용중 paths: /api/v1/tools/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.knowledge.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.knowledge
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.knowledge.dto.request
  - response:  client.sktai.knowledge.dto.response
---
https://aip-stg.sktai.io/api/v1/knowledge/openapi.json의 내용중 paths: /api/v1/repos/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.knowledge.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.knowledge
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.knowledge.dto.request
  - response:  client.sktai.knowledge.dto.response
---
https://aip-stg.sktai.io/api/v1/knowledge/openapi.json의 내용중 paths: /api/v1/custom_scripts/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.knowledge.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.knowledge
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.knowledge.dto.request
  - response:  client.sktai.knowledge.dto.response
---
model-providers
models
custom-runtimes
private-models
health
cache_monitoring
https://aip-stg.sktai.io/api/v1/model/openapi.json의 내용중 paths: /api/v1/model-providers/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.model.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.model
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.model.dto.request
  - response:  client.sktai.model.dto.response
---
https://aip-stg.sktai.io/api/v1/model/openapi.json의 내용중 paths: /api/v1/models/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.model.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.model
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.model.dto.request
  - response:  client.sktai.model.dto.response
---
https://aip-stg.sktai.io/api/v1/model/openapi.json의 내용중 paths: /api/v1/custom-runtimes/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.model.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.model
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.model.dto.request
  - response:  client.sktai.model.dto.response
---
https://aip-stg.sktai.io/api/v1/model/openapi.json의 내용중 paths: /api/v1/private-models/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.model.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.model
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.model.dto.request
  - response:  client.sktai.model.dto.response
---
https://aip-stg.sktai.io/api/v1/model/openapi.json의 내용중 paths: /api/v1/health/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.model.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.model
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.model.dto.request
  - response:  client.sktai.model.dto.response
---
https://aip-stg.sktai.io/api/v1/model/openapi.json의 내용중 paths: /api/v1/cache_monitoring/* 의 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.model.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.model
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.model.dto.request
  - response:  client.sktai.model.dto.response
---
https://aip-stg.sktai.io/api/v1/agent_gateway/openapi.json의 내용중 paths별로 서비스를 사용 할 수 있는 FeignClient를 생성
- service: client.sktai.${name}.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.${name}
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto도 client.sktai.config에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.${name}.dto.request
  - response:  client.sktai.${name}.dto.response
  ---
  https://aip-stg.sktai.io/api/v1/common/auth/openapi.json의 내용중 paths: /api/v1/auth/* 의 서비스를 사용 할 수 있는 FeignClient 중 
기능이 누락과 틀린 내용이 있는 것 같아 다시 검토 후 반영해줘
- service: client.sktai.auth.service
  - 환경설정(application.yml)을 참조 금지
- client : client.sktai.auth
- config,intercept(공통사용)
  - 공통기능 신규추가 금지
  - client.sktai.config에 생성
  - config,intercept사용하는 Dto는 client.sktai.common.dto에 생성
- dto: feign client에 정의된 이름과 동일하게 생성
  - request:  client.sktai.auth.dto.request
  - response:  client.sktai.auth.dto.response
 