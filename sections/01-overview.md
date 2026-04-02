# Vercel Agent Skills 개요

## 원본 저장소 역할

- repo: `agent-skills`
- source: `https://github.com/vercel-labs/agent-skills.git`
- latest synced commit: `d8d9f624bc54`
- one-line summary: **AI 코딩 에이전트의 반복 작업을 skill pack으로 확장하는 저장소**

## 이번 판단

기존 가이드는 6개 스킬 구조를 중심으로 잘 읽히지만, 현재 upstream을 기준으로 보면 frontdoor에서 한 가지가 빠진다.

바로 **`react-view-transitions`를 포함한 현재형 skill map**이다.

그래서 이번 개정은 문장 몇 개를 다듬는 게 아니라, 이 저장소를 이렇게 다시 읽게 만드는 데 목적이 있다.

- 단순한 스킬 목록이 아니라
- 작업 레인별 전문성 pack이고
- 지금은 7개 스킬 축으로 읽는 편이 더 정확하다

## 최근 upstream 커밋

- `d8d9f62 Refine react-view-transition skill to include details about loading.tsx`
- `8de1770 Specify nextjs canary relationship better in react-view-transition skill`
- `5a4b5e1 Add more patterns to react-view-transition skill`
- `b8dbce9 Add limitation note to react-view-transition skill`
- `48bda1c Refine react-view-transition skill`
- `8c56b3d Refine react-view-transition skill`

## 원본에서 확인한 핵심 현실

### 1. 이 저장소는 설치 가능한 skill pack이다

핵심 구조는 간단하다.

- `skills/` — 실제 설치하는 스킬
- `packages/` — 빌드/보조 도구
- `AGENTS.md`, `CLAUDE.md` — 에이전트 표면용 메타 문서

즉 이 저장소는 블로그형 문서 모음이 아니라, **에이전트에게 전문 지식을 꽂아 넣는 배포 단위**다.

### 2. 현재 핵심은 7개 스킬 축이다

현재 upstream README 기준 주요 스킬은 다음과 같다.

- `react-best-practices`
- `web-design-guidelines`
- `react-native-guidelines`
- `react-view-transitions`
- `composition-patterns`
- `vercel-deploy-claimable`
- `vercel-cli-with-tokens`

즉 기존 가이드 독자가 예전 6개 프레임만 기억하고 있으면, **View Transition 관련 최신 축을 놓치게 된다.**

### 3. 읽는 기준은 프레임워크보다 작업 레인이 더 중요하다

실제로는 이렇게 묶어 기억하는 편이 낫다.

- React 성능 / 데이터 페칭 레인
- 컴포넌트 구조 레인
- 모바일 앱 레인
- UI 감사 레인
- 전환 애니메이션 레인
- Vercel 배포 레인

이렇게 보면 각 스킬이 “무슨 이름인지”보다 **언제 꺼낼지**가 더 빨리 보인다.

### 4. 최근 업데이트의 무게 중심은 view transition 축이다

최근 커밋 대부분이 `react-view-transitions` 쪽에 몰려 있다.

이건 작은 사실이 아니다. 지금 upstream에서 강조되는 최신 주제가 무엇인지 보여 주는 신호다.

## 지금 학습자가 먼저 기억해야 할 것

1. Agent Skills는 에이전트에 꽂는 지식 패키지다.
2. 이 저장소는 문서집이 아니라 설치 가능한 skill pack 저장소다.
3. 현재는 6개보다 7개 스킬 축으로 읽는 편이 정확하다.
4. 스킬은 이름보다 작업 레인으로 기억하는 편이 실전에서 더 강하다.
5. 최근 업스트림 변화는 `react-view-transitions`를 주목하라고 말하고 있다.
