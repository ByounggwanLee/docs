# VSCode Spring Boot 개발 환경 설정 가이드

## 📑 목차
1. [사전 준비사항](#1-사전-준비사항)
2. [필수 확장 프로그램](#2-필수-확장-프로그램)
3. [Spring Boot 전용 확장 프로그램](#3-spring-boot-전용-확장-프로그램)
4. [개발 생산성 도구](#4-개발-생산성-도구)
5. [데이터베이스 관련 도구](#5-데이터베이스-관련-도구)
6. [코드 품질 및 테스트 도구](#6-코드-품질-및-테스트-도구)
7. [VSCode 설정](#7-vscode-설정)
8. [프로젝트 설정](#8-프로젝트-설정)
9. [디버깅 설정](#9-디버깅-설정)
10. [유용한 단축키](#10-유용한-단축키)

---

## 1. 사전 준비사항

### Java Development Kit (JDK) 설치
Spring Boot 개발을 위해서는 JDK가 필요합니다.

```bash
# JDK 버전 확인
java -version
javac -version

# 환경변수 확인
echo %JAVA_HOME%
```

**권장 JDK 버전:**
- **JDK 17 LTS** (현재 주류)
- **JDK 21 LTS** (최신 LTS)
- **JDK 11 LTS** (레거시 프로젝트)

### Maven / Gradle 설치 (선택사항)
- **Maven**: VSCode Extension에서 내장 지원
- **Gradle**: VSCode Extension에서 내장 지원
- 별도 설치 시 시스템 PATH 설정 필요

---

## 2. 필수 확장 프로그램

### 🔥 Java 개발 핵심 팩
**Extension Pack for Java** (`vscjava.vscode-java-pack`)
- 이 하나만 설치하면 Java 개발에 필요한 모든 확장 프로그램이 포함됩니다.

포함된 확장 프로그램들:
- **Language Support for Java™ by Red Hat** (`redhat.java`)
- **Debugger for Java** (`vscjava.vscode-java-debug`)
- **Test Runner for Java** (`vscjava.vscode-java-test`)
- **Maven for Java** (`vscjava.vscode-maven`)
- **Project Manager for Java** (`vscjava.vscode-java-dependency`)
- **Visual Studio IntelliCode** (`visualstudioexptteam.vscodeintellicode`)

### 📝 코드 품질 도구
- **SonarLint** (`sonarsource.sonarlint-vscode`)
  - 코드 품질 실시간 검사
  - 보안 취약점 및 버그 패턴 감지

- **Checkstyle for Java** (`shengchen.vscode-checkstyle`)
  - Java 코딩 스타일 검사
  - Google, Sun 등 표준 스타일 가이드 지원

---

## 3. Spring Boot 전용 확장 프로그램

### 🌱 Spring Boot 개발 도구
- **Spring Boot Extension Pack** (`pivotal.vscode-spring-boot`)
  - Spring Boot 개발에 최적화된 확장 프로그램 팩

포함된 확장 프로그램들:
- **Spring Boot Tools** (`pivotal.vscode-spring-boot`)
  - application.properties/yml 자동완성
  - Spring Boot 설정 파일 검증
  - Live Hover 정보 제공

- **Spring Initializr Java Support** (`vscjava.vscode-spring-initializr`)
  - VSCode에서 직접 Spring Boot 프로젝트 생성
  - `Ctrl+Shift+P` → "Spring Initializr"

- **Spring Boot Dashboard** (`vscjava.vscode-spring-boot-dashboard`)
  - Spring Boot 애플리케이션 관리 대시보드
  - 실행 중인 앱 모니터링

### 🔧 추가 Spring 도구
- **YAML** (`redhat.vscode-yaml`)
  - application.yml 파일 구문 강조 및 검증

- **XML** (`redhat.vscode-xml`)
  - pom.xml, web.xml 등 XML 파일 지원

---

## 4. 개발 생산성 도구

### 🚀 코드 생성 및 리팩토링
- **Lombok Annotations Support for VS Code** (`gabrielbb.vscode-lombok`)
  - Lombok 어노테이션 인식 및 자동완성
  - @Getter, @Setter, @Builder 등 지원

- **Auto Rename Tag** (`formulahendry.auto-rename-tag`)
  - HTML/XML 태그 자동 수정 (Thymeleaf 템플릿용)

- **Bracket Pair Colorizer 2** (`coenraads.bracket-pair-colorizer-2`)
  - 괄호 색상 구분으로 코드 구조 파악

### 📦 패키지 관리
- **Gradle for Java** (`vscjava.vscode-gradle`)
  - Gradle 빌드 도구 통합 지원

- **Maven for Java** (`vscjava.vscode-maven`)
  - Maven 빌드 도구 통합 지원 (Java Pack에 포함)

---

## 5. 데이터베이스 관련 도구

### 🗄 데이터베이스 연결 및 관리
- **Database Client** (`cweijan.vscode-database-client2`)
  - MySQL, PostgreSQL, Oracle, SQL Server 지원
  - 테이블 조회, 쿼리 실행, ERD 생성

- **SQLTools** (`mtxr.sqltools`)
  - 다양한 데이터베이스 연결
  - SQL 쿼리 작성 및 실행

- **MySQL** (`formulahendry.vscode-mysql`)
  - MySQL 전용 클라이언트

### 📊 JPA 및 Hibernate 도구
- **JPA Buddy** (`jpabuddy.jpa-buddy-vscode`)
  - JPA 엔티티 시각화
  - Spring Data JPA 리포지토리 자동 생성

---

## 6. 코드 품질 및 테스트 도구

### 🧪 테스트 도구
- **Test Runner for Java** (`vscjava.vscode-java-test`)
  - JUnit, TestNG 테스트 실행 (Java Pack에 포함)

- **Coverage Gutters** (`ryanluker.vscode-coverage-gutters`)
  - 코드 커버리지 시각화

### 📈 성능 분석
- **Java Profiler** (`dgileadi.java-profiler`)
  - 메모리 사용량 및 성능 프로파일링

---

## 7. VSCode 설정

### settings.json 설정
```json
{
  // Java 관련 설정
  "java.home": "C:\\Program Files\\Java\\jdk-17",
  "java.configuration.runtimes": [
    {
      "name": "JavaSE-11",
      "path": "C:\\Program Files\\Java\\jdk-11"
    },
    {
      "name": "JavaSE-17",
      "path": "C:\\Program Files\\Java\\jdk-17"
    }
  ],
  
  // Spring Boot 설정
  "spring-boot.ls.problem.application-properties.enabled": true,
  "spring-boot.ls.problem.application-yaml.enabled": true,
  
  // 코드 포맷팅
  "java.format.settings.url": "https://raw.githubusercontent.com/google/styleguide/gh-pages/eclipse-java-google-style.xml",
  "java.format.onType.enabled": true,
  "java.saveActions.organizeImports": true,
  
  // 자동 완성
  "java.completion.enabled": true,
  "java.completion.overwrite": true,
  "java.completion.guessMethodArguments": true,
  
  // 파일 연결
  "files.associations": {
    "*.properties": "spring-boot-properties",
    "*.yml": "spring-boot-properties-yaml"
  },
  
  // 에디터 설정
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.organizeImports": true
  },
  
  // Maven 설정
  "maven.executable.path": "C:\\tools\\apache-maven\\bin\\mvn.cmd",
  "maven.terminal.useJavaHome": true,
  
  // Gradle 설정
  "java.gradle.buildServer.enabled": "on"
}
```

### extensions.json (프로젝트별 권장 확장)
```json
{
  "recommendations": [
    "vscjava.vscode-java-pack",
    "pivotal.vscode-spring-boot",
    "sonarsource.sonarlint-vscode",
    "gabrielbb.vscode-lombok",
    "cweijan.vscode-database-client2",
    "redhat.vscode-yaml"
  ]
}
```

---

## 8. 프로젝트 설정

### Spring Boot 프로젝트 생성
1. **Command Palette 열기**: `Ctrl+Shift+P`
2. **"Spring Initializr: Create a Maven/Gradle Project" 선택**
3. **프로젝트 설정**:
   - Spring Boot 버전 선택
   - Group Id: `com.example`
   - Artifact Id: `demo`
   - 의존성 선택 (Web, JPA, Security 등)

### 프로젝트 구조 예시
```
demo/
├── .vscode/
│   ├── settings.json
│   ├── launch.json
│   └── extensions.json
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/demo/
│   │   │       ├── DemoApplication.java
│   │   │       ├── controller/
│   │   │       ├── service/
│   │   │       ├── repository/
│   │   │       └── entity/
│   │   └── resources/
│   │       ├── application.yml
│   │       ├── static/
│   │       └── templates/
│   └── test/
├── pom.xml (또는 build.gradle)
└── README.md
```

---

## 9. 디버깅 설정

### launch.json 설정
```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "java",
      "name": "Spring Boot-DemoApplication",
      "request": "launch",
      "cwd": "${workspaceFolder}",
      "mainClass": "com.example.demo.DemoApplication",
      "projectName": "demo",
      "args": "",
      "envFile": "${workspaceFolder}/.env",
      "vmArgs": "-Dspring.profiles.active=dev"
    },
    {
      "type": "java",
      "name": "Debug (Attach)",
      "request": "attach",
      "hostName": "localhost",
      "port": 5005
    }
  ]
}
```

### 원격 디버깅 설정
```bash
# JVM 시작 시 디버그 옵션 추가
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 -jar app.jar
```

---

## 10. 유용한 단축키

### 🔧 일반 개발
| 단축키 | 기능 |
|--------|------|
| `Ctrl+Shift+P` | Command Palette |
| `Ctrl+Shift+O` | 파일 내 심볼 이동 |
| `Ctrl+T` | 워크스페이스 심볼 검색 |
| `F12` | 정의로 이동 |
| `Shift+F12` | 모든 참조 찾기 |
| `Ctrl+K+Ctrl+0` | 모든 코드 접기 |
| `Ctrl+K+Ctrl+J` | 모든 코드 펼치기 |

### ☕ Java 전용
| 단축키 | 기능 |
|--------|------|
| `Ctrl+Shift+O` | Import 구성 |
| `Ctrl+.` | Quick Fix (자동 수정) |
| `Shift+Alt+O` | 사용하지 않는 Import 제거 |
| `Ctrl+Shift+R` | 리팩토링 메뉴 |
| `F2` | 이름 바꾸기 |

### 🌱 Spring Boot 전용
| 단축키 | 기능 |
|--------|------|
| `Ctrl+F5` | Spring Boot 앱 실행 |
| `Shift+F5` | Spring Boot 앱 중지 |
| `F5` | 디버그 모드로 실행 |

---

## 11. 추가 유용한 도구

### 📄 문서화 도구
- **Java Doc Comments** (`madhavd1.javadoc-tools`)
  - JavaDoc 자동 생성 및 포맷팅

- **Markdown All in One** (`yzhang.markdown-all-in-one`)
  - README.md 작성 도구

### 🔄 버전 관리
- **GitLens** (`eamodio.gitlens`)
  - Git 기능 강화

- **Git History** (`donjayamanne.githistory`)
  - Git 히스토리 시각화

### 🎨 테마 및 아이콘
- **Material Icon Theme** (`pkief.material-icon-theme`)
  - 파일/폴더 아이콘 테마

- **One Dark Pro** (`zhuangtongfa.material-theme`)
  - 인기 있는 다크 테마

---

## 12. 트러블슈팅

### 자주 발생하는 문제들

1. **Java 경로 인식 문제**
   ```json
   // settings.json에 명시적 경로 설정
   "java.home": "C:\\Program Files\\Java\\jdk-17"
   ```

2. **Lombok 인식 안됨**
   - Lombok Annotations Support 확장 설치
   - IDE에서 annotation processing 활성화

3. **Spring Boot 자동완성 안됨**
   - Spring Boot Tools 확장 설치 확인
   - application.properties/yml 파일 형식 확인

4. **Maven/Gradle 빌드 실패**
   - Java 버전 호환성 확인
   - 네트워크 프록시 설정 확인

---

## 13. 성능 최적화 팁

### VSCode Java 성능 향상
```json
{
  "java.jdt.ls.vmargs": "-noverify -Xmx2G -XX:+UseG1GC -XX:+UseStringDeduplication",
  "java.configuration.maven.userSettings": "C:\\Users\\{username}\\.m2\\settings.xml",
  "java.import.gradle.offline.enabled": true
}
```

### 메모리 사용량 최적화
- 불필요한 확장 프로그램 비활성화
- 큰 프로젝트의 경우 exclude 패턴 설정
- Auto Save 간격 조정

---

## 14. 참고 리소스

### 공식 문서
- [VSCode Java 개발 가이드](https://code.visualstudio.com/docs/java/java-tutorial)
- [Spring Boot VSCode 확장](https://spring.io/guides/gs/sts/)

### 추천 학습 자료
- Spring Boot 공식 문서
- VSCode Java 확장 팩 GitHub
- Java 개발 베스트 프랙티스

---

**🎯 이제 VSCode에서 Spring Boot 개발을 시작할 준비가 완료되었습니다!** 🚀

각 확장 프로그램을 순서대로 설치하고 설정을 적용하면 효율적인 Spring Boot 개발 환경을 구축할 수 있습니다.
