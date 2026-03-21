# 학습 경로 가이드

**어떤 스킬을 어떤 순서로 설치하고 사용해야 할까?**

---

## 이 문서의 목적

6개 스킬은 각각 독립적으로 돌아가지만, 역할이나 상황에 따라 **어떤 걸 먼저 쓸지**가 달라집니다. 역할별 학습 경로 세 가지와 실제 사용 시나리오를 담았습니다.

---

## 스킬 난이도 개요

| 스킬 | 난이도 | 적합한 대상 |
|------|-------|-----------|
| `deploy-to-vercel` | ★☆☆ 초급 | 배포가 처음인 개발자 |
| `web-design-guidelines` | ★☆☆ 초급 | UI 코드 작성자 |
| `react-best-practices` | ★★★ 초~고급 | React/Next.js 개발자 |
| `composition-patterns` | ★★☆ 중급 | React 컴포넌트 설계자 |
| `react-native-skills` | ★★☆ 중~고급 | 모바일 앱 개발자 |
| `vercel-cli-with-tokens` | ★★☆ 중급 | DevOps/CI 담당자 |

아래 차트는 각 스킬의 **난이도(x축)**와 **규칙 수(y축)**를 한눈에 보여줍니다. 오른쪽 위일수록 배우면 얻는 것이 많은 스킬입니다.

```mermaid
quadrantChart
    title 스킬 난이도 vs 규칙 수
    x-axis 초급 --> 고급
    y-axis 규칙 적음 --> 규칙 많음
    quadrant-1 "고급·고밀도 (핵심)"
    quadrant-2 "초급·고밀도 (빠른 효과)"
    quadrant-3 "초급·저밀도 (진입점)"
    quadrant-4 "고급·저밀도 (심화)"
    react-best-practices: [0.75, 0.95]
    web-design-guidelines: [0.25, 0.90]
    react-native-skills: [0.65, 0.70]
    composition-patterns: [0.55, 0.45]
    vercel-cli-with-tokens: [0.60, 0.25]
    deploy-to-vercel: [0.20, 0.20]
```

---

## 역할별 학습 경로

### 경로 A: React/Next.js 개발자

"성능 잘 나오는 React 앱, AI 에이전트랑 같이 만들고 싶다"

```mermaid
flowchart TD
    A["1단계 (필수)\nreact-best-practices\n코드 생성 시 자동으로 64개 성능 규칙 적용"]
    B["2단계 (권장)\ncomposition-patterns\n컴포넌트 아키텍처 개선 (boolean prop 문제 해결)"]
    C["3단계 (선택)\nweb-design-guidelines\nUI 코드 접근성·성능 감사"]
    D["4단계 (선택)\ndeploy-to-vercel\n'배포해줘' 한 마디로 Vercel 배포"]

    A -->|권장| B
    B -->|선택| C
    C -->|선택| D

    style A fill:#1a1a2e,color:#e0e0ff,stroke:#6c63ff,stroke-width:2px
    style B fill:#16213e,color:#e0e0ff,stroke:#4a90d9,stroke-width:2px
    style C fill:#0f3460,color:#e0e0ff,stroke:#4a90d9,stroke-dasharray:5 5
    style D fill:#0f3460,color:#e0e0ff,stroke:#4a90d9,stroke-dasharray:5 5
```

**설치 명령:**

```bash
for skill in react-best-practices composition-patterns web-design-guidelines deploy-to-vercel; do
  cp -r ~/guide/origin/agent-skills/skills/$skill ~/.claude/skills/
done
```

---

### 경로 B: React Native 개발자

"Expo/React Native 앱 성능이랑 UI, AI랑 같이 잡고 싶다"

```mermaid
flowchart TD
    A["1단계 (필수)\nreact-native-skills\n모바일 성능 최적화 30+ 규칙 자동 적용"]
    B["2단계 (권장)\ncomposition-patterns\n컴포넌트 아키텍처 패턴 (React Native에도 동일 적용)"]
    C["3단계 (선택)\ndeploy-to-vercel\n웹 포털이나 API 서버가 있다면 Vercel 배포 지원"]

    A -->|권장| B
    B -->|선택| C

    style A fill:#1a1a2e,color:#e0e0ff,stroke:#6c63ff,stroke-width:2px
    style B fill:#16213e,color:#e0e0ff,stroke:#4a90d9,stroke-width:2px
    style C fill:#0f3460,color:#e0e0ff,stroke:#4a90d9,stroke-dasharray:5 5
```

**설치 명령:**

```bash
for skill in react-native-skills composition-patterns; do
  cp -r ~/guide/origin/agent-skills/skills/$skill ~/.claude/skills/
done
```

---

### 경로 C: 배포 담당자 / DevOps

"Vercel 배포 자동화하고, CI/CD에서 에이전트가 알아서 굴러가게 하고 싶다"

```mermaid
flowchart TD
    A["1단계 (필수)\ndeploy-to-vercel\n일반 개발 환경에서 '배포해줘' 한 마디로 배포"]
    B["2단계 (CI/CD)\nvercel-cli-with-tokens\n토큰 기반 인증으로 자동화 스크립트에서 배포\nGitHub Actions, 자동화 파이프라인에 적합"]

    A -->|"CI/CD 환경이라면"| B

    style A fill:#1a1a2e,color:#e0e0ff,stroke:#6c63ff,stroke-width:2px
    style B fill:#16213e,color:#e0e0ff,stroke:#4a90d9,stroke-width:2px
```

**설치 명령:**

```bash
for skill in deploy-to-vercel vercel-cli-with-tokens; do
  cp -r ~/guide/origin/agent-skills/skills/$skill ~/.claude/skills/
done
```

---

### 경로 D: 풀스택 개발자 (전체 설치)

```bash
# 모든 스킬 한 번에 설치
npx skills add vercel-labs/agent-skills

# 또는 수동으로
for skill in react-best-practices composition-patterns react-native-skills web-design-guidelines deploy-to-vercel vercel-cli-with-tokens; do
  cp -r ~/guide/origin/agent-skills/skills/$skill ~/.claude/skills/
done
```

---

## 스킬 연결 관계

아래 그래프는 스킬 간 **기반·확장·독립** 관계를 보여줍니다. 화살표 방향은 "이 스킬이 저 스킬을 확장한다"는 의미입니다.

```mermaid
graph TD
    rbp["react-best-practices\n(기반 성능 규칙 · 64개)"]
    cp["composition-patterns\n(컴포넌트 구조 · React 공통)"]
    rns["react-native-skills\n(모바일 특화 규칙 · 30+개)"]
    wdg["web-design-guidelines\n(UI 품질 독립 감사 · 100+개)"]
    dtv["deploy-to-vercel\n(일반 환경 배포)"]
    vct["vercel-cli-with-tokens\n(CI/CD 토큰 배포)"]

    rbp -->|"확장"| cp
    cp -->|"모바일 특화 확장"| rns
    wdg:::independent
    dtv -->|"상호 보완 (환경에 따라 선택)"| vct

    classDef independent fill:#1e3a2f,color:#a8ffcb,stroke:#2ecc71,stroke-dasharray:6 3
    classDef default fill:#1a1a2e,color:#e0e0ff,stroke:#6c63ff,stroke-width:2px
```

---

## 시나리오별 실행 가이드

### 시나리오 1: "새 Next.js 프로젝트 시작"

```
1. react-best-practices 설치
2. Claude에게: "Next.js 앱에서 사용자 목록 페이지 만들어줘"
   → 에이전트가 자동으로:
      - Promise.all로 병렬 데이터 페칭
      - dynamic import로 번들 최적화
      - React.cache()로 서버 캐싱
      - useMemo로 리렌더 최적화
```

### 시나리오 2: "기존 컴포넌트 리팩토링"

```
1. composition-patterns 설치
2. Claude에게: "이 컴포넌트 boolean prop 너무 많아. 리팩토링해줘"
   → 에이전트가 자동으로:
      - Compound Component 패턴 제안
      - State Provider로 state lift
      - 명시적 variant 컴포넌트로 분리
```

### 시나리오 3: "React Native 앱 리스트 성능 개선"

```
1. react-native-skills 설치
2. Claude에게: "FlatList 스크롤이 너무 버벅여. 최적화해줘"
   → 에이전트가 자동으로:
      - FlashList로 교체
      - renderItem 콜백 호이스팅
      - 인라인 객체 제거
      - 아이템 메모이제이션
```

### 시나리오 4: "UI 접근성 감사"

```
1. web-design-guidelines 설치
2. Claude에게: "src/components/ 접근성 체크해줘"
   → 에이전트가 자동으로:
      - 최신 가이드라인 fetch
      - 100+ 규칙으로 파일 분석
      - file:line 형식으로 위반 사항 보고
```

### 시나리오 5: "Vercel에 빠르게 배포"

```
1. deploy-to-vercel 설치
2. Claude에게: "이 프로젝트 Vercel에 배포해줘"
   → 에이전트가 자동으로:
      - git remote, .vercel/, CLI 인증 상태 확인
      - 최적의 방법 선택 (Git Push / CLI / Fallback)
      - 팀 선택 후 배포
      - Preview URL 반환
```

### 시나리오 6: "CI/CD에서 자동 배포"

```
1. vercel-cli-with-tokens 설치
2. Claude에게: "VERCEL_TOKEN이 있어. GitHub Actions에서 Vercel 배포 설정해줘"
   → 에이전트가 자동으로:
      - 환경변수에서 토큰 탐지
      - 안전한 토큰 사용 방법 적용
      - CI 환경에 맞는 배포 스크립트 생성
```

---

## 우선순위 선택 기준

**React/Next.js 코드 품질이 가장 중요하다면**:
→ `react-best-practices` + `composition-patterns`

**모바일 앱을 만들고 있다면**:
→ `react-native-skills`

**UI 품질과 접근성이 중요하다면**:
→ `web-design-guidelines`

**빠른 배포가 필요하다면**:
→ `deploy-to-vercel`

**자동화 환경에서 배포한다면**:
→ `vercel-cli-with-tokens`

---

## 스킬 활성화 확인

설치 후 Claude Code에서 이렇게 테스트해볼 수 있습니다:

```bash
# 설치된 스킬 확인
ls ~/.claude/skills/

# 테스트 (react-best-practices)
# Claude Code에서: "React에서 두 개의 독립적인 API를 호출하는 방법 보여줘"
# → Promise.all 패턴을 자동으로 사용하면 스킬이 활성화된 것입니다

# 테스트 (deploy-to-vercel)
# Claude Code에서: "이 프로젝트 배포해줘"
# → 프로젝트 상태를 확인하고 배포 방법을 안내하면 스킬이 활성화된 것입니다
```
