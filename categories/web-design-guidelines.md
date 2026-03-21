# Web Design Guidelines (웹 인터페이스 가이드라인)

## 스킬 소개

이 스킬은 **웹 UI 코드를 100개 이상의 규칙으로 감사하는 에이전트 스킬**입니다. 접근성(a11y), 성능, UX, 폼 처리, 애니메이션, 국제화 등 실전 웹 개발에서 자주 놓치는 항목들을 체계적으로 점검합니다.

특이한 점: 이 스킬은 규칙을 직접 내장하지 않고, **항상 최신 가이드라인을 원격에서 fetch**합니다. 규칙이 업데이트되면 스킬도 자동으로 최신 버전을 사용합니다.

---

## 이 스킬이 필요한 이유

UI 코드 리뷰에서 접근성, 성능, UX 항목을 빠뜨리기 쉽습니다:

- `<img>`에 `alt` 속성을 빠뜨리는 경우
- 폼에 `autocomplete` 속성이 없어 모바일에서 불편한 경우
- 애니메이션에 `prefers-reduced-motion` 미처리로 접근성 위반
- 다크모드 대응 누락

이 스킬은 에이전트가 이런 항목을 **`file:line` 형식**으로 정확히 지적하도록 합니다.

---

## 스킬 메타데이터

| 항목 | 내용 |
|------|------|
| **스킬 이름** | `web-design-guidelines` |
| **버전** | 1.0.0 |
| **저자** | Vercel Engineering |
| **규칙 수** | 100+ |
| **가이드라인 소스** | [vercel-labs/web-interface-guidelines](https://github.com/vercel-labs/web-interface-guidelines) |

---

## 작동 방식

```
1. 사용자가 "UI 리뷰해줘" 또는 "접근성 체크해줘" 요청
2. 에이전트가 최신 가이드라인을 원격 URL에서 fetch
   → https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md
3. 지정한 파일(들)을 읽음
4. 100+ 규칙 모두 적용해 위반 사항 감지
5. file:line 형식으로 결과 출력
```

---

## 11개 검사 카테고리

### 1. Accessibility (접근성)

ARIA 레이블, 시맨틱 HTML, 키보드 핸들러 점검.

**주요 검사 항목:**
- 인터랙티브 요소에 `aria-label` 또는 텍스트 콘텐츠 존재 여부
- `<button>` vs `<div onClick>` 올바른 시맨틱 사용
- 이미지에 의미 있는 `alt` 속성

```html
<!-- 위반 예: aria-label 누락 -->
<button onClick={close}>×</button>

<!-- 올바른 예 -->
<button onClick={close} aria-label="닫기">×</button>
```

### 2. Focus States (포커스 상태)

포커스 표시 및 focus-visible 패턴.

```css
/* 위반 예: 포커스 제거 */
button:focus { outline: none; }

/* 올바른 예: 키보드 사용자에게만 포커스 표시 */
button:focus-visible { outline: 2px solid blue; }
button:focus:not(:focus-visible) { outline: none; }
```

### 3. Forms (폼)

자동완성, 유효성 검사, 에러 처리.

```html
<!-- 위반 예: autocomplete 누락 -->
<input type="email" name="email" />

<!-- 올바른 예 -->
<input type="email" name="email" autocomplete="email" />
```

### 4. Animation (애니메이션)

`prefers-reduced-motion`, GPU 친화적 transform 사용.

```css
/* 올바른 예: 모션 민감 사용자 배려 */
@media (prefers-reduced-motion: no-preference) {
  .card { transition: transform 0.3s ease; }
}

@media (prefers-reduced-motion: reduce) {
  .card { transition: none; }
}
```

### 5. Typography (타이포그래피)

인쇄 따옴표, 줄임표, tabular-nums.

```html
<!-- 위반 예: 직선 따옴표 -->
<p>"안녕하세요"</p>

<!-- 올바른 예: 인쇄 따옴표 -->
<p>"안녕하세요"</p>

<!-- 숫자 정렬 -->
<span style="font-variant-numeric: tabular-nums">1,234</span>
```

### 6. Images (이미지)

크기 지정, 레이지 로딩, alt 텍스트.

```html
<!-- 올바른 예 -->
<img
  src="photo.jpg"
  alt="제품 사진"
  width="400"
  height="300"
  loading="lazy"
/>
```

### 7. Performance (성능)

가상화, layout thrashing 방지, preconnect.

```html
<!-- DNS 미리 연결 -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="dns-prefetch" href="https://analytics.example.com" />
```

### 8. Navigation & State (네비게이션 & 상태)

URL이 상태를 반영, 딥링킹 지원.

```tsx
// 올바른 예: URL에 상태 반영
const [filter, setFilter] = useQueryState('filter');
```

### 9. Dark Mode & Theming (다크모드)

`color-scheme`, `theme-color` meta 태그.

```html
<meta name="color-scheme" content="light dark" />
<meta name="theme-color" content="#ffffff"
      media="(prefers-color-scheme: light)" />
<meta name="theme-color" content="#1a1a1a"
      media="(prefers-color-scheme: dark)" />
```

```css
:root {
  color-scheme: light dark;
  --bg: light-dark(#ffffff, #1a1a1a);
  --text: light-dark(#1a1a1a, #ffffff);
}
```

### 10. Touch & Interaction (터치 & 인터랙션)

`touch-action`, tap highlight 처리.

```css
/* 스크롤 성능 개선 */
.scrollable { touch-action: pan-y; }

/* iOS tap highlight 제거 (의도적으로) */
.custom-button { -webkit-tap-highlight-color: transparent; }
```

### 11. Locale & i18n (국제화)

`Intl.DateTimeFormat`, `Intl.NumberFormat` 사용.

```tsx
// 위반 예: 하드코딩된 날짜 포맷
const date = `${year}/${month}/${day}`;

// 올바른 예: Intl API
const formatter = new Intl.DateTimeFormat('ko-KR', {
  year: 'numeric', month: 'long', day: 'numeric'
});
const date = formatter.format(new Date());
```

---

## 출력 형식

에이전트는 위반 사항을 다음 형식으로 출력합니다:

```
src/components/Button.tsx:23 [접근성] button에 aria-label 또는 텍스트 콘텐츠 필요
src/pages/login.tsx:45 [폼] email input에 autocomplete="email" 추가 필요
src/styles/global.css:12 [애니메이션] prefers-reduced-motion 미처리
```

---

## 트리거 키워드

이 스킬은 다음 요청에서 자동 활성화됩니다:

- "UI 리뷰해줘" / "Review my UI"
- "접근성 체크" / "Check accessibility"
- "디자인 감사" / "Audit design"
- "UX 점검" / "Review UX"
- "베스트 프랙티스 체크" / "Check my site against best practices"

---

## 사용 예시

```
사용자: src/components/ 폴더 접근성 체크해줘

에이전트:
1. 최신 가이드라인 fetch 중...
2. src/components/ 파일 읽기...
3. 100+ 규칙 적용 중...

결과:
src/components/Modal.tsx:34 [접근성] Modal에 role="dialog"와 aria-labelledby 필요
src/components/Input.tsx:12 [폼] autocomplete 속성 누락
src/components/Button.tsx:8 [포커스] focus:not(:focus-visible) 패턴 적용 필요
```

---

## 설치 및 활성화

```bash
cp -r ~/guide/origin/agent-skills/skills/web-design-guidelines ~/.claude/skills/
```

네트워크 접근이 필요합니다. claude.ai에서 사용 시 `claude.ai/settings/capabilities`에서 허용 도메인을 추가하세요.

---

## 추가 자료

- **원본 스킬 파일**: `~/guide/origin/agent-skills/skills/web-design-guidelines/SKILL.md`
- **가이드라인 원본**: [web-interface-guidelines](https://github.com/vercel-labs/web-interface-guidelines)
