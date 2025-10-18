타입 안전성을 최우선으로 고려(Object 타입 대신 구체적 Generic DTO 사용) 했는데, Object Type이 많아서 https://aip-stg.sktai.io/api/v1/model/openapi.json확인 해서 반영해줘

모든 JPA 쿼리에 자동으로 특정 공통 주석으로 Controller → Service → Repository 호출 전체 CallChain 까지도 SQL 주석으로 남기고 싶어

모든 JPA 쿼리에 자동으로 특정 공통 주석으로 serviceimpl명.method명.Repository명.method명을 추가하여 DB서버에 호출할 수 있도록
JPA로 db호출시 sql에 serviceimpl.method 주석을 포함하여 호출하는 방법


JPA 호출시 자동으로 SQL에 레포지토리명.메소드(레포지토리를 호출한 최종 서비스명.메소드)를 주석에 포함하는 방법 
- 테스트 코드는 작성 불필요


모든 JPA 쿼리에 자동으로  공통 주석으로 serviceimpl명.method명.Repository명.method명을 추가하여 DB서버에 호출할 수 있도록 반영해줘
- 테스트 코딩 작성 금지
- 수동주석 설정 유틸리티 불필요
- @SqlComment 어노테이션 (선택사항) 불필요
- Service는 Repostitory를 호출하는  메소드를 정확히 표시
- DML(Insert, update, Delete)은 트랜잭션 처리을 고려하여 반영
  - Hibernate의 동작 방식을 고려
  
- Service의 한메소드에서 repository를 다수 호출할 수도 있음을 고려
- Hibernate가 생성하는 Default주석은 삭제

제 동작을 확인하기 위해 간단한 테스트 클래스는 삭제

은 지적입니다! SQL 코멘트 시스템이 잘 작동하고 있지만, INSERT 문에는 코멘트가 추가되지 않는 문제가 있네요.

이는 Hibernate의 동작 방식 때문입니다. INSERT 문의 경우 다른 쿼리들과는 다른 시점에서 실행되며, 특히 @Transactional 경계에서 flush될 때 실행되기 때문에 컨텍스트 정보가 손실될 수 있습니다.

현재 SQL 코멘트 시스템을 확인하고 개선해보겠습니다.

Read AutoSqlCommentInspector.java

Read SqlCommentAspect.java, lines 1 to 50

문제를 파악했습니다. INSERT 문이 실행되는 시점에서 SqlCommentUtil의 ThreadLocal 컨텍스트가 정리되어 있기 때문입니다.

해결 방법을 위해 SqlCommentAspect를 개선하겠습니다. Service 메서드가 끝날 때까지 컨텍스트를 유지하도록 수정하겠습니다