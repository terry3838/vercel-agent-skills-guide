# Obsidian Vault Map

이 문서는 `vercel-agent-skills-guide` 의 repo guide 문서를 Obsidian note pack과 어떻게 대응시키는지 정리한다.

## 출력 모드

- mode: `hybrid`
- repo guide: `vercel-agent-skills-guide/`
- repo-local note pack: `obsidian/vercel-agent skills Guide/`
- live vault target: `unset`
- live sync status: `not applied`

## 안전 원칙

- repo-local pack이 정본이다.
- live vault sync는 **의도된 vault target이 명시적으로 확인된 뒤에만** 수행한다.
- default vault나 CLI 반환값은 참고 정보일 뿐, 목적지 확정 근거가 아니다.

## 매핑

| repo guide | note pack |
|---|---|
| `README.md` | `vercel-agent skills Guide/vercel-agent skills Guide - MOC.md` |
| `01-learning-paths.md` | `vercel-agent skills Guide/02 Learning Paths.md` |
| `02-glossary.md` | `vercel-agent skills Guide/03 Glossary.md` |
| `CLAUDE.md` | `vercel-agent skills Guide/Deep Dives/CLAUDE.md` |
| `categories/composition-patterns.md` | `vercel-agent skills Guide/Categories/Composition patterns.md` |
| `categories/deploy-to-vercel.md` | `vercel-agent skills Guide/Categories/Deploy to vercel.md` |
| `categories/overview.md` | `vercel-agent skills Guide/01 Overview.md` |
| `categories/react-best-practices.md` | `vercel-agent skills Guide/Categories/React best practices.md` |
| `categories/react-native-skills.md` | `vercel-agent skills Guide/Categories/React native skills.md` |
| `categories/vercel-cli-with-tokens.md` | `vercel-agent skills Guide/Categories/Vercel cli with tokens.md` |
| `categories/web-design-guidelines.md` | `vercel-agent skills Guide/Categories/Web design guidelines.md` |

## note map 의도

- MOC가 frontdoor 역할을 한다.
- Learning Paths / Glossary가 기본 3축이 된다.
- deep dive는 source-backed reading surface로 붙인다.
- References와 Workflows는 길찾기/증거를 붙잡아 둔다.
