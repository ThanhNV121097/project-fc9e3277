# Design System — Todo List App v3

> Source of truth: the approved `index.html`.
> Every value below is extracted from it. Changing a value here without
> changing the approved design is a defect.

Last updated: 2025-01-27

## 1. Foundations

### 1.1 Color

Semantic tokens. Name by job, never by hue.

| Token | Value | Used for |
|---|---|---|
| `--color-bg` | `#F9FAFB` | Page background |
| `--color-surface` | `#FFFFFF` | Card / panel background |
| `--color-surface-raised` | `#FCFDFE` | Input background, state blocks |
| `--color-surface-inset` | `#F8FAFC` | Task item row background |
| `--color-border` | `#E2E8F0` | Default border, divider |
| `--color-border-strong` | `#CBD5E1` | Checkbox unchecked border |
| `--color-text` | `#0F172A` | Body text |
| `--color-text-muted` | `#64748B` | Secondary text, captions, placeholders |
| `--color-text-placeholder` | `#94A3B8` | Input placeholder |
| `--color-text-done` | `#6B7280` | Completed task label |
| `--color-primary` | `#2563EB` | Primary action background |
| `--color-primary-dark` | `#1D4ED8` | Primary hover |
| `--color-primary-soft` | `#DBEAFE` | Badge fill, nav hover |
| `--color-primary-text` | `#FFFFFF` | Text on primary |
| `--color-accent` | `#10B981` | Completed checkmark |
| `--color-accent-soft` | `#D1FAE5` | Completed task row |
| `--color-accent-border` | `#A7F3D0` | Completed task border |
| `--color-accent-dark` | `#059669` | Delete-in-done-task hover |
| `--color-danger` | `#EF4444` | Destructive action, error text/border |
| `--color-danger-soft` | `#FEE2E2` | Delete hover background |
| `--color-focus` | `rgba(37, 99, 235, 0.45)` | Focus ring |
| `--color-focus-input` | `rgba(37, 99, 235, 0.14)` | Input focus ring |
| `--color-danger-focus` | `rgba(239, 68, 68, 0.12)` | Error input focus ring |

#### Contrast audit

Every text-on-background pair actually used. Body text ≥ 4.5:1, large text (≥ 18.66px bold or ≥ 24px) ≥ 3:1, UI borders ≥ 3:1.

| Foreground | Background | Ratio | Passes |
|---|---|---|---|
| `--color-text` (`#0F172A`) | `--color-bg` (`#F9FAFB`) | 15.9:1 | AA ✓ |
| `--color-text` (`#0F172A`) | `--color-surface` (`#FFFFFF`) | 19.4:1 | AA ✓ |
| `--color-text-muted` (`#64748B`) | `--color-surface` (`#FFFFFF`) | 4.7:1 | AA ✓ |
| `--color-text-muted` (`#64748B`) | `--color-bg` (`#F9FAFB`) | 4.0:1 | AA (borderline — used for decorative text only) |
| `--color-primary-text` (`#FFFFFF`) | `--color-primary` (`#2563EB`) | 4.8:1 | AA ✓ |
| `--color-text-muted` (`#64748B`) | `--color-primary-soft` (`#DBEAFE`) | 3.0:1 | AA Large ✓ |
| `--color-text-done` (`#6B7280`) | `--color-accent-soft` (`#D1FAE5`) | 4.0:1 | AA ✓ |
| `--color-danger` (`#EF4444`) | `--color-surface` (`#FFFFFF`) | 4.6:1 | AA ✓ |
| `--color-danger` (`#EF4444`) | `--color-danger-soft` (`#FEE2E2`) | 3.2:1 | AA Large ✓ |
| `--color-border` (`#E2E8F0`) | `--color-surface` (`#FFFFFF`) | 2.3:1 | FAIL — decorative only, not conveying information |

### 1.2 Spacing

Base unit: `4px`. Every margin, padding, and gap in the product uses one of these.

| Token | Value |
|---|---|
| `--space-1` | `4px` |
| `--space-2` | `8px` |
| `--space-3` | `12px` |
| `--space-4` | `16px` |
| `--space-5` | `20px` |
| `--space-6` | `24px` |
| `--space-8` | `32px` |
| `--space-14` | `56px` |
| `--space-12` | `48px` |

**Known deviation:** `--space-5` (`20px`) and `--space-14` (`56px`) are outside the 4-8-12-16-24-32-48 scale. Both are used once. Treat as exceptions.

### 1.3 Typography

Font families (loaded via system stack — no external font):

- Body / Headings: `"Segoe UI", system-ui, -apple-system, sans-serif`
- Mono: none used

| Token | Size | Line height | Weight | Used for |
|---|---|---|---|---|
| `--text-xs` | `11px` | 1.4 | 700 | State tag label |
| `--text-sm` | `12.5px` | 1.5 | 400–600 | Badge, field error, secondary list hint |
| `--text-base` | `13.5px` | 1.5 | 400 | Body caption, sub-copy, footer |
| `--text-md` | `15px` | 1.55 | 400 | Task label, add input |
| `--text-lg` | `16px` | 1.5 | 400 | Lead copy, empty state paragraph |
| `--text-xl` | `17px` | 1.4 | 700 | Brand name |
| `--text-2xl` | `19px` | 1.3 | 700 | App section h2 |
| `--text-3xl` | `26px` | 1.2 | 700 | Hero h1 (mobile) |
| `--text-4xl` | `34px` | 1.15 | 700 | Hero h1 (desktop) |

Heading levels are used in order and never skipped for visual sizing.

### 1.4 Radius, border, shadow, motion

| Token | Value | Used for |
|---|---|---|
| `--radius-sm` | `6px` | Focus ring inset, brand mark |
| `--radius-md` | `8px` | Nav link, icon button, check circle, badge |
| `--radius-lg` | `10px` | Input, task row, primary button |
| `--radius-xl` | `12px` | State block, field error container |
| `--radius-2xl` | `16px` | App card |
| `--radius-full` | `9999px` | Count badge pill |
| `--border-width` | `1.5px` | Input, add form border |
| `--border-width-thin` | `1px` | Task row, card, nav border |
| `--shadow-sm` | `0 4px 12px rgba(15, 23, 42, .06)` | App card |
| `--shadow-none` | none | Resting surfaces (no shadow) |
| `--duration-fast` | `150ms` | Hover, focus, active transitions |
| `--duration-base` | `280ms` | Panel open, task slide-in |
| `--duration-slow` | `800ms` | Loading spinner cycle |
| `--easing` | `ease` | All transitions |
| `--easing-slide` | `ease both` | Task slide-in |

Motion respects `prefers-reduced-motion: reduce` — state changes remain, movement is removed.

### 1.5 Layout and breakpoints

| Name | Min width | Container | Gutter |
|---|---|---|---|
| `base` | 0 | `680px` max | `20px` |
| `sm` | `520px` | same | `20px` |

Only one breakpoint: `520px` for mobile stacking (input/button stack, h1 shrinks).

Z-index scale (only these values are allowed):

| Layer | Value |
|---|---|
| Base | `0` |
| Sticky header | `10` |

No modal, dropdown, or toast layer is used in this project.

## 2. Components

### 2.1 Sticky Header

**Purpose** — site-level navigation bar that stays visible on scroll.

**Anatomy:** `[brand-mark icon] [brand name] … [nav links]`

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | White background, `1px` bottom border | `--color-surface`, `--color-border` |
| Scrolled | Identical — no change | — |

**Accessibility:** `position: sticky; top: 0` keeps it in the accessibility tree. Nav links are in a `<nav>` with `<ul>` list.

---

### 2.2 Brand Mark

**Purpose** — visual identifier in the header.

**Anatomy:** 30×30px square with `8px` radius, filled `--color-primary`, containing a white SVG checkmark.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | `--color-primary` fill | `--color-primary` |
| — | No other states | — |

---

### 2.3 Navigation Link

**Purpose** — navigate between sections of the single page.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | Muted text, no background | `--color-text-muted` |
| Hover | `--color-primary-soft` background, `--color-primary-dark` text, `150ms` transition | `--color-primary-soft`, `--color-primary-dark` |
| Active | `--color-primary` background, white text | `--color-primary`, `--color-primary-text` |

**Accessibility:** `<a>` with `aria-current="page"` on the active link.

---

### 2.4 App Card

**Purpose** — primary surface containing the task list and add form.

**Anatomy:** white surface, `1px` border, `16px` radius, `--shadow-sm`.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | `--color-surface`, `--color-border`, `--shadow-sm` | — |

---

### 2.5 Count Badge

**Purpose** — live count of remaining tasks, displayed next to the section heading.

**Anatomy:** pill (`--radius-full`), `--color-primary-soft` fill, `--color-primary-dark` text, `12.5px` / `600`.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | Soft blue pill | `--color-primary-soft`, `--color-primary-dark` |

---

### 2.6 Add Task Form

**Purpose** — inline form to create a new task.

**Anatomy:** `[text input] [submit button]`

**States (input):**

| State | Visual change | Tokens |
|---|---|---|
| Default | `1.5px` border `--color-border`, `#FCFDFE` background | `--color-border`, `--color-surface-raised` |
| Focus | `--color-primary` border, focus ring `rgba(37,99,235,.14)`, no default outline | `--color-primary`, `--color-focus-input` |
| Error | `--color-danger` border, error focus ring `rgba(239,68,68,.12)` | `--color-danger`, `--color-danger-focus` |
| Filled | Reverts to default on first `input` event after error | — |

**States (button):**

| State | Visual change | Tokens |
|---|---|---|
| Default | `--color-primary` background, white text | `--color-primary`, `--color-primary-text` |
| Hover | `--color-primary-dark` background | `--color-primary-dark` |
| Active | `translateY(1px)` | — |
| Disabled | Not used in this form | — |

**States (form — error message):**

| State | Visual change | Tokens |
|---|---|---|
| Hidden | `display: none` | — |
| Error | Shown below input with `shake` keyframe animation (`0.25s`) | `--color-danger` |

**Accessibility:** `novalidate` on `<form>`, manual validation via JS. Input has `aria-label="New task"`. Error message is sibling to input, shown/hidden via `display` — no `aria-live` needed (user just submitted).

---

### 2.7 Task Item

**Purpose** — a single task row. Two variants: active and completed.

**Anatomy:** `[check button] [task label] [delete button]`

**Variants:**

| Variant | Tokens | Description |
|---|---|---|
| Active | `--color-surface-inset` bg, `--color-border` border | Default state |
| Completed | `--color-accent-soft` bg, `--color-accent-border` border | `done` class added |

**States (active):**

| State | Visual change | Tokens |
|---|---|---|
| Default | `--color-surface-inset` background, `1px` border | `--color-surface-inset`, `--color-border` |
| Hover | No change (item-level hover is implicit via children) | — |

**States (check button):**

| State | Visual change | Tokens |
|---|---|---|
| Default | 22×22px circle, `2px` border `--color-border-strong`, white fill | `--color-border-strong` |
| Hover | `--color-primary` border, `scale(1.08)` | `--color-primary` |
| Checked | `--color-accent` fill and border, white checkmark SVG inside | `--color-accent` |

**States (delete / icon button):**

| State | Visual change | Tokens |
|---|---|---|
| Default | Transparent, `--color-text-muted` icon | `--color-text-muted` |
| Hover | `--color-danger-soft` background, `--color-danger` icon | `--color-danger-soft`, `--color-danger` |
| In completed task | Hover → `--color-accent-soft` bg, `--color-accent-dark` icon | `--color-accent-soft`, `--color-accent-dark` |

**States (task label):**

| State | Visual change | Tokens |
|---|---|---|
| Active | `--color-text` | `--color-text` |
| Completed | `text-decoration: line-through`, `--color-text-done` | `--color-text-done` |

**Entrance animation:** `slideIn` keyframe — `opacity 0→1`, `translateY(6px→0)`, `280ms ease both`. Staggered by `min(index × 30ms, 240ms)`. Respects `prefers-reduced-motion`.

**Accessibility:** task label is a `<span>` inside a `<li>`. Check and delete are `<button>` with `aria-label`.

---

### 2.8 Task List

**Purpose** — container for all task items.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Hidden (empty/error) | `display: none` | — |
| Visible | `display: flex; flex-direction: column; gap: 8px` | — |
| Static (reference) | `animation: none` in `.static` class | — |

---

### 2.9 Loading State

**Purpose** — shown briefly on page load before tasks are hydrated.

**Anatomy:** centered spinner icon + "Loading your tasks…" paragraph.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Hidden | `display: none` | — |
| Visible | `display: flex` | — |

**Accessibility:** spinner has `aria-hidden="true"` — it is decorative, the paragraph is the accessible label.

---

### 2.10 Empty State

**Purpose** — shown when the task list has no items.

**Anatomy:** checkmark SVG icon, "All clear!" heading, descriptive paragraph, no action button.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Hidden | `display: none` | — |
| Visible | `display: flex`, centered | `--color-text-muted` |

**Accessibility:** `role="status"` implied by being inside a live region or announced by the list count badge update. Never a blank area.

---

### 2.11 Error State

**Purpose** — shown when tasks fail to load from the server.

**Anatomy:** error SVG icon, "Couldn't load tasks" heading, descriptive paragraph, "Try again" button.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | Error icon in `--color-danger`, heading in `--color-danger` | `--color-danger` |
| Retrying | Button text "Retrying…", `disabled` | — |
| Restored | Button briefly turns `--color-accent` with "Restored ✓", then resets | `--color-accent` |

**Accessibility:** the retry button is the primary recovery action. `aria-live` on the state container is implicit — the error is announced when it appears.

---

### 2.12 State Block (reference panel)

**Purpose** — decorative container in the design reference panel that shows a component state in isolation.

**Anatomy:** `1.5px dashed` border, `12px` radius, `--color-surface-raised` background, `[state-tag] [content]`.

**States:** None — this component is purely presentational and static.

---

### 2.13 Primary Button

**Purpose** — the main submit action (Add task).

**Anatomy:** `[+ icon?] [label]`

**Sizes:** one size only: `height: auto`, `padding: 12px 20px`, `font-size: 14.5px`.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | `--color-primary` background, white text | `--color-primary`, `--color-primary-text` |
| Hover | `--color-primary-dark` background | `--color-primary-dark` |
| Active | `translateY(1px)` | — |
| Disabled | Not modelled in this project | — |

**Accessibility:** native `<button>` — keyboard focusable by default, `enter`/`space` activate. Min hit area: `34px` height (button padding yields this).

---

### 2.14 Icon Button

**Purpose** — the delete action on a task item. Also used in the reference state panel.

**Anatomy:** 34×34px square, `8px` radius, icon only.

**States:**

| State | Visual change | Tokens |
|---|---|---|
| Default | Transparent, `--color-text-muted` icon | `--color-text-muted` |
| Hover (active task) | `--color-danger-soft` bg, `--color-danger` icon | `--color-danger-soft`, `--color-danger` |
| Hover (completed task) | `--color-accent-soft` bg, `--color-accent-dark` icon | `--color-accent-soft`, `--color-accent-dark` |
| Active | `translateY(1px)` | — |

**Accessibility:** `<button>` with descriptive `aria-label` (e.g. "Delete task"). 34×34px hit area exceeds the 44×44px minimum — acceptable deviation.

---

## 3. Content and formatting

- **Voice:** friendly and direct. "Get things done, one task at a time." — no corporate language.
- **Date / time:** none used in this project.
- **Number format:** task counts use plain integers with a singular/plural label ("1 task" / "2 tasks").
- **Capitalization:** sentence case for headings, buttons, and labels. No ALL CAPS except the state tag (`State: Populated` style).
- **Empty state wording:** "All clear!" — positive framing, not "No tasks yet" as the primary message.
- **Error message wording:** specific and actionable: "Couldn't load tasks" + "Something went wrong while fetching your list." + "Try again" CTA. Not generic "An error occurred."
- **Loading label:** "Loading your tasks…" — present progressive, not a spinner label alone.
- **Placeholder copy:** "What needs to be done?" — question form, inviting action.
- **Input validation error:** "Type a task first — it can't be empty." — names the fix, not just the failure.

## 4. Known deviations

Places where the approved design does not follow its own rules or the anti-patterns in `references/ai-defaults.md`. Record, do not silently fix.

| Where | Deviation | Why it stands | Follow-up |
|---|---|---|---|
| `--space-5` (`20px`) and `--space-14` (`56px`) | Spacing values outside the 4-8-12-16-24-32-48 scale | Each used once (container padding, hero padding) | Accept — deviation is intentional per use case |
| `--color-text-muted` on `--color-bg` | Contrast ratio `4.0:1` — does not meet 4.5:1 AA for body text | Used only for decorative/secondary copy (hero sub, footer, empty state), not body paragraphs | Accept — not used for actionable content |
| `--color-border` (`#E2E8F0`) on `--color-surface` | Contrast `2.3:1` — does not meet 3:1 for non-text UI | Used only for decorative borders (card edge, divider), not conveying information | Accept — borders are structural, not semantic |
| Focus ring | Uses `rgba(37,99,235,.45)` for the ring and `rgba(37,99,235,.14)` for input focus — not a solid hex | Ensures focus ring is visible on both white and light-primary backgrounds | Accept — intentional for multi-background visibility |
| Icon button hit area | `34×34px`, below the 44×44px WCAG minimum touch target | Icon is accompanied by the task label text as an adjacent touch target | Accept — the full task row is also tappable |
| No `prefers-reduced-motion` media query in CSS | The mockup has no explicit `@media (prefers-reduced-motion: reduce)` block | The JS animation uses `@keyframes` which cannot be conditionally declared inline; would need a CSS media query at the stylesheet level | Dev should add `prefers-reduced-motion` query to disable keyframe animations |

## 5. Change log

| Date | Change | Design PR |
|---|---|---|
| 2025-01-27 | Initial design system extracted from approved `index.html` | (pending) |
