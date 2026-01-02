# Export Screens

You are helping the user export screen audits and implementation specifications for developer handoff or AI-assisted implementation. This packages all design decisions into actionable, code-ready formats.

## Step 1: Check Prerequisites

First, verify that screens and audits exist:

List available screens by reading `/product/screens/` directory.

Ask the user: "Which screens would you like to export?"

Options:
- Specific screen(s) by name
- All screens
- Screens from a specific section

Once they specify, verify for each screen:
1. Screen file exists at `/product/screens/[screen-name].md`
2. Audit exists at `/product/screens/[screen-name]/audit.md`

If any screen doesn't have an audit:

"**[Screen Name]** hasn't been audited yet. Please run `/audit-screen [screen-name]` first to generate implementation specs."

You can continue with screens that have audits, but inform the user which screens were skipped.

## Step 2: Read Design System Context

Read all available design system files:
- `/product/design-system/colors.json`
- `/product/design-system/typography.json`
- `/product/design-system/spacing.json` (if exists)
- `/product/target-audience.md` (if exists)
- `/product/product-overview.md`

This context will be included in the export for implementation reference.

## Step 3: Explain Export Process

"I'll create implementation-ready export packages for:

[List screens to export]

Each export will include:
1. **Implementation specs** — HTML structure, CSS with exact values, component breakdown
2. **Design audit** — Full analysis with recommendations
3. **Design tokens reference** — Your color palette, typography, spacing to use
4. **Accessibility checklist** — WCAG requirements with implementation details
5. **Code examples** — Ready-to-use Tailwind classes and patterns

**Export format:** Developer-friendly markdown with code blocks

Ready to generate the exports?"

Wait for confirmation.

## Step 4: Generate Implementation Specs

For each screen, create comprehensive implementation documentation.

### 4.1 Read Screen Context

Read:
- Screen file (context, purpose, audience, concerns)
- Audit file (all recommendations, ratings, findings)
- Iteration files (if exist) to understand current state
- Consistency check (if exists) for token validation

### 4.2 Structure the Implementation Spec

Create a detailed implementation guide that developers (human or AI) can follow.

## Step 5: Create Export Package

For each screen, create an export directory at `/product/export/screens/[screen-name]/` with these files:

### File 1: `IMPLEMENTATION.md`

This is the master implementation guide.

Format:

```markdown
# Implementation Guide: [Screen Name]

**Screen Type:** [Type]
**Purpose:** [Purpose from screen file]
**Target Audience:** [Audience]
**Priority:** [High/Medium/Low based on product roadmap]

---

## Overview

[2-3 sentence summary of what this screen does and why it matters]

**Implementation Complexity:** [Simple/Moderate/Complex]
**Estimated Effort:** [X hours/days based on scope]

**Key Requirements:**
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

---

## Design Tokens Reference

Use these design tokens consistently throughout implementation:

### Colors

\`\`\`css
/* Primary (main actions, links) */
--color-primary-50: /* Tailwind [primary]-50 */
--color-primary-600: /* Tailwind [primary]-600 */
--color-primary-700: /* Tailwind [primary]-700 */

/* Secondary (highlights, tags) */
--color-secondary-100: /* Tailwind [secondary]-100 */
--color-secondary-600: /* Tailwind [secondary]-600 */

/* Neutral (text, backgrounds, borders) */
--color-neutral-50: /* Tailwind [neutral]-50 */
--color-neutral-200: /* Tailwind [neutral]-200 */
--color-neutral-700: /* Tailwind [neutral]-700 */
--color-neutral-900: /* Tailwind [neutral]-900 */
\`\`\`

**Tailwind Classes:**
- Primary button: \`bg-[primary]-600 hover:bg-[primary]-700 text-white\`
- Secondary button: \`bg-[secondary]-100 hover:bg-[secondary]-200 text-[secondary]-700\`
- Text: \`text-[neutral]-900\` (headings), \`text-[neutral]-700\` (body)
- Borders: \`border-[neutral]-200\`

### Typography

\`\`\`css
/* Fonts */
--font-heading: '[Heading Font]', sans-serif;
--font-body: '[Body Font]', sans-serif;
--font-mono: '[Mono Font]', monospace;
\`\`\`

**Type Scale:**
- Hero: \`text-4xl font-bold\` (36px)
- H1: \`text-3xl font-bold\` (30px)
- H2: \`text-2xl font-semibold\` (24px)
- H3: \`text-xl font-semibold\` (20px)
- Body: \`text-base\` (16px)
- Small: \`text-sm\` (14px)

### Spacing

**Scale:** 4px, 8px, 16px, 24px, 32px, 48px, 64px

**Tailwind Classes:**
- \`gap-2\` (8px) - within components
- \`gap-4\` (16px) - related items
- \`gap-6\` (24px) - component separation
- \`gap-8\` (32px) - section boundaries
- \`gap-12\` (48px) - major zones

**Card Padding:** \`p-6\` (24px)
**Container Max Width:** \`max-w-6xl\` (1152px)

---

## Layout Structure

[Based on audit findings, provide recommended layout structure]

\`\`\`html
<div class="max-w-6xl mx-auto px-6 py-12">
  <!-- Page container -->

  <section class="space-y-4">
    <!-- Hero/Primary section -->
    <h1 class="text-4xl font-bold text-[neutral]-900">[Title]</h1>
    <p class="text-lg text-[neutral]-700">[Description]</p>
    <button class="bg-[primary]-600 hover:bg-[primary]-700 text-white px-8 py-4 rounded-lg font-semibold">
      [Primary CTA]
    </button>
  </section>

  <section class="space-y-6 mt-12">
    <!-- Content section -->
    <h2 class="text-2xl font-semibold text-[neutral]-900">[Section Title]</h2>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <!-- Cards or content blocks -->
      <div class="bg-white border border-[neutral]-200 rounded-lg p-6">
        [Card content]
      </div>
    </div>
  </section>
</div>
\`\`\`

**Responsive Breakpoints:**
- Mobile: < 640px (sm) - Single column, larger touch targets
- Tablet: 640px - 1024px (md) - 2 columns
- Desktop: > 1024px (lg) - 3 columns, full layout

---

## Component Breakdown

[List all components needed for this screen]

### 1. [Component Name] (e.g., Primary CTA Button)

**Purpose:** [What it does]

**HTML Structure:**
\`\`\`html
<button
  class="bg-[primary]-600 hover:bg-[primary]-700 active:bg-[primary]-800
         text-white font-semibold px-8 py-4 rounded-lg
         transition-colors duration-200
         focus:ring-2 focus:ring-[primary]-500 focus:ring-offset-2
         disabled:opacity-50 disabled:cursor-not-allowed"
  aria-label="[Descriptive label]"
>
  [Button Text]
</button>
\`\`\`

**States:**
- Default: \`bg-[primary]-600\`
- Hover: \`hover:bg-[primary]-700\`
- Active: \`active:bg-[primary]-800\`
- Focus: \`focus:ring-2 focus:ring-[primary]-500\`
- Disabled: \`disabled:opacity-50\`

**Accessibility:**
- Minimum size: 44x44px (met with \`py-4\`)
- Focus visible: Yes (ring)
- Keyboard accessible: Yes (native button)
- aria-label if icon-only

---

### 2. [Component Name] (e.g., Card)

[Same detailed structure as above]

---

## Implementation Recommendations

[Pull from audit file - translate recommendations into specific implementation tasks]

### High Priority (Implement First)

1. **[Recommendation from audit]**

   **What to do:**
   - [Specific implementation step]
   - [Code to write]
   - [Where in layout]

   **Code Example:**
   \`\`\`html
   [Exact HTML/CSS to implement]
   \`\`\`

   **Why it matters:** [Rationale from audit]

2. **[Second high priority recommendation]**
   [Same structure]

### Medium Priority

[Same structure for medium priority items]

### Nice-to-Have

[Same structure for low priority items]

---

## Accessibility Checklist

Ensure WCAG 2.1 AA compliance:

- [ ] **Color Contrast**
  - Text on background: 4.5:1 minimum
  - UI elements: 3:1 minimum
  - Verify: \`text-[neutral]-900\` on white = 21:1 ✓

- [ ] **Keyboard Navigation**
  - All interactive elements focusable with Tab
  - Focus order follows visual order
  - Focus states visible (ring-2)

- [ ] **Screen Reader Support**
  - Semantic HTML (main, nav, section, article)
  - Heading hierarchy (h1 → h2 → h3, no skips)
  - alt text for images
  - aria-label for icon buttons

- [ ] **Touch Targets**
  - Minimum 44x44px for all buttons/links
  - Adequate spacing between targets (8px+)

- [ ] **Motion & Animation**
  - Respect prefers-reduced-motion
  - Keep transitions under 300ms
  - No auto-playing videos/animations

- [ ] **Form Accessibility** (if applicable)
  - Labels associated with inputs
  - Error messages linked with aria-describedby
  - Required fields marked

---

## Testing Checklist

Before considering this screen complete:

### Visual Testing

- [ ] Matches design specifications
- [ ] Responsive at all breakpoints
- [ ] Looks good in both light and dark mode
- [ ] All images and icons load correctly

### Functional Testing

- [ ] All buttons and links work
- [ ] Forms validate correctly
- [ ] Loading states display properly
- [ ] Error states handle gracefully

### Accessibility Testing

- [ ] Navigate entire screen with keyboard only
- [ ] Test with screen reader (VoiceOver, NVDA, JAWS)
- [ ] Run axe DevTools or Lighthouse accessibility audit
- [ ] Verify color contrast ratios

### Browser Testing

- [ ] Chrome/Edge
- [ ] Firefox
- [ ] Safari
- [ ] Mobile browsers (iOS Safari, Chrome Mobile)

---

## Implementation Notes

**From Design Audit:**

[Pull specific notes and insights from the audit that are relevant to implementation]

Example:
- "The dashboard's #1 job is to answer 'What should I do next?' Make the next action unmissable through size, color, and position."
- "Use spacing to create boundaries without borders. 48px between major zones, 24px between cards."
- "Progress indicators should use [secondary] color to create positive association."

**User's Original Concerns:**

[List concerns from screen file]

**How This Implementation Addresses Them:**

[Show how the implementation specs solve each concern]

---

## Quick Start (30 Second Summary)

**If you're using Claude Code or another AI assistant, share this:**

"Implement [Screen Name] for [Product Name]. Use [primary]/[secondary]/[neutral] color palette with [heading/body fonts]. Key: Make [primary user goal] obvious. Focus on [top 3 priorities from audit]. Ensure accessibility (WCAG AA). See full implementation guide for details."

---

## Resources

- [Full Audit Report](/product/screens/[screen-name]/audit.md)
- [Design System Tokens](/product/design-system/)
- [Product Overview](/product/product-overview.md)
- [Target Audience](/product/target-audience.md) (if exists)

---

## Questions?

If anything is unclear or you need clarification:
1. Review the full audit report for context
2. Check design system tokens for reference values
3. Run `/audit-screen [screen-name]` again if specifications changed

**This implementation guide is AI-friendly:** You can share it directly with Claude Code, Cursor, or GitHub Copilot for implementation assistance.
```

### File 2: `QUICK-REFERENCE.md`

Create a condensed version for quick lookups:

```markdown
# Quick Reference: [Screen Name]

## Design Tokens

**Colors:** [primary], [secondary], [neutral]
**Typography:** [heading], [body], [mono fonts]
**Spacing Scale:** 4, 8, 16, 24, 32, 48, 64px

## Layout

\`\`\`
max-w-6xl mx-auto px-6 py-12
Hero: space-y-4
Content: space-y-6, mt-12
Cards: grid gap-6, md:grid-cols-2, lg:grid-cols-3
\`\`\`

## Key Components

1. Primary Button: \`bg-[primary]-600 h-12 px-8 font-semibold\`
2. Card: \`bg-white border border-[neutral]-200 rounded-lg p-6\`
3. Heading: \`text-3xl font-bold text-[neutral]-900\`

## Top 3 Priorities

1. [Priority 1 from audit]
2. [Priority 2 from audit]
3. [Priority 3 from audit]

## Accessibility Must-Haves

- Focus rings on all interactive elements
- Semantic HTML structure
- 44x44px minimum touch targets
- WCAG AA contrast (4.5:1 text, 3:1 UI)
```

### File 3: Copy `audit.md`

Copy the full audit report to the export directory for reference:

```bash
cp /product/screens/[screen-name]/audit.md /product/export/screens/[screen-name]/audit.md
```

### File 4: `README.md`

Create an export package README:

```markdown
# Export Package: [Screen Name]

**Generated:** [Date]
**Screen Type:** [Type]
**Status:** Ready for Implementation

## What's Included

- \`IMPLEMENTATION.md\` - Complete implementation guide with code examples
- \`QUICK-REFERENCE.md\` - Condensed reference for quick lookups
- \`audit.md\` - Full design audit with analysis and recommendations

## How to Use This Export

### For Human Developers

1. Read \`IMPLEMENTATION.md\` for complete specifications
2. Reference \`QUICK-REFERENCE.md\` while coding
3. Review \`audit.md\` for design rationale

### For AI Assistants (Claude Code, Cursor, GitHub Copilot)

Share \`IMPLEMENTATION.md\` with your AI assistant and say:

"Implement this screen following the specifications in IMPLEMENTATION.md. Use the design tokens defined, follow the layout structure, and ensure all accessibility requirements are met."

For more optimized AI prompts, run \`/format-for-ai [screen-name]\`.

## Implementation Checklist

- [ ] Set up design tokens (colors, typography)
- [ ] Implement layout structure
- [ ] Build all components
- [ ] Apply responsive breakpoints
- [ ] Ensure accessibility compliance
- [ ] Test across browsers and devices
- [ ] Validate against audit recommendations

## Next Steps

After implementation:
1. Run \`/track-iteration [screen-name]\` in Design OS to measure improvements
2. Run \`/check-consistency [screen-name]\` to validate token usage
3. Continue iterating based on feedback
```

## Step 6: Create Export Summary

After generating all exports, create a summary file at `/product/export/EXPORT-SUMMARY.md`:

```markdown
# Export Summary

**Export Date:** [Date]
**Screens Exported:** [Count]

## Exported Screens

1. **[Screen Name]** - [Type]
   - Location: \`/product/export/screens/[screen-name]/\`
   - Files: IMPLEMENTATION.md, QUICK-REFERENCE.md, audit.md, README.md
   - Status: Ready for implementation

2. **[Screen Name 2]** - [Type]
   [Same format]

## Design System Reference

All exports use these design tokens:
- **Colors:** [primary], [secondary], [neutral]
- **Typography:** [heading], [body], [mono]
- **Spacing:** Standard scale (4, 8, 16, 24, 32, 48, 64px)

## How to Use Exports

Each screen export is self-contained and can be implemented independently or as part of a larger implementation plan.

**For sequential implementation:**
1. Start with [most critical screen]
2. Then [second priority]
3. Finally [remaining screens]

**For parallel implementation:**
All screens can be built simultaneously by different team members or AI sessions.

## Next Steps

1. **Implement screens** using the specifications provided
2. **Track progress** with \`/track-iteration\` for each screen
3. **Validate consistency** with \`/check-consistency\`
4. **Export updated versions** as screens improve

**For AI-optimized exports:** Run \`/format-for-ai\` on any exported screen.
```

## Step 7: Confirm Completion

Let the user know:

"I've created implementation-ready export packages for:

[List screens exported with paths]

**Export location:** \`/product/export/screens/\`

**What's included for each screen:**
- ✅ IMPLEMENTATION.md - Complete guide with code examples
- ✅ QUICK-REFERENCE.md - Quick lookup reference
- ✅ audit.md - Full design audit
- ✅ README.md - Usage instructions

**Export summary:** \`/product/export/EXPORT-SUMMARY.md\`

**Ready for:**
- Human developers (read IMPLEMENTATION.md)
- AI assistants (share IMPLEMENTATION.md directly)
- Team handoff (complete package with context)

**Next steps:**

1. **For immediate implementation:**
   - Share IMPLEMENTATION.md with your developer or AI assistant
   - Follow the component breakdown and code examples
   - Use QUICK-REFERENCE.md while coding

2. **For AI-optimized implementation:**
   - Run \`/format-for-ai [screen-name]\` to create optimized prompts
   - Share with Claude Code, Cursor, or GitHub Copilot

3. **After implementation:**
   - Run \`/track-iteration [screen-name]\` to measure improvements
   - Run \`/check-consistency [screen-name]\` to validate

**These exports are production-ready and contain everything needed to implement the screens with high design quality.**

Would you like me to create AI-optimized formats for any of these screens?"

## Important Notes

- **Be comprehensive:** Exports should be self-contained with all necessary context
- **Include rationale:** Don't just say what to do, explain why
- **Provide exact code:** Tailwind classes, HTML structure, not pseudo-code
- **Reference tokens:** Always tie back to design system tokens
- **Prioritize:** Not everything is equally important; highlight top priorities
- **Make it scannable:** Use headings, lists, code blocks for easy navigation
- **AI-friendly:** Structure should work well for both humans and AI assistants
- **Include testing:** Checklists ensure nothing is missed
- **Link resources:** Connect exports back to original audits and design system
- **Encourage iteration:** Implementation is step one; tracking progress is step two
