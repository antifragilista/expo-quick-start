# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Quick Start

   ```bash
   pnpm create expo-app@latest 'appname'
   ```

2. 기본 명령어 확인해보기

   ```bash
   # 앱 실행
   pnpm start

   # 패키지 추가
   pnpm add <package-name>

   # 개발 의존성 추가
   pnpm add -D <package-name>

   # 패키지 제거
   pnpm remove <package-name>

   # 패키지 업데이트
   pnpm update
   ```

## 프로젝트 구조

### 전체 개요
- **기술 스택**: Expo + React Native + TypeScript
- **라우팅**: Expo Router 파일 기반 라우팅(화면은 `app/`에서 정의)
- **기능**: 라이트/다크 테마, 탭 네비게이션, 공통 UI 컴포넌트, 이미지/폰트 에셋, 린트/TS 설정 포함

### 디렉터리 트리
```
app/
  _layout.tsx
  (tabs)/
    _layout.tsx
    index.tsx
    explore.tsx
  +not-found.tsx
assets/
  fonts/SpaceMono-Regular.ttf
  images/* (아이콘/스플래시/데모 이미지)
components/
  Collapsible.tsx
  ExternalLink.tsx
  HapticTab.tsx
  HelloWave.tsx
  ParallaxScrollView.tsx
  ThemedText.tsx
  ThemedView.tsx
  ui/
    IconSymbol.tsx
    IconSymbol.ios.tsx
    TabBarBackground.tsx
    TabBarBackground.ios.tsx
constants/
  Colors.ts
hooks/
  useColorScheme.ts
  useColorScheme.web.ts
  useThemeColor.ts
scripts/
  reset-project.js
app.json
eslint.config.js
package.json
pnpm-lock.yaml
tsconfig.json
README.md
```

### 디렉터리별 설명
- **`app/`**: 화면과 라우팅의 중심
  - **`_layout.tsx`**: 루트 레이아웃(전역 네비/테마/상태바 래핑)
  - **`(tabs)/_layout.tsx`**: 탭 네비게이션 레이아웃
  - **`(tabs)/index.tsx` · `explore.tsx`**: 탭 화면들
  - **`+not-found.tsx`**: 존재하지 않는 라우트 처리(404)
- **`components/`**: 공통 프레젠테이션/레이아웃 컴포넌트
  - **`ThemedText.tsx` · `ThemedView.tsx`**: 테마 반응형 UI
  - **`ParallaxScrollView.tsx`**: 패럴랙스 헤더 스크롤
  - **`HapticTab.tsx`**: 탭 전환 햅틱 보조
  - **`ui/`**: 플랫폼 특화 UI
    - **`IconSymbol(.ios).tsx`**, **`TabBarBackground(.ios).tsx`**
- **`assets/`**: 정적 에셋(폰트/이미지)
- **`hooks/`**: 테마/색상 관련 커스텀 훅
  - **`useColorScheme(.web).ts`**, **`useThemeColor.ts`**
- **`constants/Colors.ts`**: 테마 팔레트/공통 색상 상수
- **설정/메타**: `app.json`, `package.json`, `pnpm-lock.yaml`, `tsconfig.json`, `eslint.config.js`, `README.md`
- **`scripts/reset-project.js`**: 캐시/빌드 산출물 정리용 초기화 스크립트

### 라우팅/네비게이션 흐름 요약
- 앱 시작 시 `app/_layout.tsx`가 루트 컨테이너를 구성하고, 내부에서 `app/(tabs)/_layout.tsx`가 탭 네비게이션을 설정합니다.
- 잘못된 경로 진입 시 `app/+not-found.tsx` 화면이 표시됩니다.

### 플랫폼별 파일 규칙
- 같은 이름의 파일이 있을 때 iOS에서는 `*.ios.tsx`가 우선 사용됩니다(공통 파일이 기본).