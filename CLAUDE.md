# CLAUDE.md

## 명령어 (Bun)
- **개발 서버**: `bun run dev`
- **빌드**: `bun run build`
- **시작**: `bun run start`
- **린트**: `bun run lint` (Biome)
- **포맷**: `bun run format` (Biome)
- **테스트**: `bun run test` (Vitest)
- **타입 체크**: `bun x tsc --noEmit`

## 기술 스택
- **프레임워크**: Next.js 16 (App Router)
- **언어**: TypeScript
- **스타일링**: Tailwind CSS 4, Shadcn UI
- **인증**: Better-Auth
- **상태 관리**: React Query
- **패키지 매니저**: Bun

## 코딩 규칙 (FSD)
- **아키텍처**: Feature-Sliced Design (app > views > widgets > features > entities > shared)
- **임포트**: 상위 레이어에서 하위 레이어로만 임포트 가능. (shared는 아무것도 임포트 불가)
- **공개 API**: 각 슬라이스의 `index.ts`를 통해서만 외부로 노출.
- **서버 액션**: 데이터 변형(Mutation)은 Server Actions 사용.
- **타입 안전성**: Zod 스키마 검증 필수.
- **스타일**: Tailwind CSS 4 사용.
