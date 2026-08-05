# AGENTS.md
Guidelines for Claude Code before modifying this Day13 project. Read this alongside CLAUDE.md (Korean version).

---

## Golden Rule: Confirm Before Acting

**STOP and use AskUserQuestion if any part of a request is ambiguous.** Do not assume, guess, or improvise. Confirmation takes seconds; fixing wrong changes takes minutes.

---

## Policy 1: Design Changes — Confirm Target, Scope, and Intent

**When users request UI/design changes:**
1. **Identify target**: Which file(s)? Which element? (e.g., "chart labels in list.html", not "the whole page")
2. **Clarify scope**: What property changes? (font, color, size, spacing, layout — be specific). What stays untouched?
3. **Confirm no side effects**: Will this break mobile layout? Affect other components?

**Example flow**: User: "Make text bigger" → Ask: "Product names in the chart? Just font size? Leave spacing unchanged?" → Wait for answer → Execute exactly that, nothing more.

**Violation to avoid**: Adding gradients, darkening colors, or changing unrelated elements. Stick to the request.

---

## Policy 2: Reference Materials — Always Ask "Where and Why?"

**When users show samples (screenshots, icons, color palettes, design references):**
1. **Ask explicitly**: "Where should this appear?" and "What's the purpose?" — do not assume placement
2. **Wait for confirmation**: Use only what the user explicitly approves
3. **No improvisation**: Do not extract parts randomly or repurpose elsewhere

**Example flow**: User shows Sayvoca trophy icon → Ask: "Should this mark the best-selling product in list.html? Or is it decorative elsewhere?" → Get explicit answer → Use only as confirmed.

**Violation to avoid**: Placing decorative elements randomly without stated purpose (e.g., trophy on detail.html with no meaning).

---

## Policy 3: Mobile-First is Non-Negotiable

**Every UI change must work on mobile (≤480px width):**
1. Components resize properly without horizontal scrolling
2. Touch targets stay ≥44px (buttons, links, form inputs)
3. Text remains readable; no truncation unless intentional

**Test before shipping**: Use Chrome DevTools device toolbar. If mobile breaks, fix it — do not merge.

**Never compromise**: Desktop-only changes that break mobile are bugs, not features.

---

## Policy 4: Clarity Checklist (Use This Before Every Change)

Before executing ANY UI/design request:

- [ ] **File**: Which file(s)? (index.html / list.html / detail.html / other)
- [ ] **Location**: Exact screen region? (chart, header, button row, form, etc.)
- [ ] **Change**: What property? (font size, color hex, spacing px, layout grid, etc.)
- [ ] **Scope**: Only this element? Or cascading effects?
- [ ] **Purpose**: Why? (readability, data clarity, mobile fit, user hierarchy)
- [ ] **Mobile impact**: Does this break ≤480px layout?

**If ANY are unclear or missing: Ask first via AskUserQuestion.**

---

## Policy 5: Request Clarity Levels

**Clear ✓ (proceed):**
- "Expand product names in list.html chart so 'カフェラテ' displays fully without truncation"
- "Center trophy icon in detail.html header, 2em size, marks best-selling product"
- "Make submit button tappable on mobile: min 48px height, thumb-friendly"

**Unclear ✗ (ask first):**
- "Make text bigger" ← Which text? Where? Just font? With spacing?
- "Add a trophy" ← Where? For what purpose? Decorative or data-linked?
- "Improve design" ← Which specific improvement? What metric?
- "Change colors" ← Which elements? To what color? Why?

**Default**: When unsure, ask. It saves time.

---

## Policy 6: Never Assume User Intent From Samples

**This is critical.** Showing you a design does NOT mean "use this everywhere."

If user shows Sayvoca stats cards → **Do not** automatically add similar cards to detail.html without asking where and why.
If user shows trophy icon → **Do not** place it randomly. Ask: "Where should this go? What does it represent?"

**Process**: See sample → Ask clarification → Get explicit answer → Apply only as confirmed.

---

## Policy 7: Plan Mode Requirement

**Use Plan Mode (with AskUserQuestion in Phase 1) when:**
- Request has multiple valid interpretations
- UI change spans multiple files
- Sample materials need intent clarification
- Mobile layout impact is uncertain
- Change could affect user experience unexpectedly

**Skip Plan Mode only for:**
- Obvious typo fixes (single file, clear intent)
- One-line logic changes (well-documented, narrow scope)
- Simple renames with full context provided

---

## Policy 8: Korean & English in This Project

**CLAUDE.md is in Korean** (user-facing, instructional). **AGENTS.md is in English** (for agents to read quickly).

**In code:**
- Variable names, function logic: **English**
- UI text, labels, messages: **Korean** (for users)
- Comments: Follow the file's language

---

## Pre-Execution Checklist for Agents

Before ANY change:

1. ✓ Is this request clear? (Use checklist from Policy 4)
2. ✓ Did I confirm the target, scope, and intent?
3. ✓ Is mobile layout affected? (Test if yes)
4. ✓ Does this align with CLAUDE.md rules?
5. ✓ Am I doing EXACTLY what was asked, nothing more?

If you answer "no" to ANY: Stop and ask via AskUserQuestion. Do not guess.

---

## Summary: Speed Comes From Clarity

Fast execution = clear communication first, then precise action. Skipping clarification causes rework. A 30-second confirmation saves 5 minutes of fixes.

**Remember**: The user can see the result. If it's wrong, it's wrong — no partial credit. Confirm first.
