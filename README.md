# React Deployment 학습 프로젝트

이 프로젝트는 React 애플리케이션의 배포 방법에 대해 학습하기 위한 프로젝트입니다.

## 📚 학습 내용

### 1. React 애플리케이션 빌드

React 애플리케이션을 배포하기 위해서는 먼저 프로덕션용 빌드를 생성해야 합니다.

```bash
npm run build
```

이 명령어는 다음과 같은 작업을 수행합니다:

- 코드 최적화 및 압축
- CSS 및 JavaScript 번들링
- 정적 파일들을 `build/` 폴더에 생성

### 2. 배포 플랫폼

#### Firebase Hosting 🔥

Firebase Hosting은 Google에서 제공하는 정적 웹사이트 호스팅 서비스입니다.

**설치 및 설정:**

```bash
# Firebase CLI 설치
npm install -g firebase-tools

# Firebase 로그인
firebase login

# 프로젝트 초기화
firebase init

# 배포
firebase deploy
```

**Firebase 설정 파일:**

- `.firebaserc`: Firebase 프로젝트 설정
- `firebase.json`: 호스팅 구성 설정

#### 기타 배포 플랫폼

1. **Netlify**

   - GitHub 연동으로 자동 배포
   - 무료 티어 제공
   - 간단한 설정

2. **Vercel**

   - Next.js 개발사에서 제공
   - 빠른 배포와 성능 최적화
   - 자동 HTTPS

3. **GitHub Pages**
   - GitHub 리포지토리 직접 호스팅
   - 무료 사용 가능
   - `gh-pages` 패키지 활용

### 3. 배포 전 체크리스트

- [ ] 프로덕션 빌드 생성 (`npm run build`)
- [ ] 환경 변수 설정 확인
- [ ] API 엔드포인트 프로덕션 URL로 변경
- [ ] 최적화 및 성능 테스트
- [ ] 브라우저 호환성 확인
- [ ] SEO 메타 태그 설정

### 4. 환경 변수 관리

프로덕션 환경에서는 민감한 정보를 환경 변수로 관리해야 합니다.

```javascript
// 개발 환경
const API_URL = process.env.REACT_APP_API_URL || 'http://localhost:3001';

// .env.production.local
REACT_APP_API_URL=https://api.production.com
```

### 5. 성능 최적화

#### Code Splitting

```javascript
import { lazy, Suspense } from "react";

const LazyComponent = lazy(() => import("./LazyComponent"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}
```

#### 이미지 최적화

- WebP 형식 사용
- 적절한 이미지 크기
- Lazy loading 구현

## 🚀 프로젝트 실행

### 개발 서버 실행

```bash
npm start
```

### 프로덕션 빌드

```bash
npm run build
```

### 로컬에서 프로덕션 빌드 테스트

```bash
npx serve -s build
```

## 📁 프로젝트 구조

```
react-deployment/
├── public/
│   ├── index.html
│   └── ...
├── src/
│   ├── components/
│   ├── pages/
│   ├── App.js
│   └── index.js
├── build/              # 빌드 결과물 (배포용)
├── .gitignore
├── package.json
└── README.md
```

## 🔧 사용된 기술

- **React**: 프론트엔드 라이브러리
- **React Router**: 클라이언트 사이드 라우팅
- **CSS Modules**: 스타일링
- **Firebase Hosting**: 배포 플랫폼

## 📝 배포 과정에서 배운 점

1. **빌드 과정의 중요성**: 개발 환경과 프로덕션 환경의 차이점 이해
2. **환경 변수 관리**: 보안과 설정 관리의 중요성
3. **성능 최적화**: 사용자 경험 향상을 위한 최적화 기법
4. **배포 자동화**: CI/CD 파이프라인의 필요성
5. **모니터링**: 배포 후 애플리케이션 상태 확인의 중요성

## 🔗 참고 자료

- [Create React App - Deployment](https://create-react-app.dev/docs/deployment/)
- [Firebase Hosting 가이드](https://firebase.google.com/docs/hosting)
- [React 성능 최적화](https://reactjs.org/docs/optimizing-performance.html)

---

이 프로젝트를 통해 React 애플리케이션의 배포 과정과 관련 기술들을 학습할 수 있습니다.
