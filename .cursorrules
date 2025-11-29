# 프로젝트: AI 주식 예측 서비스 (Investlio)

## 기술 스택
- **프레임워크**: Next.js 16 (App Router)
- **언어**: TypeScript
- **스타일링**: Tailwind CSS 4, Shadcn UI
- **인증**: Better-Auth
- **상태 관리**: React Query (@tanstack/react-query)
- **데이터베이스**: Supabase (필요 시)
- **차트**: TradingView JS
- **패키지 매니저**: Bun
- **유효성 검사**: Zod
- **린팅/포매팅**: Biome
- **테스트**: Vitest

## 아키텍처: FSD (Feature-Sliced Design)
참고: [Next.js와 함께 사용하는 FSD](https://feature-sliced.design/kr/docs/guides/tech/with-nextjs)

### 계층 (엄격한 순서)
1. **app**: 애플리케이션 전역 설정, 스타일, 프로바이더.
2. **views**: 엔티티, 기능, 위젯을 조합하여 전체 페이지를 구성하는 계층. (Next.js `pages` 디렉토리와 충돌 방지)
3. **widgets**: 엔티티와 기능을 결합하여 의미 있는 블록(예: 헤더, 사이드바, 피드)을 구성하는 계층.
4. **features**: 사용자 상호작용 기능 (예: 인증, 검색, 장바구니 담기).
5. **entities**: 비즈니스 엔티티 (예: 사용자, 주식, 상품).
6. **shared**: 재사용 가능한 코드, UI 키트, API 클라이언트, 타입.

### 규칙
- **단방향 의존성**: 상위 계층은 하위 계층만 임포트할 수 있습니다.
    - `features`는 `entities`와 `shared`를 임포트할 수 있습니다.
    - `entities`는 `shared`를 임포트할 수 있습니다.
    - `shared`는 상위 계층을 절대 임포트할 수 없습니다.
- **공개 API**: 모든 슬라이스 간의 임포트는 해당 슬라이스의 `index.ts` (Public API)를 통해서만 이루어져야 합니다.
    - ❌ `import { User } from '@entities/user/model/types'`
    - ✅ `import { User } from '@entities/user'`
- **슬라이스 패턴**: [슬라이스 및 세그먼트](https://feature-sliced.design/kr/docs/reference/slices-segments) 가이드를 따릅니다.
    - 일반적인 세그먼트: `ui`, `model` (스토어/액션), `lib` (유틸리티), `api`.

## 코딩 표준
- **제로 결합도, 높은 응집도**: 독립적인 모듈을 지향합니다.
- **단일 책임 원칙 (SRP)**: 엄격하게 준수합니다.
- **Server Actions**: 모든 데이터 변형(Mutation)은 Server Actions를 사용합니다.
- **React Query**:
    - 타입 안전성과 재사용성을 위해 `queryOptions` 및 `mutationOptions` 팩토리를 사용합니다.
- **타입 안전성**: 모든 스키마 검증(API 응답, 폼)에 **Zod**를 사용합니다.
- **테스트**: 단위 및 통합 테스트에 **Vitest**를 사용합니다.

## 디렉토리 구조 예시
```
src/
  app/
  views/
    home/
      ui/
        Page.tsx
      index.ts
  widgets/
    stock-chart/
      ui/
      model/
      index.ts
  features/
    auth/
      login/
      register/
  entities/
    stock/
      model/
      ui/
  shared/
    ui/
    api/
    lib/
```
