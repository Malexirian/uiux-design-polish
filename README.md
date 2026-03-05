# uiux-design-polish

Codex Skill to polish UI/UX for responsive web interfaces (desktop/mobile): visual hierarchy, spacing, typography, states (loading/empty/error), WCAG accessibility, and perceived performance.

## What this skill does
- Improves visual clarity and hierarchy (scanability, grouping, CTA priority)
- Normalizes spacing / typography via tokens and consistent rules
- Ensures complete UI states (loading/empty/error/success + focus/disabled)
- Reduces UX friction in forms and flows (error prevention + recovery)
- Applies baseline accessibility (WCAG AA mindset: keyboard, focus, labels, contrast)
- Adds a final QA + validation protocol (landing / dashboard / multi-step form)

## When to use
- A screen looks inconsistent or hard to read
- A form is confusing or causes errors/abandonment
- UI states and feedback are missing
- You need an accessibility and UI QA pass before release

## How to use
1. Copy `SKILL.md` into your Codex skills folder/bundle.
2. Invoke the skill when you’re refactoring UI, building screens, or auditing accessibility.
3. Follow the “Process (BMAD hooks + 3-pass iteration)” and “Definition of Done”.

> Tip: the `name` + `description` in the YAML front matter are key for triggering.

## Example triggers
- “Polish this screen: spacing and typography are inconsistent.”
- “Add loading/empty/error states and improve perceived performance.”
- “Audit this form for UX + WCAG and fix keyboard/focus/labels/contrast issues.”
- “Before release, run a UI/UX QA pass on these pages.”

## Status
- v0.1.0 (early): usable as-is
- Examples: coming soon (after first real-world usage)

## Contributing
Issues and PRs are welcome:
- add real before/after examples
- improve checklists and validation scenarios
- strengthen sourcing and references

## License
MIT
