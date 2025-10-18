sktai feignclient가 MutiPart를 지원할 수 있도록 소스 수정해줘
- SpringFormEncoder
- @RequestPart의 사용필요 유무
- Content-Type: multipart/form-data 설정  
- @PostMapping(value = "/api/v1/knowledge/custom_scripts", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)에서 consumes = MediaType.MULTIPART_FORM_DATA_VALUE 삭제 필요여부
- projectId와 createdBy 파라미터는 추가하지 말아줘
  
  