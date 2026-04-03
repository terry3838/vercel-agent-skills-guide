# Upstream Snapshot — agent-skills

- source repo: `https://github.com/vercel-labs/agent-skills.git`
- previous synced commit: `d8d9f624bc54beaf7af9a5033d41d90aa49d7f5a`
- current synced commit: `73140fc5b3a214ad3222bcf557b397b3c02d11c1`
- sync mode: `update`
- impact labels: 스킬/플러그인, 소스코드
- guide repo: `vercel-agent-skills-guide`

## 원본 한줄 요약

A collection of skills for AI coding agents. Skills are packaged instructions and scripts that extend agent capabilities.

## recent upstream commits

- `73140fc Refine react-view-transition skill`
- `1a5a9a0 Refine patterns in view-transitions-skill`
- `992d7f6 Merge pull request #212 from vercel-labs/shu/Cb1db`
- `93f5a2d new rule`
- `bed2162 Refine react-view-transition skill`
- `01bec29 Tweak react-view-transition skill`
- `3755c87 Refine react-view-transition to specify no need for react canary`
- `a7b34e8 Remove references from react-view-transition`

## top-level structure

- `AGENTS.md`
- `CLAUDE.md`
- `packages/`
- `README.md`
- `skills/`

## changed files

- `packages/react-best-practices-build/test-cases.json`
- `skills/react-best-practices.zip`
- `skills/react-best-practices/AGENTS.md`
- `skills/react-best-practices/SKILL.md`
- `skills/react-best-practices/rules/advanced-effect-event-deps.md`
- `skills/react-view-transitions.zip`
- `skills/react-view-transitions/AGENTS.md`
- `skills/react-view-transitions/README.md`
- `skills/react-view-transitions/SKILL.md`
- `skills/react-view-transitions/metadata.json`
- `skills/react-view-transitions/references/css-recipes.md`
- `skills/react-view-transitions/references/implementation.md`
- `skills/react-view-transitions/references/nextjs.md`
- `skills/react-view-transitions/references/patterns.md`

## README excerpt

```md
# Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

## Available Skills

### react-best-practices

React and Next.js performance optimization guidelines from Vercel Engineering. Contains 40+ rules across 8 categories, prioritized by impact.

**Use when:**
- Writing new React components or Next.js pages
- Implementing data fetching (client or server-side)
- Reviewing code for performance issues
- Optimizing bundle size or load times

**Categories covered:**
- Eliminating waterfalls (Critical)
- Bundle size optimization (Critical)
- Server-side performance (High)
- Client-side data fetching (Medium-High)
- Re-render optimization (Medium)
- Rendering performance (Medium)
- JavaScript micro-optimizations (Low-Medium)

### web-design-guidelines

Review UI code for compliance with web interface best practices. Audits your code for 100+ rules covering accessibility, performance, and UX.

**Use when:**
- "Review my UI"
- "Check accessibility"
- "Audit design"
- "Review UX"
- "Check my site against best practices"

**Categories covered:**
- Accessibility (aria-labels, semantic HTML, keyboard handlers)
- Focus States (visible focus, focus-visible patterns)
- Forms (autocomplete, validation, error handling)
- Animation (prefers-reduced-motion, compositor-friendly transforms)
- Typography (curly quotes, ellipsis, tabular-nums)
- Images (dimensions, lazy loading, alt text)
- Performance (virtualization, layout thrashing, preconnect)
- Navigation & State (URL reflects state, deep-linking)
- Dark Mode & Theming (color-scheme, theme-color meta)
- Touch & Interaction (touch-action, tap-highlight)
- Locale & i18n (Intl.DateTimeFormat, Intl.NumberFormat)

### react-native-guidelines

React Native best practices optimized for AI agents. Contains 16 rules across 7 sections covering performance, architecture, and platform-specific patterns.

**Use when:**
- Building React Native or Expo apps
- Optimizing mobile performance
- Implementing animations or gestures
- Working with native modules or platform APIs

**Categories covered:**
- Performance (Critical) - FlashList, memoization, heavy computation
- Layout (High) - flex patterns, safe areas, keyboard handling
- Animation (High) - Reanimated, gesture handling
- Images (Medium) - expo-image, caching, lazy loading
- State Management (Medium) - Zustand patterns, React Compiler
- Architecture (Medium) - monorepo structure, imports
- Platform (Medium) - iOS/Android specific patterns

### react-view-transitions

Implement smooth, native-feeling animations using React's View Transition API. Covers the `<ViewTransition>` component, `addTransitionType`, transition types, and Next.js integration including the `transitionTypes` prop on `next/link`.

**Use when:**
- Adding page transitions or route animations
- Animating enter/exit of components
- Creating shared element transitions (list-to-detail morphing)
- Implementing directional (forward/back) navigation animations
- Integrating view transitions in Next.js App Router
- Animating list reorder or Suspense fallback reveals

**Topics covered:**
- `<ViewTransition>` component (enter, exit, update, share triggers)
- `addTransitionType` for directional/context-specific animations
- View Transition Classes and CSS pseudo-elements
- Shared element transitions with the `name` prop
- JavaScript animations via Web Animations API
- Next.js `transitionTypes` prop on `next/link`
- Ready-to-use CSS animation recipes (fade, slide, scale, flip)
- Accessibility (`prefers-reduced-motion`)

### composition-patterns

React composition patterns that scale. Helps avoid boolean prop proliferation through compound components, state lifting, and internal composition.

**Use when:**
- Refactoring components with many boolean props
- Building reusable component libraries
- Designing flexible APIs
- Reviewing component architecture

**Patterns covered:**
- Extracting compound components
- Lifting state to reduce props
- Composing internals for flexibility
- Avoiding prop drilling

### vercel-deploy-claimable

Deploy applications and websites to Vercel instantly. Designed for use with claude.ai and Claude Desktop to enable deployments directly from conversations. Deployments are "claimable" - users can transfer ownership to their own Vercel account.

**Use when:**
- "Deploy my app"
- "Deploy this to production"
- "Push this live"
- "Deploy and give me the link"

**Features:**
- Auto-detects 40+ frameworks from `package.json`
```
