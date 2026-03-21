# Agent Skills 용어 사전

**Vercel Agent Skills 관련 핵심 용어 30+ 개**

---

## A

### Agent Skill (에이전트 스킬)

AI 코딩 에이전트(Claude Code, Cursor, Copilot 등)에 심어두는 **전문 지식 패키지**. SKILL.md 파일을 중심으로 구성되며, 에이전트가 특정 도메인의 모범 사례를 꺼내 쓰도록 한다.

- **관련 파일**: `SKILL.md`, `AGENTS.md`
- **설치 위치**: `~/.claude/skills/` (Claude Code)

### AGENTS.md

스킬의 **컴파일된 전체 가이드** 파일. 여러 규칙 파일(`rules/*.md`)을 하나로 합친 결과물. 에이전트가 스킬의 모든 규칙을 한 번에 참조할 수 있게 한다.

- **생성 방법**: `packages/react-best-practices-build`의 빌드 도구가 만들어냄
- **직접 편집 금지**: 소스는 `rules/*.md`이고, `AGENTS.md`는 빌드 산출물

### async-defer-await

`react-best-practices` 스킬의 규칙. `await`를 실제로 값이 필요한 지점까지 미뤄서 불필요한 직렬 실행(Waterfall)을 방지한다.

---

## B

### barrel import (배럴 임포트)

여러 모듈을 하나의 `index.ts`에서 re-export하는 패턴. 편리하지만 번들러가 tree-shaking을 못 해 **번들 크기가 폭증**하는 원인이 된다.

- **금지 규칙**: `bundle-barrel-imports` (react-best-practices)

```typescript
// 배럴 임포트 (금지)
import { Button, Modal } from '@/components';

// 직접 임포트 (권장)
import { Button } from '@/components/Button';
```

### bundle-dynamic-imports

무거운 컴포넌트를 `next/dynamic`으로 지연 로딩하는 규칙. 초기 번들에 포함되지 않아 첫 로드 속도를 개선한다.

---

## C

### Claim URL (클레임 URL)

`deploy-to-vercel` 스킬의 no-auth 배포 방식에서 반환되는 URL. 인증 없이 배포된 프로젝트를 **본인 Vercel 계정으로 이전(소유권 주장)**할 수 있는 링크.

```
Claim URL: https://vercel.com/claim-deployment?code=...
```

### Claude Code

Anthropic이 만든 AI 코딩 에이전트 CLI. Agent Skills를 `~/.claude/skills/`에 설치해 확장한다.

### Compound Component (컴파운드 컴포넌트)

여러 서브컴포넌트가 공유 Context로 상태를 나눠 쓰는 React 패턴. Boolean prop 남용을 피하는 데 가장 직접적인 구조.

```tsx
<Dialog>
  <Dialog.Trigger>열기</Dialog.Trigger>
  <Dialog.Content>
    <Dialog.Header>제목</Dialog.Header>
  </Dialog.Content>
</Dialog>
```

- **관련 규칙**: `architecture-compound-components` (composition-patterns)

### Context Interface (컨텍스트 인터페이스)

`state`, `actions`, `meta`를 구분해 정의한 React Context 타입. 소비자가 어떤 값을 쓸 수 있는지 한눈에 파악할 수 있다.

- **관련 규칙**: `state-context-interface` (composition-patterns)

---

## D

### deploy.sh

`deploy-to-vercel` 스킬에 포함된 배포 스크립트. Vercel CLI 인증 없이 프로젝트를 배포할 때 쓴다 (no-auth fallback).

- **경로**: `skills/deploy-to-vercel/resources/deploy.sh`
- **claude.ai 샌드박스 사용**: `bash /mnt/skills/user/deploy-to-vercel/resources/deploy.sh`

---

## F

### FlashList

`@shopify/flash-list` 라이브러리의 React Native 리스트 컴포넌트. FlatList보다 빠른 재사용 가능 셀(recyclable) 방식으로 동작한다.

- **관련 규칙**: `list-performance-virtualize` (react-native-skills)

### forwardRef

React 18 이하에서 ref를 자식 컴포넌트에 전달하기 위한 HOC. **React 19에서 더 이상 필요 없음** — ref를 일반 prop으로 전달 가능.

- **관련 규칙**: `react19-no-forwardref` (composition-patterns)

---

## G

### GestureDetector

React Native Gesture Handler의 컴포넌트. 터치 제스처를 Reanimated와 결합해 JS 스레드 블로킹 없이 부드러운 애니메이션을 구현한다.

- **관련 규칙**: `animation-gesture-detector-press` (react-native-skills)

---

## I

### Impact Level (영향도)

스킬 규칙의 우선순위 등급. 높을수록 먼저 적용해야 한다.

| 등급 | 의미 |
|------|------|
| `CRITICAL` | 성능/기능에 심각한 영향. 즉시 수정 필요 |
| `HIGH` | 유의미한 성능 개선. 높은 우선순위 |
| `MEDIUM` | 적당한 개선. 여유 있을 때 적용 |
| `LOW` | 점진적 개선. 코드 품질 향상 |

---

## K

### kebab-case

스킬 디렉토리명 및 스크립트 파일명의 네이밍 컨벤션. 예: `deploy-to-vercel`, `react-best-practices`, `deploy.sh`.

---

## L

### LegendList

React Native 고성능 리스트 라이브러리. FlashList와 함께 가상화 리스트로 권장된다.

- **관련 규칙**: `list-performance-virtualize` (react-native-skills)

### linked (링크드)

Vercel CLI에서 로컬 프로젝트가 Vercel 프로젝트에 연결된 상태. `.vercel/project.json` 또는 `.vercel/repo.json`이 존재하면 linked 상태.

---

## M

### metadata.json

스킬 폴더에 포함된 메타데이터 파일. 스킬의 버전, 저자, 설명 등을 담는다.

```json
{
  "name": "react-best-practices",
  "version": "1.0.0",
  "author": "vercel",
  "abstract": "React/Next.js 성능 최적화 가이드"
}
```

### memoization (메모이제이션)

값이나 컴포넌트를 캐싱해 불필요한 재계산/리렌더를 막는 기법. `useMemo`, `useCallback`, `React.memo`가 대표적.

- **관련 규칙**: `rerender-memo`, `list-performance-item-memo`

---

## N

### no-auth fallback (인증 없는 폴백)

`deploy-to-vercel` 스킬에서 Vercel CLI 인증이 불가능한 환경(claude.ai 샌드박스 등)에서 사용하는 배포 방법. 인증 없이도 Preview URL과 Claim URL을 반환한다.

---

## P

### passive event listener (패시브 이벤트 리스너)

스크롤 이벤트에 `{ passive: true }` 옵션을 달아 브라우저에게 `preventDefault()`를 쓰지 않겠다고 알리는 기법. 스크롤 성능이 눈에 띄게 좋아진다.

- **관련 규칙**: `client-passive-event-listeners` (react-best-practices)

### prefers-reduced-motion

사용자가 OS에서 설정한 모션 감소 접근성 설정. CSS `@media (prefers-reduced-motion: reduce)`로 감지해 애니메이션을 비활성화해야 한다.

- **관련 규칙**: web-design-guidelines의 Animation 카테고리

### Preview URL (프리뷰 URL)

Vercel에서 프로덕션이 아닌 배포에 생성되는 임시 URL. 모든 브랜치 push 또는 `vercel deploy`로 생성된다.

### Promise.all

여러 비동기 작업을 병렬로 실행하는 JavaScript 메서드. Waterfall(직렬 실행)을 방지하는 핵심 패턴.

- **관련 규칙**: `async-parallel` (react-best-practices)

---

## R

### React.cache()

React 19+의 서버 컴포넌트에서 같은 요청 내 함수 결과를 캐싱하는 API. 여러 컴포넌트가 같은 데이터를 요청해도 실제 호출은 한 번만 일어난다.

- **관련 규칙**: `server-cache-react` (react-best-practices)

### Reanimated

React Native에서 고성능 애니메이션을 구현하는 라이브러리. UI 스레드에서 직접 실행되어 JS 스레드 블로킹 없이 60fps 애니메이션을 구현한다.

### RSC (React Server Component)

서버에서 렌더링되는 React 컴포넌트. 클라이언트 번들에 포함되지 않아 번들 크기를 줄일 수 있다. Next.js 13+의 기본 컴포넌트 타입.

### rules/ (규칙 폴더)

각 스킬의 개별 규칙 파일이 담긴 폴더. 파일명은 `area-description.md` 형식 (예: `async-parallel.md`, `rendering-activity.md`).

---

## S

### sections.md (_sections.md)

`rules/` 폴더 내 특수 파일. 각 섹션의 제목, 영향도, 설명을 정의하는 메타데이터 파일. 파일명이 `_`로 시작해 빌드 시 규칙 파일로 처리되지 않는다.

### shared value (Reanimated Shared Value)

Reanimated에서 JS 스레드와 UI 스레드 모두에서 접근 가능한 값. `useSharedValue()`로 생성하며, `.value` 속성으로 읽고 쓴다.

- **관련 규칙**: `react-compiler-reanimated-shared-values` (react-native-skills)

### SKILL.md

Agent Skill의 핵심 파일. 에이전트가 이 스킬을 어떻게 쓸지 정의한다. frontmatter에 `name`, `description`을 담으며, 에이전트가 언제 스킬을 꺼낼지 판단하는 트리거 역할을 한다.

```markdown
---
name: skill-name
description: 스킬 설명 (트리거 문구 포함)
---
```

### skills add (npx skills add)

Agent Skills를 설치하는 CLI 명령. `npx skills add vercel-labs/agent-skills`로 전체 스킬 패키지를 설치한다.

### Suspense (React Suspense)

React의 비동기 로딩 처리 컴포넌트. `<Suspense fallback={<Loading />}>`으로 데이터 페칭 중 로딩 UI를 보여주고, 스트리밍 렌더링을 가능하게 한다.

- **관련 규칙**: `async-suspense-boundaries` (react-best-practices)

---

## T

### template.md (_template.md)

새 규칙 파일을 만들 때 복사해서 사용하는 템플릿 파일. `_`로 시작해 빌드에서 제외된다.

### tree-shaking

번들러가 사용되지 않는 코드를 번들에서 제거하는 최적화. barrel import를 사용하면 tree-shaking이 제대로 동작하지 않을 수 있다.

---

## V

### vca_ 토큰

Vercel 액세스 토큰의 접두사. `VERCEL_TOKEN` 환경변수에 설정해 CLI 인증에 사용한다.

- **토큰 생성**: `vercel.com/account/tokens`
- **보안 규칙**: `--token` 플래그로 전달하지 말고 환경변수로만 사용

### vercel link --repo

프로젝트를 Vercel에 연결하는 CLI 명령. git remote URL을 기반으로 Vercel 프로젝트를 찾아 연결한다. `vercel link`(디렉토리명 기반)보다 정확하다.

### VERCEL_ORG_ID / VERCEL_PROJECT_ID

두 환경변수를 모두 설정하면 `.vercel/` 디렉토리 없이도 Vercel CLI가 프로젝트를 식별할 수 있다. CI/CD 환경에서 유용하다.

---

## W

### Waterfall (폭포수 문제)

따로 실행해도 되는 비동기 작업이 줄줄이 직렬로 실행되는 패턴. 그 수만큼 실행 시간이 곱해진다.

- **해결**: `Promise.all()`, `async-parallel` 규칙 (react-best-practices)

---

## Z

### Zeego

React Native에서 네이티브 드롭다운 및 컨텍스트 메뉴를 구현하는 라이브러리. iOS/Android 플랫폼 네이티브 메뉴 API를 사용한다.

- **관련 규칙**: `ui-menus` (react-native-skills)

---

## 파일 구조 참고

```
skills/{skill-name}/
├── SKILL.md          # 스킬 정의 (frontmatter + 사용 방법)
├── AGENTS.md         # 컴파일된 전체 가이드 (빌드 산출물)
├── README.md         # 사람이 읽는 구조 설명
├── metadata.json     # 버전, 저자 등 메타데이터
└── rules/
    ├── _sections.md  # 섹션 메타데이터 (빌드 제외)
    ├── _template.md  # 새 규칙 템플릿 (빌드 제외)
    └── area-description.md  # 개별 규칙 파일
```
