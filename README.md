# Vercel Agent Skills 학습 가이드

Vercel Labs의 Agent Skills는 “에이전트에게 규칙을 몇 개 더 알려주는 부가자료”가 아니다. 이 저장소의 핵심은 **프레임워크별/작업별 지식을 SKILL.md 형식으로 패키징해서, AI 코딩 에이전트가 적절한 순간에 꺼내 쓰게 하는 것**이다.

이 가이드는 원본 저장소를 직접 대조해, 각 스킬을 단순 소개하는 데서 멈추지 않고 **왜 이 저장소를 skill pack으로 읽어야 하는지 / 어떤 스킬이 어떤 작업 레인에 대응하는지 / 최근 upstream 변화가 어디에 있는지**를 다시 정리한다.

---

## 현재 기준선

- upstream repo: `vercel-labs/agent-skills`
- latest synced commit: `d8d9f624bc54`
- 현재 frontdoor에서 먼저 기억해야 할 변화:
  - 이제 핵심은 **6개가 아니라 7개 스킬**로 읽는 편이 맞다
  - 최근 업데이트의 중심은 `react-view-transitions` 보강이다
  - 저장소는 `skills/`와 `packages/`로 나뉘며, 보통 설치 대상은 `skills/` 쪽이다

---

## 이 저장소를 한 문장으로 말하면

**React, Next.js, React Native, UI 감사, Vercel 배포 같은 반복 작업을 에이전트가 더 잘 수행하게 만드는 skill pack 저장소**다.

핵심은 두 가지다.

1. 스킬이 **작업 맥락을 감지하면 자동으로 발화**된다는 점
2. 각 스킬이 단순 팁 모음이 아니라 **실무 규칙과 보조 스크립트가 묶인 패키지**라는 점

즉 이 저장소는 “예제 모음”보다 **작업별 전문성 확장 레이어**에 가깝다.

---

## 왜 지금 다시 봐야 하나

### 1. 현재 upstream은 7개 스킬 축으로 읽어야 한다

기존 가이드는 6개 스킬을 중심으로 잘 정리되어 있었다. 하지만 현재 upstream README에는 다음 스킬들이 전면에 잡힌다.

- `react-best-practices`
- `web-design-guidelines`
- `react-native-guidelines`
- `react-view-transitions`
- `composition-patterns`
- `vercel-deploy-claimable`
- `vercel-cli-with-tokens`

즉 지금은 **React View Transition API / Next.js view transition 흐름**이 새로운 핵심 축으로 들어왔다.

### 2. 이 저장소는 “문서집”이 아니라 설치 가능한 skill pack이다

원본 구조를 보면 핵심은 다음과 같다.

- `skills/` — 실제 설치 대상 스킬들
- `packages/` — 빌드/컴파일 도구
- `AGENTS.md`, `CLAUDE.md` — 에이전트 표면과 메타 지식

즉 사용자는 문서를 읽고 끝나는 게 아니라, **스킬을 실제 에이전트에 설치해 동작시키는 것**이 목적이다.

### 3. 스킬을 개별 문서가 아니라 작업 레인으로 읽어야 한다

이 저장소를 잘 쓰려면 “스킬 이름 외우기”보다, 먼저 어떤 레인이 필요한지 구분하는 게 낫다.

- **React 성능 레인** — `react-best-practices`
- **컴포넌트 구조 레인** — `composition-patterns`
- **모바일 구현 레인** — `react-native-guidelines`
- **UI 품질 감사 레인** — `web-design-guidelines`
- **전환 애니메이션 레인** — `react-view-transitions`
- **배포 레인** — `vercel-deploy-claimable`, `vercel-cli-with-tokens`

이렇게 보면 각 스킬의 쓰임새가 훨씬 선명해진다.

---

## 지금 가장 먼저 봐야 할 것

### 1. React / Next.js 최적화가 필요하면

- `react-best-practices`
- `composition-patterns`
- 필요 시 `react-view-transitions`

### 2. 모바일 앱이면

- `react-native-guidelines`
- 필요 시 `composition-patterns`

### 3. UI 품질 검토면

- `web-design-guidelines`

### 4. 배포 자동화면

- `vercel-deploy-claimable`
- `vercel-cli-with-tokens`

---

## 추천 읽기 순서

1. `sections/01-overview.md` — 이 저장소를 현재 기준으로 어떻게 읽어야 하는지
2. `01-learning-paths.md` — 역할별/작업별 진입 경로
3. `categories/overview.md` — 업스트림 구조와 최근 변화
4. 각 스킬 category 문서
5. `02-glossary.md` — 형식과 용어 정리

---

## 흔한 오해

### 오해 1 — 스킬은 그냥 긴 프롬프트다

아니다. 스킬은 구조화된 지식 패키지이며, 경우에 따라 스크립트와 메타데이터까지 포함한다.

### 오해 2 — 이 저장소는 React 팁 모음집이다

아니다. React 계열 비중이 크긴 하지만, 모바일·UI 감사·배포·view transition까지 별도 레인이 있다.

### 오해 3 — 가이드에 있는 스킬 수가 곧 현재 upstream 현실이다

아니다. 이 저장소는 비교적 빠르게 변하고, 지금은 `react-view-transitions`를 포함한 7개 스킬 구조로 읽는 편이 더 정확하다.

---

## 다음 문서

- 현재 구조를 먼저 잡으려면 `sections/01-overview.md`
- 어떤 스킬을 어떤 순서로 써야 할지 보려면 `01-learning-paths.md`
- 개별 스킬 해설은 `categories/` 문서들로 이어진다

<!-- GUIDE_SYNC:START -->
## 자동 동기화 상태

- origin repo: `agent-skills`
- latest source commit: `ce3e64e468f8`
- sync mode: `update`
- 영향 분류: 스킬/플러그인

### 이번 반영 포인트

origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: 스킬/플러그인.

### 최근 upstream 커밋

- `ce3e64e Merge pull request #231 from tonypan2/tonypan/vercel-cli-sp-awareness`
- `77a6a14 vercel-cli-with-tokens: fix 5 real bugs + document Stripe Projects plan changes`

### 변경 파일 샘플

- `skills/vercel-cli-with-tokens.zip`
- `skills/vercel-cli-with-tokens/SKILL.md`

> 이 블록은 guide sync가 자동 갱신합니다.
<!-- GUIDE_SYNC:END -->
