```
---
name: uiux-design-polish
description: |
  Polishes UI/UX for responsive web interfaces (desktop/mobile): visual hierarchy, spacing, typography,
  component patterns and states (loading/empty/error), form and flow ergonomics, baseline accessibility (WCAG),
  and perceived performance. Use to refactor inconsistent/ugly screens, improve confusing forms/flows, add missing
  feedback states, or run a pre-release UI/a11y QA pass. Framework-agnostic: adapt to the current stack.
---

# uiux-design-polish

## A) Resources (for grounding + patterns)
Keep sourcing **authoritative** references. Prefer official design systems and W3C/WAI docs.

### Official design systems & guidelines
- Material Design 3 (Google) — design system — https://m3.material.io/ — Actionable: semantic tokens + state patterns + responsive layout guidance.
- Human Interface Guidelines (Apple) — platform guidelines — https://developer.apple.com/design/human-interface-guidelines/ — Actionable: navigation patterns, touch targets, clarity principles.
- Fluent 2 (Microsoft) — design system — https://fluent2.microsoft.design/ — Actionable: semantic color roles, adaptable components, density.
- Carbon Design System (IBM) — design system — https://carbondesignsystem.com/ — Actionable: component anatomy + content guidelines + spacing.
- GOV.UK Design System — gov patterns — https://design-system.service.gov.uk/ — Actionable: form errors, content patterns, accessible components.
- U.S. Web Design System (USWDS) — gov patterns — https://designsystem.digital.gov/ — Actionable: accessible component guidance + content patterns.
- Atlassian Design System — product UI patterns — https://atlassian.design/ — Actionable: spacing, typography roles, component behavior.

### UX heuristics (decision rules)
- Nielsen Norman Group — “10 usability heuristics” — https://www.nngroup.com/articles/ten-usability-heuristics/ — Actionable: visibility of system status, error prevention, consistency.
- Nielsen Norman Group — form UX articles (labels, validation, error recovery) — https://www.nngroup.com/topic/forms/ — Actionable: reduce friction + prevent errors.

### Accessibility & implementation patterns
- WCAG 2.2 (W3C) — spec — https://www.w3.org/TR/WCAG22/ — Actionable: baseline success criteria and definitions.
- WAI-ARIA Authoring Practices (APG) — patterns — https://www.w3.org/WAI/ARIA/apg/ — Actionable: keyboard interaction + roles/states for complex widgets.
- MDN Web Docs — Accessibility — https://developer.mozilla.org/en-US/docs/Web/Accessibility — Actionable: semantic HTML guidance + ARIA usage.
- WebAIM — accessibility techniques — https://webaim.org/ — Actionable: contrast, keyboard, forms.
- WAI “Understanding WCAG” — explanations — https://www.w3.org/WAI/WCAG21/Understanding/ — Actionable: practical interpretation of criteria.

### UI craft (optional but useful)
- Refactoring UI (Larson & Simon) — book/site — https://www.refactoringui.com/ — Actionable: visual hierarchy, spacing, component polish.

## 0) Contract
### Goals
- Measurably improve: **visual clarity**, **task success / error rate**, **accessibility**, **perceived performance**.
- Produce a repeatable workflow a coding agent can execute (plan → changes → QA).

### Non-goals
- Full redesign / new brand identity (unless explicitly requested).
- Pixel-perfect parity with a specific design system unless provided.

### Required outputs (always produce)
1) **UI Implementation Plan** (tokens + layout + components + states)
2) **Change List** (what will change, where, and why)
3) **QA Checklist results** (pass/fail + fixes)

## 1) When to use
- Screen looks “off” (inconsistent spacing/typography/colors), hard to scan, unclear primary action.
- Forms cause user errors or abandonment.
- Missing states: loading/empty/error/success/disabled/focus.
- Accessibility baseline is missing (keyboard/focus/labels/contrast).
- Before release: quick UI + a11y + perceived performance pass.

## 2) When to avoid
- Backend-only tasks (no UI surface).
- High-risk refactors with zero QA: do **Structure pass only** (layout/semantics) and stop.
- Ultra-throwaway prototypes where consistency is not a requirement.

## 3) Inputs (with defaults)
- platform: `web` (default) | mobile | desktop
- product_type: `app` (default) | landing | dashboard | e-commerce | tool
- audience: `pro` (default) | grand_public | expert
- brand_tone: `minimal` (default) | playful | premium | corporate
- constraints (defaults):
  - must_keep_layout: false
  - must_keep_colors: false
  - must_keep_copy: false
  - must_keep_components: false
- scope (defaults):
  - pages: ["current page"]
  - components: []
  - flow: "" (optional: “signup”, “checkout”, “settings”, …)
- quality_targets (defaults):
  - wcag_target: "AA"
  - contrast_text_min: 4.5
  - contrast_large_text_min: 3.0
  - contrast_non_text_min: 3.0
  - pointer_target_min_css_px: 24
  - pointer_target_preferred_mobile: ">=44pt (iOS) / >=48dp (Android)"
  - feedback_latency_target_ms: 100  # show some UI feedback quickly
  - avoid_layout_shift: true

If stack/framework is not specified, infer it from the codebase and stay consistent.

## 4) Process (3-pass iteration)

### Brain — clarify success
- Identify **primary user task** on the screen (1 sentence).
- Define **1 primary CTA** + up to **2 secondary actions**.
- List 3 top risks: (1) confusion, (2) errors, (3) accessibility gaps.

### Model — build the UI Implementation Plan (before editing code)
Create these artifacts (short, actionable):

1) **Design tokens**
- Spacing scale (prefer multiples of 4 or 8)
- Typography roles (H1/H2/H3, body, label, helper, caption)
- Colors as **semantic roles** (bg/surface/text/muted/primary/success/warn/danger)
- Radius, shadow/elevation, border width

2) **Layout rules**
- Container width + gutters + responsive breakpoints
- Grid strategy (stack on mobile, columns on desktop)
- Information hierarchy (what is above the fold, what is secondary)

3) **Component inventory**
- Buttons (primary/secondary/tertiary), inputs, select, checkbox, radio
- Cards, tables, alerts/toasts, modals/drawers
- Navigation (tabs/sidebar/breadcrumb) if relevant

4) **States matrix (must be explicit)**
- loading / empty / error / success
- enabled / hover / focus-visible / active / disabled
- validation states for forms

5) **Accessibility baseline**
- semantic HTML first, labels, keyboard order, focus visibility, contrast, status messages.

### Action — implement in 3 passes (stop after each pass if constraints demand it)

#### Pass 1 — Structure (layout + semantics)
- Fix DOM/semantic structure (headings, landmarks, form labels).
- Establish layout grid, consistent spacing, predictable alignment.
- Ensure CTA hierarchy is obvious in grayscale (spacing/size first, not color).

#### Pass 2 — Polish (tokens + micro-details)
- Replace one-off values with tokens (spacing, font sizes, colors, radius).
- Improve scannability: tighter grouping, consistent paddings, readable line-height.
- Add micro-interactions: hover, focus, pressed, disabled, with consistent affordances.
- Data-heavy UI: align numbers (use tabular numerals if available) and reduce visual noise.

#### Pass 3 — Accessibility + QA (must-pass checks)
- Keyboard navigation: logical order, no traps, focus visible and not obscured.
- Forms: persistent labels, inline validation, clear error copy + summary when needed.
- Contrast meets targets; interactive controls have non-text contrast.
- Status messages announced appropriately (aria-live) without stealing focus unnecessarily.

### Data — evaluate + report
- Run the QA checklists below.
- Provide a short “before/after” summary: what improved and how to verify.
- If any must-pass fails, fix before declaring done.

## 5) Do / Don’t (agent-ready rules)

### Do ✅
- Define tokens once and apply everywhere (no random 7px/11px/13px).
- Design hierarchy with **spacing + size + weight** first; color is last.
- Keep **one clear primary action** per screen; everything else is secondary/tertiary.
- Always implement full states: loading/empty/error/success + focus/disabled.
- Prefer semantic HTML controls; use ARIA only to fill real gaps.
- Make errors actionable: **what happened + how to fix**, near the field, and optionally a summary.
- Reserve space to prevent layout shift (images, async content, skeletons).

### Don’t ❌
- Don’t remove focus outlines without replacing with an accessible focus style.
- Don’t rely on color alone to communicate state (error/success/selection).
- Don’t use placeholder-only labels for forms.
- Don’t create “div buttons” or custom controls without keyboard/a11y parity.
- Don’t introduce new visual styles per component without tokenizing.

## 6) Checklists

### A) Visual UI checklist
- Tokens in place (spacing/typo/colors/radius/shadow); no one-off values.
- Consistent grid/containers; alignments are crisp; no “floating” elements.
- Typographic roles are explicit; line-height supports readability.
- Semantic colors: primary/neutral/status; consistent across screens.
- States cover: hover/focus/active/disabled + loading/empty/error/success.
- No noticeable layout shifts during load; skeletons reserve space when needed.

### B) UX + Accessibility checklist
- Flow is minimal; CTAs are unambiguous; “Back/Cancel/Undo” exists when relevant.
- Labels persist; helper text is linked; validation is progressive.
- Errors are identified in text and include suggestions when possible.
- Keyboard: logical order, focus visible, no traps, focus not obscured.
- Touch targets meet minimum; spacing prevents mis-taps.
- Status changes are announced (e.g., aria-live) when it matters.

## 7) Common anti-patterns + fixes (10)
1) Primary CTA drowned in noise → enforce a single primary CTA, reduce competing emphasis.
2) Inconsistent spacing → adopt a 4/8 scale and refactor paddings/margins to tokens.
3) “Everything bold” typography → enforce roles (title/body/label) and reduce weights.
4) Placeholder-only forms → add labels; keep placeholders as examples only.
5) Error = red text only → add error text + icon/structure; link to field; add summary if multiple.
6) Focus invisible → implement focus-visible styling with sufficient contrast.
7) Overuse of modals → prefer inline/step flows; if modal, manage focus and escape.
8) No empty states → add empty + next step; don’t show blank tables.
9) Loading with no feedback → show immediate feedback; use skeleton for large surfaces.
10) Data tables too noisy → reduce borders; align numeric columns; use tabular numerals.

## 8) Definition of Done (must-pass)
- Primary task is obvious; primary CTA is easy to find.
- All states exist (loading/empty/error/success + focus/disabled).
- Keyboard-only use is functional end-to-end on the scope.
- Contrast targets met for text and key controls.
- No critical layout shift during load in the scoped screen/flow.

## 9) Validation protocol (3 scenarios)
For each scenario:
- Provide **test steps**
- Provide **must-pass checklist**
- Provide **expected outputs** (what user sees/gets)

### Scenario 1 — Landing marketing (conversion)
Steps:
- Mobile viewport first, then desktop.
- Scan headline → value props → CTA → trust elements.
Must-pass:
- Clear hierarchy above the fold
- Primary CTA visible without hunting
- No layout shift while media loads
- Focus visible on all interactive elements

### Scenario 2 — Dashboard data (scannability)
Steps:
- Verify table/cards readability; filter/sort interactions; loading/empty/error states.
Must-pass:
- Numbers aligned; columns readable; dense UI still scannable
- States for data fetch exist (loading/empty/error)
- Keyboard can reach filters and table controls

### Scenario 3 — Multi-step form (error prevention)
Steps:
- Fill with valid + invalid inputs; trigger validation; recover; submit.
Must-pass:
- Labels persist; inline validation is clear
- Error messages explain how to fix
- Focus moves appropriately (no surprise focus jumps)
- Success state is explicit; user knows what happened

## 10) Examples (before → after)

### Example 1 — Multi-step form
Before:
- 15 fields on one screen, placeholders instead of labels, errors only in red.
After (mini checklist):
- [ ] Split into 3 logical steps (progressive disclosure)
- [ ] Persistent labels + helper text
- [ ] Inline validation + error summary when multiple errors
- [ ] Clear primary CTA per step + Back/Cancel

### Example 2 — Dashboard cards + table
Before:
- Random paddings, inconsistent headings, table hard to scan, no empty state.
After (mini checklist):
- [ ] Tokenized spacing/typography; consistent card padding
- [ ] Clear section headings and grouping
- [ ] Table noise reduced; numeric alignment improved
- [ ] Loading/empty/error states for data
```


