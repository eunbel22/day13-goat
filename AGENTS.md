# AGENTS.md
Guidelines for Claude Code before modifying this Day13 coffee vending machine project (order registration + sales dashboard + detail page).

---

## Golden Rule: Confirm User Intent Before Acting

**If a request is ambiguous or has multiple interpretations, STOP and ask AskUserQuestion FIRST.** Do not assume or guess. Confirmation is faster than fixing wrong changes.

---

## Policy 1: Clarify Design Change Targets

**When users request design changes (e.g., "make text bigger", "change colors"), always confirm THREE things:**
1. **Which file and location?** (e.g., list.html chart labels, not entire page)
2. **What exactly changes?** (font size, text length, color — be specific)
3. **What stays untouched?** (don't add gradients/shadows unless requested)

**Example**: User says "increase text size" → Ask "Do you mean the product names in the chart? Just enlarge the font? Leave everything else unchanged?" → Wait for answer → Execute.

**Violation to avoid**: Changing graph colors to gradients, darkening shades, or adding effects not requested. Stick to exactly what was asked.

---

## Policy 2: Confirm Intent for Sample/Reference Elements

**When users show design samples (e.g., Sayvoca screenshots, icons, color palettes), ALWAYS ask BEFORE using them:**
1. **Where should this go?** (specific file, section, component)
2. **Why this element?** (aesthetic, functional, data-related)
3. **How much of it?** (just the icon? the whole component?)

**Example**: User shows trophy icon → Ask "Should the trophy appear in the sales dashboard to mark best-selling product? Or elsewhere?" → Wait for answer → Place it correctly with meaning.

**Violation to avoid**: Placing trophy randomly on detail.html without purpose. Using decorative elements just because they look good, not because they serve a function.

---

## Policy 3: Mobile-First UI Requirements

**This project must be mobile-responsive. When designing or modifying UI, always ensure:**
1. Components resize properly on screens ≤ 480px wide (use media queries)
2. Touch targets are ≥ 44px for buttons and interactive elements
3. Text is readable without horizontal scrolling (max-width constraints)

**Test**: Preview changes on mobile (Chrome DevTools: toggle device toolbar). If it breaks layout or text is cut off, fix it before shipping.

**Non-negotiable**: Every page (index.html, list.html, detail.html) must work smoothly on both desktop and mobile.

---

## Policy 4: Design Clarity Checklist

**Before executing ANY UI/design change, confirm these in order:**

- [ ] **File**: Which file(s) change? (index.html / list.html / detail.html)
- [ ] **Location**: Exact screen region (chart labels, header, buttons)
- [ ] **Change type**: What property? (font, color, size, spacing, layout)
- [ ] **Scope**: Only this element? Or does it affect others?
- [ ] **Purpose**: Why? (readability, data clarity, mobile fit, visual hierarchy)
- [ ] **Mobile impact**: Does this break mobile layout?

**If any are unclear: use AskUserQuestion before proceeding.**

---

## Policy 5: Request Clarity Levels

**Clear requests (proceed immediately):**
- "Expand chart labels in list.html so 'カフェラテ' (full name) displays without truncation"
- "Center the trophy icon in detail.html header with 2em size"
- "Make buttons tappable on mobile (min 48px height)"

**Unclear requests (ask first):**
- "Make text bigger" ← Which text? Where?
- "Add a trophy" ← Where? For what purpose?
- "Change colors" ← Which colors? To what?
- "Improve the design" ← Specific improvement needed

**Default behavior**: When in doubt, ask. It saves time.

---

## Policy 6: Sample/Reference Material Handling

**If users provide design samples (images, screenshots, color palettes, icons):**

1. Do NOT assume where or how to use them
2. Ask: "Where should this appear?" and "What's the purpose?"
3. Wait for explicit confirmation before applying
4. Use only the parts the user approves; don't improvise

**Example workflow**:
- User shows Sayvoca screenshot → Ask clarifying questions → Get explicit answer → Apply only what was confirmed

**Never**: Extract parts randomly or repurpose them elsewhere without asking.

---

## Policy 7: When to Enter Plan Mode

**Use Plan Mode → AskUserQuestion in Initial Understanding phase when:**
- Request is vague or has multiple valid interpretations
- UI change affects multiple files
- Sample/reference materials need intent clarification
- Design impact on mobile layout is uncertain

**Skip Plan Mode only for:**
- Typo fixes (single file, obvious intent)
- One-line logic changes (documented, clear scope)
- Simple renames with full context

---

## Policy 8: Korean Language in Code Comments

**Project is in Korean (CLAUDE.md, file content). When adding code:**
- Write code in English (variable names, function logic)
- Use Korean for UI text (customer-facing strings) only
- Keep this AGENTS.md and CLAUDE.md in their original languages for project maintainers

---

## Summary for Agents

Before any change:
1. **Confirm unclear requests** via AskUserQuestion
2. **Check mobile responsiveness** — if mobile layout breaks, fix it
3. **Understand sample usage** — ask where and why before applying
4. **Use the checklist** — file, location, change type, scope, purpose, mobile impact
5. **Wait for answers** — don't guess or improvise

**Speed comes from clarity, not from skipping confirmation steps.**
