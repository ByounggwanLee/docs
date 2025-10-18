# React 개발환경 설정 가이드

## 📑 목차
1. [사전 준비사항](#1-사전-준비사항)
   - [Node.js 설치](#nodejs-설치)
   - [pnpm 설치 (권장)](#pnpm-설치-권장)
   - [권장 개발 도구](#권장-개발-도구)
2. [React 프로젝트 생성 방법](#2-react-프로젝트-생성-방법)
   - [방법 1: Create React App (CRA)](#방법-1-create-react-app-cra)
   - [방법 2: Vite](#방법-2-vite)
   - [방법 3: Next.js](#방법-3-nextjs)
3. [프로젝트 구조](#3-프로젝트-구조)
   - [Create React App 기본 구조](#create-react-app-기본-구조)
   - [권장 폴더 구조](#권장-폴더-구조)
4. [필수 패키지 설치](#4-필수-패키지-설치)
   - [라우팅](#라우팅)
   - [상태 관리](#상태-관리)
   - [HTTP 클라이언트](#http-클라이언트)
   - [UI 라이브러리](#ui-라이브러리)
   - [개발 도구](#개발-도구)
5. [TypeScript 설정 (선택사항)](#5-typescript-설정-선택사항)
6. [개발 환경 최적화](#6-개발-환경-최적화)
   - [VSCode 확장 프로그램](#vscode-확장-프로그램)
   - [환경 변수 설정](#환경-변수-설정)
7. [빌드 및 배포](#7-빌드-및-배포)
   - [개발 서버](#개발-서버)
   - [프로덕션 빌드](#프로덕션-빌드)
   - [배포 옵션](#배포-옵션)
8. [트러블슈팅](#8-트러블슈팅)
9. [학습 리소스](#9-학습-리소스)
10. [베스트 프랙티스](#10-베스트-프랙티스)

---

## 1. 사전 준비사항

### Node.js 설치
React 개발을 위해서는 Node.js가 필요합니다.

1. [Node.js 공식 웹사이트](https://nodejs.org/)에서 LTS 버전 다운로드
2. 설치 후 터미널에서 버전 확인
```bash
node --version
npm --version
```

### pnpm 설치 (권장)
pnpm은 npm보다 빠르고 디스크 공간을 효율적으로 사용하는 패키지 매니저입니다.

**Windows에서 설치:**
```bash
# PowerShell에서 실행 (관리자 권한 권장)
iwr https://get.pnpm.io/install.ps1 -useb | iex

# 또는 npm을 통해 설치
npm install -g pnpm

# 또는 Chocolate를 사용하는 경우
choco install pnpm
```

**설치 확인:**
```bash
pnpm --version
```

**pnpm 주요 명령어:**
```bash
pnpm install          # 의존성 설치 (npm install과 동일)
pnpm add <package>     # 패키지 추가 (npm install <package>와 동일)
pnpm remove <package>  # 패키지 제거
pnpm run <script>      # 스크립트 실행
pnpm start            # 개발 서버 시작
pnpm build            # 프로덕션 빌드
```

**pnpm의 장점:**
- **속도**: npm보다 최대 2배 빠른 설치 속도
- **디스크 공간**: 중복 패키지를 하드링크로 관리하여 공간 절약
- **엄격한 의존성**: phantom dependencies 방지
- **npm 호환성**: package.json과 완전 호환

### 권장 개발 도구
- **VSCode**: React 개발에 최적화된 에디터
- **Git**: 버전 관리
- **Chrome DevTools**: 디버깅용

## 2. React 프로젝트 생성 방법

### 방법 1: Create React App (CRA)
가장 간단하고 빠른 방법입니다.

```bash
# 새 React 앱 생성
npx create-react-app my-app

# 프로젝트 디렉토리로 이동
cd my-app

# 개발 서버 시작 (npm 사용)
npm start

# 또는 pnpm 사용 (권장)
pnpm start
```

**pnpm을 사용한 전체 과정:**
```bash
# React 앱 생성
npx create-react-app my-app

# 프로젝트 디렉토리로 이동
cd my-app

# npm을 pnpm으로 변경 (선택사항)
rm package-lock.json
pnpm install

# 개발 서버 시작
pnpm start
```

**장점:**
- 설정이 간단함
- 초보자에게 적합
- Webpack, Babel 등이 자동으로 구성됨

**단점:**
- 설정 커스터마이징이 제한적
- 번들 크기가 상대적으로 큼

### 방법 2: Vite
더 빠른 개발 서버와 빌드를 제공합니다.

```bash
# npm 사용
npm create vite@latest my-react-app -- --template react
cd my-react-app
npm install
npm run dev

# pnpm 사용 (권장)
pnpm create vite my-react-app --template react
cd my-react-app
pnpm install
pnpm dev
```

**장점:**
- 매우 빠른 개발 서버
- 빠른 HMR (Hot Module Replacement)
- 작은 번들 크기

### 방법 3: Next.js
프로덕션급 React 프레임워크입니다.

```bash
# npm 사용
npx create-next-app@latest my-next-app
# TypeScript 사용 시
npx create-next-app@latest my-next-app --typescript

# pnpm 사용 (권장)
pnpm create next-app my-next-app
# TypeScript 사용 시
pnpm create next-app my-next-app --typescript

# 프로젝트 디렉토리로 이동
cd my-next-app

# 개발 서버 시작
pnpm dev  # 또는 npm run dev
```

**장점:**
- SSR/SSG 지원
- 파일 기반 라우팅
- API Routes 지원
- 최적화된 성능

## 3. 프로젝트 구조

### Create React App 기본 구조
```
my-app/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── App.js
│   ├── App.css
│   ├── index.js
│   └── index.css
├── package.json
└── README.md
```

### 권장 폴더 구조
```
src/
├── components/          # 재사용 가능한 컴포넌트
│   ├── common/         # 공통 컴포넌트
│   └── ui/             # UI 컴포넌트
├── pages/              # 페이지 컴포넌트
├── hooks/              # 커스텀 훅
├── services/           # API 호출 함수
├── utils/              # 유틸리티 함수
├── styles/             # 스타일 파일
└── assets/             # 이미지, 폰트 등
```

## 4. 필수 패키지 설치

### 라우팅
```bash
# npm 사용
npm install react-router-dom

# pnpm 사용 (권장)
pnpm add react-router-dom
```

### 상태 관리
```bash
# Redux Toolkit (권장)
npm install @reduxjs/toolkit react-redux
# 또는 pnpm으로
pnpm add @reduxjs/toolkit react-redux

# 또는 Zustand (간단한 경우)
npm install zustand
# 또는 pnpm으로
pnpm add zustand
```

### HTTP 클라이언트
```bash
# npm 사용
npm install axios

# pnpm 사용 (권장)
pnpm add axios
```

### UI 라이브러리
```bash
# Material-UI
npm install @mui/material @emotion/react @emotion/styled
# 또는 pnpm으로
pnpm add @mui/material @emotion/react @emotion/styled

# 또는 Ant Design
npm install antd
# 또는 pnpm으로
pnpm add antd

# 또는 Chakra UI
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
# 또는 pnpm으로
pnpm add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

### 개발 도구
```bash
# ESLint, Prettier (코드 품질)
npm install --save-dev eslint prettier
# 또는 pnpm으로
pnpm add -D eslint prettier

# Testing
npm install --save-dev @testing-library/react @testing-library/jest-dom
# 또는 pnpm으로
pnpm add -D @testing-library/react @testing-library/jest-dom
```

## 5. TypeScript 설정 (선택사항)

### 새 프로젝트에서 TypeScript 사용
```bash
npx create-react-app my-app --template typescript
```

### 기존 프로젝트에 TypeScript 추가
```bash
npm install --save typescript @types/node @types/react @types/react-dom
```

## 6. 개발 환경 최적화

### VSCode 확장 프로그램
React 개발을 위한 필수 및 권장 확장 프로그램들입니다.

#### 🔥 필수 확장 프로그램
- **ES7+ React/Redux/React-Native snippets** (`dsznajder.es7-react-js-snippets`)
  - React 컴포넌트, hooks, Redux 코드 스니펫 제공
  - `rfc`, `rafc`, `useEffect` 등 단축키로 빠른 코드 생성

- **Prettier - Code formatter** (`esbenp.prettier-vscode`)
  - 코드 자동 포맷팅으로 일관된 스타일 유지
  - 저장 시 자동 포맷팅 설정 가능

- **ESLint** (`dbaeumer.vscode-eslint`)
  - JavaScript/TypeScript 코드 품질 검사
  - 문법 오류 및 잠재적 버그 사전 검출

- **Auto Rename Tag** (`formulahendry.auto-rename-tag`)
  - HTML/JSX 태그 이름 변경 시 자동으로 닫는 태그도 함께 변경
  - JSX 작업 시 생산성 향상

#### 🎨 UI/UX 개발 도구
- **Bracket Pair Colorizer 2** (`coenraads.bracket-pair-colorizer-2`)
  - 괄호, 중괄호를 색상으로 구분하여 가독성 향상
  - 복잡한 JSX 구조 파악에 유용

- **Indent Rainbow** (`oderwat.indent-rainbow`)
  - 들여쓰기를 색상으로 구분하여 코드 구조 파악 용이

- **Color Highlight** (`naumovs.color-highlight`)
  - CSS 색상 코드를 실제 색상으로 표시

#### 🔧 개발 생산성 도구
- **Thunder Client** (`rangav.vscode-thunder-client`)
  - VSCode 내장 REST API 클라이언트
  - Postman 대신 사용 가능

- **GitLens** (`eamodio.gitlens`)
  - Git 히스토리 및 변경 사항 시각화
  - 코드 작성자 정보 표시

- **Live Server** (`ritwickdey.liveserver`)
  - 정적 파일 개발 서버 (React 개발 서버와 별도)
  - HTML/CSS 테스트용

#### 📱 React/Next.js 전용 도구
- **vscode-styled-components** (`styled-components.vscode-styled-components`)
  - styled-components 문법 하이라이팅 및 자동완성

- **Next.js snippets** (`PulkitGangwar.nextjs-snippets`)
  - Next.js 개발을 위한 코드 스니펫

- **React Native Tools** (`msjsdiag.vscode-react-native`)
  - React Native 개발 시 디버깅 도구

#### 🎯 TypeScript 개발 도구
- **TypeScript Importer** (`pmneo.tsimporter`)
  - TypeScript import 문 자동 생성

- **Auto Import - ES6, TS, JSX, TSX** (`steoates.autoimport`)
  - 모듈 자동 import 기능

#### ⚡ 추가 유용한 도구
- **Error Lens** (`usernamehw.errorlens`)
  - 에러 메시지를 코드 라인에 직접 표시

- **Code Spell Checker** (`streetsidesoftware.code-spell-checker`)
  - 코드 내 오타 검사

- **Material Icon Theme** (`pkief.material-icon-theme`)
  - 파일/폴더 아이콘 테마

- **One Dark Pro** (`zhuangtongfa.material-theme`)
  - 인기 있는 다크 테마

#### 🛠 설정 방법
1. **Extensions 탭 열기**: `Ctrl+Shift+X`
2. **확장 프로그램 검색**: 위 확장 프로그램 이름 또는 ID로 검색
3. **Install 클릭**하여 설치
4. **설정 파일 구성** (선택사항):

```json
// settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

#### 📦 확장 프로그램 팩 설치
개별 설치 대신 팩으로 한번에 설치하는 방법:

- **React Extension Pack** (`jawandarajbir.react-vscode-extension-pack`)
  - React 관련 확장 프로그램들을 한번에 설치

### 환경 변수 설정
`.env` 파일 생성:
```
REACT_APP_API_URL=http://localhost:3001
REACT_APP_VERSION=1.0.0
```

사용법:
```javascript
const apiUrl = process.env.REACT_APP_API_URL;
```

## 7. 빌드 및 배포

### 개발 서버
```bash
# npm 사용
npm start          # 개발 서버 시작

# pnpm 사용 (권장)
pnpm start         # 개발 서버 시작
# 또는 Vite 프로젝트의 경우
pnpm dev
```

### 프로덕션 빌드
```bash
# npm 사용
npm run build      # 빌드 생성
npm run serve      # 빌드된 파일 서빙 (선택사항)

# pnpm 사용 (권장)
pnpm build         # 빌드 생성
pnpm preview       # 빌드된 파일 미리보기 (Vite)
```

### 배포 옵션
- **Netlify**: 무료, 간단한 배포
- **Vercel**: Next.js에 최적화
- **GitHub Pages**: 정적 사이트 호스팅
- **AWS S3 + CloudFront**: 확장성 있는 배포

## 8. 트러블슈팅

### 자주 발생하는 문제들

1. **포트 충돌**
   ```bash
   # npm 사용
   PORT=3001 npm start
   
   # pnpm 사용
   PORT=3001 pnpm start
   ```

2. **캐시 문제**
   ```bash
   # npm 캐시 정리
   npm cache clean --force
   rm -rf node_modules package-lock.json
   npm install
   
   # pnpm 캐시 정리
   pnpm store prune
   rm -rf node_modules pnpm-lock.yaml
   pnpm install
   ```

3. **의존성 충돌**
   ```bash
   # npm 사용
   npm audit
   npm audit fix
   
   # pnpm 사용
   pnpm audit
   pnpm audit --fix
   ```

4. **pnpm 관련 문제**
   ```bash
   # pnpm 버전 업데이트
   pnpm add -g pnpm@latest
   
   # 전역 저장소 확인
   pnpm store path
   
   # 저장소 최적화
   pnpm store prune
   ```

## 9. 학습 리소스

### 공식 문서
- [React 공식 문서](https://react.dev/)
- [Create React App 문서](https://create-react-app.dev/)

### 추천 학습 사이트
- React 공식 튜토리얼
- freeCodeCamp
- React 공식 블로그

## 10. 베스트 프랙티스

1. **컴포넌트 설계**
   - 단일 책임 원칙 준수
   - 재사용 가능하게 설계
   - Props 타입 검증

2. **성능 최적화**
   - React.memo 활용
   - useMemo, useCallback 적절히 사용
   - 코드 스플리팅 적용

3. **코드 품질**
   - ESLint, Prettier 사용
   - 일관된 네이밍 컨벤션
   - 적절한 주석 작성

이제 React 개발을 시작할 준비가 완료되었습니다! 🚀