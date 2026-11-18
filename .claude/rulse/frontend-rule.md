---
paths: 
   - "src/components/**/*, src/app/**/*.tsx"
---

# Frontend Rules

## 스택
- Next.js 14 (App Router), TypeScript strict mode
- 스타일링: Tailwind CSS만 사용, CSS-in-JS 금지
- 상태 관리: 서버 상태는 TanStack Query, 클라이언트 상태는 Zustand
- 폼: react-hook-form + zod validation

## 컴포넌트 컨벤션
- 컴포넌트는 함수형 컴포넌트만 사용, class component 금지
- 파일명은 PascalCase (예: UserProfile.tsx), 폴더명은 kebab-case
- 하나의 파일에는 하나의 컴포넌트만 export
- Props 타입은 반드시 interface로 정의하고 `ComponentNameProps` 형식으로 네이밍

## 임포트 순서
1. React / Next.js 관련
2. 외부 라이브러리
3. 내부 절대경로 (@/components, @/lib 등)
4. 상대경로
5. 타입 임포트는 항상 마지막

## 절대 하지 말 것
- `useEffect` 안에서 데이터 fetching 하지 말 것 (TanStack Query 사용)
- inline style 사용 금지
- `any` 타입 사용 금지, 불가피하면 `unknown` + 타입가드
- 새 라이브러리 임의로 설치 금지 (이미 date-fns 있음, dayjs 추가 금지 등)

## 접근성
- 모든 인터랙티브 요소는 키보드 접근 가능해야 함
- 이미지에는 alt 텍스트 필수

## 테스트
- 새 컴포넌트 작성 시 `*.test.tsx` 파일 함께 생성
- Testing Library 사용, 구현 디테일 대신 사용자 관점으로 테스트