# Format for AI

You are helping the user optimize Design OS exports for AI coding assistants (Claude Code, Cursor, GitHub Copilot, etc.). This restructures exports into AI-friendly formats with clear prompts, context, and acceptance criteria.

## Step 1: Check Prerequisites

First, determine what to optimize:

Ask the user: "Which export would you like to optimize for AI assistants?"

Options:
1. **Specific screen export** - Optimize a single screen implementation package
2. **Design system** - Optimize design tokens for AI-assisted styling
3. **Multiple screens** - Batch optimize several screens
4. **Complete project** - Optimize everything for full AI-assisted implementation

Once they specify, verify the export exists:

**For screen:**
Check that `/product/export/screens/[screen-name]/` exists with IMPLEMENTATION.md

**For design system:**
Check that design tokens exist at `/product/design-system/`

If exports don't exist:
- For screens: "Please run `/export-screens [screen-name]` first to create the export package."
- For design system: "Please run `/design-tokens` first to define your design system."

Stop here if prerequisites are missing.

## Step 2: Understand AI Assistant Target

Ask the user (optional): "Which AI assistant will you be using?"

Options:
- Claude Code (default, most comprehensive)
- Cursor
- GitHub Copilot
- Generic/Unsure

This helps optimize the format, but the output should work well with all AI assistants.

## Step 3: Read Original Export

Read the relevant export files:
- IMPLEMENTATION.md (for screens)
- Design system tokens (for design system)
- Audit reports (for context)
- Product overview (for understanding)

Extract:
- Key requirements
- Implementation specs
- Design tokens
- Priority recommendations
- Accessibility requirements

## Step 4: Create AI-Optimized Format

Generate an AI-friendly implementation prompt that packages all information in a structured, clear format optimized for AI comprehension and code generation.

## Step 5: Generate AI Prompt Package

Create files at `/product/export/ai-assistant/[package-name]/`:

### File 1: `AI-IMPLEMENTATION-PROMPT.md`

This is the master prompt to share with AI assistants.

Format:

```markdown
# AI Implementation Prompt: [Screen/Feature Name]

**Product:** [Product Name]
**Component:** [Screen Name]
**Complexity:** [Simple/Moderate/Complex]
**Estimated Time:** [X hours with AI assistance]

---

## Context

You are helping implement **[Screen Name]** for [Product Name]. This is a [screen type] that [purpose in 1 sentence].

**Target Users:** [User type from target audience]
**Primary Goal:** [What the screen should accomplish]

---

## Design System (Apply Consistently)

### Colors (Tailwind Palette)

**Primary Color:** `[primary]`
- Use for: Main CTAs, primary actions, links
- Classes: `bg-[primary]-600 hover:bg-[primary]-700 text-[primary]-600`

**Secondary Color:** `[secondary]`
- Use for: Tags, highlights, progress indicators, success states
- Classes: `bg-[secondary]-100 text-[secondary]-700 border-[secondary]-200`

**Neutral Color:** `[neutral]`
- Use for: Text, backgrounds, borders
- Classes:
  - Text: `text-[neutral]-900` (headings), `text-[neutral]-700` (body), `text-[neutral]-500` (secondary)
  - Backgrounds: `bg-[neutral]-50` (page), `bg-white` (cards)
  - Borders: `border-[neutral]-200`

### Typography

**Fonts:**
- Heading: [font name]
- Body: [font name]
- Mono: [font name] (for code)

**Type Scale (use these classes):**
```
Hero:    text-4xl font-bold      (36px)
H1:      text-3xl font-bold      (30px)
H2:      text-2xl font-semibold  (24px)
H3:      text-xl font-semibold   (20px)
Body:    text-base               (16px)
Small:   text-sm                 (14px)
```

### Spacing (8px scale)

**Use these gap values:**
```
gap-2  (8px)  - within components
gap-4  (16px) - related items
gap-6  (24px) - component separation
gap-8  (32px) - section boundaries
gap-12 (48px) - major zones
```

**Standard patterns:**
- Cards: `p-6 rounded-lg border border-[neutral]-200`
- Container: `max-w-6xl mx-auto px-6 py-12`
- Sections: `space-y-12` (between major zones)

---

## Implementation Requirements

### Must Have (Critical)

1. **[Requirement 1 from audit]**
   - What: [Specific feature/element]
   - Why: [Reason from audit]
   - How: [Implementation guidance]
   - Code: `[Tailwind classes]`

2. **[Requirement 2]**
   [Same structure]

3. **[Requirement 3]**
   [Same structure]

### Should Have (Important)

[Same format for important features]

### Nice to Have (Enhancement)

[Same format for enhancements]

---

## Layout Structure

Implement this layout hierarchy:

\`\`\`jsx
// React/JSX example (adapt to your framework)
export function [ComponentName]() {
  return (
    <div className="max-w-6xl mx-auto px-6 py-12">
      {/* Hero Section */}
      <section className="space-y-4 mb-12">
        <h1 className="text-4xl font-bold text-[neutral]-900">
          [Title]
        </h1>
        <p className="text-lg text-[neutral]-700">
          [Description]
        </p>
        <button className="bg-[primary]-600 hover:bg-[primary]-700 text-white px-8 py-4 rounded-lg font-semibold transition-colors focus:ring-2 focus:ring-[primary]-500 focus:ring-offset-2">
          [Primary CTA]
        </button>
      </section>

      {/* Content Section */}
      <section className="space-y-6">
        <h2 className="text-2xl font-semibold text-[neutral]-900">
          [Section Title]
        </h2>

        {/* Grid of Cards */}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {/* Card Component */}
          <div className="bg-white border border-[neutral]-200 rounded-lg p-6 hover:border-[neutral]-300 transition-colors">
            <h3 className="text-lg font-medium text-[neutral]-900 mb-2">
              [Card Title]
            </h3>
            <p className="text-sm text-[neutral]-600">
              [Card Description]
            </p>
          </div>
        </div>
      </section>
    </div>
  )
}
\`\`\`

**Responsive Breakpoints:**
- Mobile (<640px): Single column, stack everything
- Tablet (640-1024px): 2 columns where applicable
- Desktop (>1024px): 3 columns, full layout

---

## Component Specifications

### 1. Primary Button

**Purpose:** Main call-to-action
**Usage:** 1 per screen maximum, for primary user action

\`\`\`jsx
<button
  className="
    bg-[primary]-600 hover:bg-[primary]-700 active:bg-[primary]-800
    text-white font-semibold
    px-8 py-4 h-12
    rounded-lg
    transition-colors duration-200
    focus:outline-none focus:ring-2 focus:ring-[primary]-500 focus:ring-offset-2
    disabled:opacity-50 disabled:cursor-not-allowed
  "
  aria-label="[Descriptive label]"
>
  [Button Text]
</button>
\`\`\`

### 2. Secondary Button

**Purpose:** Secondary actions
**Usage:** Supporting actions, less prominent than primary

\`\`\`jsx
<button
  className="
    bg-[secondary]-100 hover:bg-[secondary]-200 active:bg-[secondary]-300
    text-[secondary]-700 font-medium
    px-6 py-3 h-10
    rounded-lg border border-[secondary]-300
    transition-colors duration-200
    focus:outline-none focus:ring-2 focus:ring-[secondary]-500 focus:ring-offset-2
  "
>
  [Button Text]
</button>
\`\`\`

### 3. Card

**Purpose:** Content container
**Usage:** Group related information

\`\`\`jsx
<div className="bg-white border border-[neutral]-200 rounded-lg p-6 hover:border-[neutral]-300 transition-colors">
  <h3 className="text-lg font-medium text-[neutral]-900 mb-3">
    [Card Title]
  </h3>
  <p className="text-sm text-[neutral]-600 mb-4">
    [Card Description]
  </p>
  {/* Card content */}
</div>
\`\`\`

[Add more component specs as needed]

---

## Accessibility Requirements (Must Implement)

### Keyboard Navigation
- [ ] All interactive elements focusable with Tab
- [ ] Focus order follows visual order (top to bottom, left to right)
- [ ] Focus visible: `focus:ring-2 focus:ring-[primary]-500 focus:ring-offset-2`
- [ ] Escape key closes modals/dropdowns (if applicable)

### Screen Reader Support
- [ ] Semantic HTML: Use `<main>`, `<nav>`, `<section>`, `<article>` appropriately
- [ ] Heading hierarchy: h1 → h2 → h3 (no skips)
- [ ] `aria-label` on icon-only buttons
- [ ] `alt` text on all images (descriptive, not redundant)
- [ ] Form labels associated with inputs

### Color & Contrast
- [ ] Text on background: 4.5:1 minimum (WCAG AA)
  - `text-[neutral]-900` on white = 21:1 ✓
  - `text-[neutral]-700` on white = 10.5:1 ✓
- [ ] UI elements: 3:1 minimum
- [ ] Don't convey info by color alone (use icons + text)

### Touch Targets
- [ ] Buttons minimum 44x44px
  - Primary button with `py-4` = 48px height ✓
- [ ] Adequate spacing between targets (8px+)

### Motion
- [ ] Respect `prefers-reduced-motion`
- [ ] Transitions under 300ms
- [ ] No auto-playing content

---

## Implementation Steps

Follow these steps in order:

### Step 1: Set Up Structure (15 min)
1. Create component file: `[ComponentName].tsx` (or .jsx, .vue, etc.)
2. Import necessary dependencies
3. Set up basic component structure

### Step 2: Implement Layout (30 min)
1. Add container with max-width and padding
2. Create hero section with heading, description, CTA
3. Add main content section with proper spacing
4. Implement grid/flex layout for cards or content blocks

### Step 3: Build Components (45 min)
1. Primary button with all states (default, hover, active, focus, disabled)
2. Secondary buttons and links
3. Cards with proper styling and hover states
4. Any other custom components needed

### Step 4: Apply Design Tokens (20 min)
1. Replace all colors with design system colors ([primary], [secondary], [neutral])
2. Apply typography classes (text-4xl, text-2xl, etc.)
3. Use spacing scale (gap-4, gap-6, gap-8, gap-12)
4. Ensure consistent padding (p-6 for cards)

### Step 5: Make Responsive (20 min)
1. Test at mobile (< 640px), tablet (640-1024px), desktop (> 1024px)
2. Apply responsive classes (md:, lg:)
3. Ensure touch targets are 44x44px minimum on mobile
4. Stack columns appropriately on small screens

### Step 6: Ensure Accessibility (30 min)
1. Add semantic HTML elements
2. Implement proper heading hierarchy
3. Add focus states to all interactive elements
4. Test keyboard navigation
5. Add aria-labels where needed
6. Verify color contrast

### Step 7: Test & Refine (30 min)
1. Visual check against specifications
2. Test all interactive elements
3. Validate responsive behavior
4. Run accessibility audit (axe DevTools or Lighthouse)
5. Fix any issues found

**Total estimated time: 3 hours**

---

## Acceptance Criteria

Implementation is complete when:

✅ **Visual**
- [ ] Matches layout structure specified
- [ ] Uses correct design tokens (colors, typography, spacing)
- [ ] Responsive at all breakpoints
- [ ] Hover states work on all interactive elements

✅ **Functional**
- [ ] All buttons and links work
- [ ] Primary CTA is clearly prominent
- [ ] Loading/empty states handled (if applicable)

✅ **Accessibility**
- [ ] Can navigate entire interface with keyboard only
- [ ] Focus states visible and clear
- [ ] Contrast ratios meet WCAG AA (4.5:1 text, 3:1 UI)
- [ ] Screen reader announces content correctly
- [ ] Lighthouse accessibility score > 90

✅ **Code Quality**
- [ ] Uses design system tokens consistently
- [ ] No hardcoded colors, font sizes, or spacing values
- [ ] Semantic HTML structure
- [ ] Clean, readable code

---

## Testing Commands

After implementation, validate with:

\`\`\`bash
# Accessibility audit
npm run lighthouse -- --only-categories=accessibility

# Visual regression (if set up)
npm run test:visual

# Keyboard navigation
# Manual: Tab through all interactive elements, ensure focus visible
\`\`\`

---

## Common Pitfalls (Avoid These)

❌ **Don't:**
- Use colors outside the design system (`bg-blue-500` instead of `bg-[primary]-500`)
- Skip focus states (accessibility violation)
- Hardcode spacing values (`mt-[23px]` instead of `mt-6`)
- Make buttons too small (<44x44px)
- Skip semantic HTML (`<div>` everywhere instead of `<main>`, `<section>`)

✅ **Do:**
- Use design tokens consistently
- Implement all focus states
- Follow spacing scale
- Ensure touch targets are 44x44px minimum
- Use semantic HTML

---

## Questions to Ask (If Anything is Unclear)

Before starting, clarify if needed:
1. What framework are we using? (React, Vue, Svelte, vanilla HTML)
2. Are there existing components to reuse?
3. What's the data source? (static, API, props)
4. Any specific browser support requirements?
5. Should this be server-rendered or client-rendered?

---

## After Implementation

When done:
1. **Share with user** for visual review
2. **Run accessibility audit** and fix any issues
3. **Test responsive** behavior at all breakpoints
4. **In Design OS:** Run `/track-iteration [screen-name]` to measure improvements against audit

---

## Need Help?

If you encounter issues:
- **Design rationale:** Review the full audit at `/product/export/screens/[screen-name]/audit.md`
- **Design tokens:** Check `/product/design-system/` for exact color/typography values
- **Component examples:** See IMPLEMENTATION.md for more detailed code examples

**This prompt is optimized for AI assistants but also works for human developers.**

Good luck with implementation! 🚀
```

### File 2: `QUICK-START-PROMPT.md`

Create a condensed version for quick AI prompting:

```markdown
# Quick Start Prompt: [Screen Name]

**Copy and paste this into Claude Code, Cursor, or GitHub Copilot:**

---

Implement [Screen Name] for [Product Name].

**Design System:**
- Colors: [primary] (primary), [secondary] (secondary), [neutral] (neutral)
- Fonts: [heading/body fonts]
- Spacing: 8px scale (gap-2, gap-4, gap-6, gap-8, gap-12)

**Layout:**
```
max-w-6xl mx-auto px-6 py-12
Hero section: space-y-4, text-4xl heading, primary CTA button
Content: space-y-6, grid md:grid-cols-2 lg:grid-cols-3 gap-6
Cards: bg-white border border-[neutral]-200 rounded-lg p-6
```

**Key Requirements:**
1. [Top requirement from audit]
2. [Second requirement]
3. [Third requirement]

**Accessibility:**
- Focus rings: focus:ring-2 focus:ring-[primary]-500
- Semantic HTML
- 44x44px touch targets
- WCAG AA contrast

**Component:** [Framework] component with TypeScript. Responsive (mobile/tablet/desktop). Full implementation with all interactive states.

See AI-IMPLEMENTATION-PROMPT.md for complete specs.

---
```

### File 3: `VERIFICATION-CHECKLIST.md`

```markdown
# Verification Checklist: [Screen Name]

After AI implementation, verify these items:

## Visual Check

- [ ] Layout matches specifications
- [ ] Design tokens applied correctly:
  - [ ] Colors use [primary]/[secondary]/[neutral]
  - [ ] Typography uses correct fonts and scale
  - [ ] Spacing follows 8px scale
- [ ] Responsive at all breakpoints:
  - [ ] Mobile (< 640px): Single column, stacked
  - [ ] Tablet (640-1024px): 2 columns
  - [ ] Desktop (> 1024px): 3 columns
- [ ] All hover states work
- [ ] Focus states visible on all interactive elements

## Functional Check

- [ ] All buttons/links work
- [ ] Primary CTA is prominently displayed
- [ ] Forms validate (if applicable)
- [ ] Loading states display (if applicable)
- [ ] Error handling works (if applicable)

## Accessibility Check

- [ ] Keyboard navigation works (Tab through everything)
- [ ] Focus order follows visual order
- [ ] Focus visible on all elements
- [ ] Screen reader test passes (basic check)
- [ ] Color contrast meets WCAG AA:
  - [ ] Text: 4.5:1 minimum
  - [ ] UI elements: 3:1 minimum
- [ ] Touch targets 44x44px minimum
- [ ] Semantic HTML used (`<main>`, `<section>`, `<h1-h6>`)

## Code Quality Check

- [ ] No hardcoded colors (all use design tokens)
- [ ] No hardcoded spacing (all use Tailwind scale)
- [ ] No arbitrary values (`[23px]`)
- [ ] Semantic HTML throughout
- [ ] TypeScript types correct (if applicable)
- [ ] No console errors
- [ ] No accessibility violations (run axe DevTools)

## If Any Item Fails

1. Review AI-IMPLEMENTATION-PROMPT.md for correct specifications
2. Ask AI to fix the specific issue
3. Re-verify after fix
4. Repeat until all items pass

## After All Pass

✅ Implementation complete!

**Next:** Run `/track-iteration [screen-name]` in Design OS to measure improvements.
```

### File 4: `COMMON-AI-PATTERNS.md`

```markdown
# Common AI Implementation Patterns

Useful patterns when working with AI assistants on this implementation:

## Pattern 1: Iterative Refinement

Instead of asking for everything at once:

1. **First:** "Implement the basic layout structure for [Screen Name] using the design system specified."
2. **Then:** "Add the hero section with primary CTA button."
3. **Then:** "Implement the card grid with proper spacing."
4. **Finally:** "Add all accessibility features (focus states, semantic HTML)."

## Pattern 2: Component-First

Build reusable components first:

1. "Create a PrimaryButton component following the specifications."
2. "Create a Card component with the specified styling."
3. "Now use these components to build [Screen Name]."

## Pattern 3: Fix-As-You-Go

If AI makes mistakes:

"The button is using `bg-blue-600` but should use `bg-[primary]-600` per the design system. Please update."

## Pattern 4: Accessibility First

After basic implementation:

"Please add full accessibility: focus states, semantic HTML, ARIA labels where needed, and ensure WCAG AA contrast."

## Pattern 5: Responsive Check

After desktop implementation:

"Make this fully responsive: mobile (single column), tablet (2 columns), desktop (3 columns). Ensure touch targets are 44x44px on mobile."

## What Works Well

✅ Be specific: "Use `text-4xl font-bold`" not "make it big"
✅ Reference design system: "Use primary color from design system"
✅ Give examples: "Like this: `<button className='...'>`"
✅ Check incrementally: Verify each section before moving on

## What Doesn't Work Well

❌ Vague: "Make it look good"
❌ Contradictory: Asking for both minimal and detailed at once
❌ Too much at once: 20 requirements in one prompt
❌ Skipping verification: Assuming AI got everything right

## Best Practice

1. Share AI-IMPLEMENTATION-PROMPT.md in full
2. Ask AI to implement in stages
3. Verify each stage with VERIFICATION-CHECKLIST.md
4. Fix issues as they arise
5. Final accessibility pass at the end
```

## Step 6: Create AI Package Summary

Create a README at `/product/export/ai-assistant/[package-name]/README.md`:

```markdown
# AI Assistant Package: [Package Name]

**Optimized for:** Claude Code, Cursor, GitHub Copilot
**Generated:** [Date]
**Source:** [Screen/Design System/Project]

## What's Included

- **AI-IMPLEMENTATION-PROMPT.md** - Complete AI-friendly implementation guide (share this with AI)
- **QUICK-START-PROMPT.md** - Condensed prompt for fast starts
- **VERIFICATION-CHECKLIST.md** - Verify AI implementation quality
- **COMMON-AI-PATTERNS.md** - Best practices for AI-assisted implementation

## How to Use

### With Claude Code

1. Open Claude Code in your project
2. Share AI-IMPLEMENTATION-PROMPT.md
3. Say: "Implement this screen following the specifications provided"
4. Verify with VERIFICATION-CHECKLIST.md
5. Iterate as needed

### With Cursor / GitHub Copilot

1. Open QUICK-START-PROMPT.md
2. Copy the prompt
3. Paste into Cursor Chat or Copilot
4. Verify with VERIFICATION-CHECKLIST.md
5. Ask for fixes if needed

## Tips for Best Results

- **Be specific:** Reference exact file names and specifications
- **Iterate:** Build in stages, verify each stage
- **Use checklist:** Don't skip verification
- **Fix incrementally:** Address issues one at a time

## After Implementation

Run these Design OS commands to track progress:
- `/track-iteration [screen-name]` - Measure improvements
- `/check-consistency [screen-name]` - Validate token usage

**AI-optimized exports make implementation faster and higher quality.**
```

## Step 7: Confirm Completion

Let the user know:

"I've created an AI-optimized implementation package for **[Package Name]**!

**Location:** `/product/export/ai-assistant/[package-name]/`

**What's included:**
- ✅ AI-IMPLEMENTATION-PROMPT.md - Complete prompt for AI assistants (700+ lines)
- ✅ QUICK-START-PROMPT.md - Condensed version for quick starts
- ✅ VERIFICATION-CHECKLIST.md - Quality checklist for AI implementations
- ✅ COMMON-AI-PATTERNS.md - Best practices for AI-assisted development

**How to use:**

**For Claude Code:**
1. Open Claude Code in your project
2. Share `AI-IMPLEMENTATION-PROMPT.md`
3. Say: 'Implement this screen following all specifications'
4. Verify with `VERIFICATION-CHECKLIST.md`

**For Cursor/Copilot:**
1. Copy prompt from `QUICK-START-PROMPT.md`
2. Paste into AI chat
3. Verify implementation with checklist

**What makes this AI-optimized:**
- Clear context and objectives upfront
- Design tokens formatted for easy reference
- Step-by-step implementation guide
- Acceptance criteria for verification
- Common pitfalls highlighted
- Questions to ask if unclear

**Expected outcome:** AI assistant can implement the screen in 2-3 hours with high design quality, proper accessibility, and correct token usage.

**After AI implementation:**
1. Verify with VERIFICATION-CHECKLIST.md
2. Fix any issues found
3. Run `/track-iteration [screen-name]` to measure improvements

Would you like me to optimize any other screens or create a complete project AI package?"

## Important Notes

- **Structure for AI comprehension:** Use clear headings, lists, code blocks
- **Provide complete context:** AI needs to understand what, why, and how
- **Include acceptance criteria:** AI needs to know when it's done
- **Highlight pitfalls:** Prevent common AI mistakes
- **Keep it concise but complete:** Every line should add value
- **Format for copy-paste:** Make it easy to share with AI tools
- **Include verification:** Trust but verify AI output
- **Iterate-friendly:** Support incremental implementation
- **Framework-agnostic where possible:** Work with React, Vue, vanilla, etc.
- **Reference original exports:** Link back to full documentation
