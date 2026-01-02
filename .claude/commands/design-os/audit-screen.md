# Audit Screen

You are helping the user get comprehensive design analysis and actionable recommendations for a screen they've imported. This is the core value of Design OS - providing structured, educational design feedback.

## Step 1: Check Prerequisites

First, verify the screen exists:

Ask the user: "Which screen would you like to audit?"

If they don't provide a screen name, list available screens by reading `/product/screens/` directory.

Once they specify a screen name, read the screen file at `/product/screens/[screen-name].md`.

If it doesn't exist:

"I don't see a screen named **[screen-name]**. Please run `/add-screen` first to import the screen, or check the available screens in `/product/screens/`."

Stop here if the screen doesn't exist.

## Step 2: Read Design System Context (Optional)

Check if design tokens exist to provide context-aware recommendations:

- Read `/product/design-system/colors.json` (if exists)
- Read `/product/design-system/typography.json` (if exists)
- Read `/product/target-audience.md` (if exists)

If design tokens exist, recommendations should reference them specifically.
If they don't exist, recommendations should be general design principles.

## Step 3: Analyze the Screen Context

Read and understand the screen file:
- Screen type and purpose
- Target audience
- User flow (from → to)
- Current concerns the user mentioned
- Screen source (screenshot, URL, or description)

Use this context to make the audit relevant and specific.

## Step 4: Comprehensive Design Analysis

Provide detailed analysis across all key design areas. Be educational - explain the "why" behind each recommendation.

### 4.1 Visual Hierarchy & Information Architecture

Analyze:
- What should draw attention first? Is it clear?
- How is information organized and prioritized?
- Does the hierarchy support the screen's purpose?
- Are calls-to-action (CTAs) prominent enough?

**For dashboards specifically:**
- Is the most important information (next action, current state) immediately visible?
- Are progress indicators clear and motivating?
- Is there a clear entry point for the user's next action?

Provide specific recommendations with rationale.

### 4.2 Layout & Composition

Analyze:
- How is content organized spatially?
- Is there proper balance and visual weight distribution?
- How is whitespace used?
- Are related elements grouped together?
- Does the layout guide the user's eye through a logical flow?

**Common issues to address:**
- Text-heavy layouts → Recommend breaking into scannable chunks
- Lack of breathing room → Recommend spacing improvements
- Poor grouping → Recommend visual separation techniques

### 4.3 Spacing & Rhythm

Analyze:
- Is spacing consistent throughout?
- Is there a clear rhythm and vertical spacing pattern?
- Are spacing values logical and proportional?
- Does spacing create clear visual grouping?

**If design tokens exist:**
Reference the spacing scale and recommend specific values.

**If design tokens don't exist:**
Recommend establishing a spacing scale (e.g., 4px, 8px, 16px, 24px, 32px, 48px).

### 4.4 Typography & Readability

Analyze:
- Is text hierarchy clear (headings vs body)?
- Are font sizes appropriate for readability?
- Is line length comfortable for reading (45-75 characters)?
- Is line height sufficient for readability (1.5-1.7 for body text)?
- Are font weights used effectively to create hierarchy?

**If typography tokens exist:**
Recommend how to apply the defined fonts and type scale.

**If typography tokens don't exist:**
Provide general typography best practices.

### 4.5 Color & Contrast

Analyze:
- Is color used to support hierarchy and meaning?
- Are CTAs visually distinct through color?
- Is there sufficient contrast for readability?
- Does color usage align with common patterns (red = danger, green = success)?

**If color tokens exist (e.g., indigo/emerald/slate):**
- Recommend specific uses: "Use `indigo-600` for primary CTAs"
- Suggest color applications: "Use `emerald-500` for progress indicators"
- Reference the neutral palette: "Use `slate-700` for body text, `slate-500` for secondary text"

**Accessibility:**
- Check WCAG AA contrast requirements (4.5:1 for text, 3:1 for UI elements)
- Recommend specific color combinations that pass

### 4.6 Accessibility (WCAG)

Analyze and provide recommendations for:
- **Keyboard navigation:** Can users navigate without a mouse?
- **Focus states:** Are interactive elements clearly focusable?
- **Screen reader support:** Is content properly structured with semantic HTML?
- **Alt text:** Are images and icons described?
- **Color independence:** Is information conveyed without relying solely on color?
- **Touch targets:** Are buttons/links large enough (min 44x44px)?

Rate accessibility: **Basic / Good / Excellent**

## Step 5: Address User's Specific Concerns

Review the "Current Concerns" from the screen file and address each one directly:

For each concern:
1. Validate or clarify the concern
2. Explain why it matters
3. Provide specific, actionable recommendations
4. Show examples or patterns that solve it

## Step 6: Generate Prioritized Recommendations

Organize all recommendations into:

### Quick Wins (Low effort, high impact)
- Simple changes that can be implemented immediately
- Examples: adjust spacing, increase CTA button size, improve color contrast

### High Priority (Critical issues)
- Problems that significantly impact usability or comprehension
- Examples: unclear visual hierarchy, inaccessible contrast, confusing layout

### Medium Priority (Important improvements)
- Issues that affect experience but aren't blocking
- Examples: inconsistent spacing, suboptimal typography, minor layout adjustments

### Low Priority (Nice-to-haves)
- Polish and refinement
- Examples: subtle animations, micro-interactions, advanced states

## Step 7: Provide Specific Implementation Guidance

For top 3-5 recommendations, provide concrete implementation details:

**Example format:**
```
### Recommendation: Make "Next Action" button more prominent

**Current state:** Button likely blends with other UI elements

**Why it matters:** The dashboard's primary purpose is to guide users to their next step. If the CTA isn't immediately visible, users will feel lost.

**How to fix:**
1. Size: Increase button to `h-12` (48px) with `px-6` padding
2. Color: Use primary color `indigo-600` background with white text
3. Position: Place it prominently in top-right or center after progress indicators
4. Visual weight: Use `font-semibold` and consider adding a subtle shadow
5. Contrast: Ensure surrounding elements use neutral colors so button stands out

**Expected impact:** Users immediately identify their next action, reducing friction and cognitive load.
```

## Step 8: Educational Context

For 2-3 key recommendations, provide design principle education:

Explain:
- What design principle applies (proximity, contrast, hierarchy, etc.)
- Why this principle matters
- How professional designers think about this

**Example:**
"This follows the **Law of Proximity** - elements that are closer together are perceived as related. By reducing space between related items and increasing space between different groups, you create clear visual boundaries without needing borders or dividers."

## Step 9: Create the Audit Report

Create a comprehensive audit report at `/product/screens/[screen-name]/audit.md`.

Use this exact format:

```markdown
# Audit: [Screen Name]

**Audit Date:** [Current date]
**Screen Type:** [Type]
**Design Tokens Applied:** [Yes/No - if yes, list: colors, typography]

---

## Executive Summary

[2-3 sentence overview of the screen's current state and main opportunities for improvement]

**Overall Assessment:** [Needs Improvement / Good / Excellent]

**Key Strengths:**
- [Strength 1]
- [Strength 2]

**Key Opportunities:**
- [Opportunity 1]
- [Opportunity 2]

---

## Detailed Analysis

### 1. Visual Hierarchy & Information Architecture

**Current State:**
[Analysis]

**Assessment:** [Rating 1-5: ⭐⭐⭐⭐⭐]

**Recommendations:**
- [Specific recommendation with rationale]
- [Specific recommendation with rationale]

---

### 2. Layout & Composition

**Current State:**
[Analysis]

**Assessment:** [Rating 1-5: ⭐⭐⭐⭐⭐]

**Recommendations:**
- [Specific recommendation with rationale]
- [Specific recommendation with rationale]

---

### 3. Spacing & Rhythm

**Current State:**
[Analysis]

**Assessment:** [Rating 1-5: ⭐⭐⭐⭐⭐]

**Recommendations:**
- [Specific recommendation with rationale]
- [Specific recommendation with rationale]

[If design tokens exist:]
**Recommended Spacing Scale:**
- Tight: `gap-2` (8px)
- Normal: `gap-4` (16px)
- Relaxed: `gap-6` (24px)
- Loose: `gap-8` (32px)

---

### 4. Typography & Readability

**Current State:**
[Analysis]

**Assessment:** [Rating 1-5: ⭐⭐⭐⭐⭐]

**Recommendations:**
- [Specific recommendation with rationale]

[If typography tokens exist:]
**Recommended Type Scale:**
- Hero: `text-4xl font-bold` (36px, [Heading Font])
- H1: `text-3xl font-bold` (30px, [Heading Font])
- H2: `text-2xl font-semibold` (24px, [Heading Font])
- H3: `text-xl font-semibold` (20px, [Heading Font])
- Body: `text-base` (16px, [Body Font])
- Small: `text-sm` (14px, [Body Font])
- Code: `font-mono text-sm` ([Mono Font])

---

### 5. Color & Contrast

**Current State:**
[Analysis]

**Assessment:** [Rating 1-5: ⭐⭐⭐⭐⭐]

**Recommendations:**
- [Specific recommendation with rationale]

[If color tokens exist:]
**Recommended Color Applications:**
- **Primary actions:** `bg-[primary]-600 hover:bg-[primary]-700 text-white`
- **Secondary actions:** `bg-[secondary]-100 hover:bg-[secondary]-200 text-[secondary]-700`
- **Success states:** `bg-emerald-50 text-emerald-700 border-emerald-200`
- **Text:** `text-[neutral]-900` (headings), `text-[neutral]-700` (body), `text-[neutral]-500` (secondary)
- **Backgrounds:** `bg-[neutral]-50` (page), `bg-white` (cards)
- **Borders:** `border-[neutral]-200`

---

### 6. Accessibility

**Current State:**
[Analysis]

**Assessment:** [Basic / Good / Excellent]

**Recommendations:**
- [Specific recommendation with rationale]

**WCAG Compliance Checklist:**
- [ ] Contrast ratios meet AA standards (4.5:1 text, 3:1 UI)
- [ ] Keyboard navigation works for all interactive elements
- [ ] Focus states are visible
- [ ] Semantic HTML structure (headings, landmarks)
- [ ] Touch targets are minimum 44x44px
- [ ] No information conveyed by color alone

---

## Addressing Your Specific Concerns

[For each concern from the screen file, provide detailed response]

### Concern: [User's concern]

**Analysis:**
[Your assessment of this concern]

**Recommendation:**
[Specific solution with implementation details]

---

## Prioritized Action Plan

### 🔥 Quick Wins (Implement First)
1. **[Recommendation]** - [Brief why]
2. **[Recommendation]** - [Brief why]
3. **[Recommendation]** - [Brief why]

### ⚠️ High Priority (Critical Issues)
1. **[Recommendation]** - [Brief why]
2. **[Recommendation]** - [Brief why]

### 📋 Medium Priority (Important Improvements)
1. **[Recommendation]** - [Brief why]
2. **[Recommendation]** - [Brief why]

### ✨ Low Priority (Polish & Refinement)
1. **[Recommendation]** - [Brief why]
2. **[Recommendation]** - [Brief why]

---

## Implementation Guide

### Top Recommendation: [Title]

**Current state:** [Description]

**Why it matters:** [Rationale with design principle]

**How to fix:**
1. [Step-by-step implementation]
2. [With specific values]
3. [And code examples if helpful]

**Expected impact:** [Outcome]

---

### Second Recommendation: [Title]

[Same format as above]

---

### Third Recommendation: [Title]

[Same format as above]

---

## Design Principles Applied

### [Principle 1]: [Name]
[Explanation of the principle and how it applies to this screen]

### [Principle 2]: [Name]
[Explanation of the principle and how it applies to this screen]

---

## Next Steps

1. **Review recommendations** - Prioritize based on your goals and resources
2. **Implement changes** - Start with Quick Wins for immediate impact
3. **Track iteration** - Run `/track-iteration [screen-name]` after making changes to compare versions
4. **Check consistency** - Run `/check-consistency [screen-name]` to validate design token usage
5. **Iterate** - Design is iterative; expect multiple rounds of refinement

---

## Resources

- [Design Tokens]({path-to-tokens}) - Reference your color palette and typography
- [Target Audience]({path-to-audience}) - Keep your users' needs in mind
- [WCAG Guidelines](https://www.w3.org/WAI/WCAG21/quickref/) - Accessibility standards

**Questions or need clarification?** Design OS is here to help you improve iteratively.
```

## Step 10: Confirm Completion

Let the user know:

"I've completed the comprehensive design audit for **[Screen Name]**.

**Audit report saved:** `/product/screens/[screen-name]/audit.md`

**Summary:**
- Overall assessment: [Rating]
- [X] recommendations across 6 design areas
- [X] quick wins identified
- [X] high-priority issues flagged
- Accessibility rating: [Rating]

**Key findings:**
1. [Top finding]
2. [Second finding]
3. [Third finding]

**Recommended next steps:**
1. Review the full audit report at `/product/screens/[screen-name]/audit.md`
2. Start with the Quick Wins section for immediate improvements
3. After making changes, run `/track-iteration [screen-name]` to measure progress

The audit addresses all your specific concerns:
- [Concern 1]: [Brief solution]
- [Concern 2]: [Brief solution]
- [Concern 3]: [Brief solution]

Would you like me to clarify any recommendations or dive deeper into specific areas?"

## Important Notes

- **Be specific, not generic** - Avoid vague advice like "improve hierarchy." Say "Increase the 'Start' button size to 48px and use indigo-600 background."
- **Be educational** - Explain design principles so users learn, not just apply
- **Reference design tokens** - When tokens exist, show exactly how to use them
- **Address concerns** - The user's specific concerns should be thoroughly addressed
- **Prioritize ruthlessly** - Not all recommendations are equal; help users focus
- **Be encouraging** - Frame issues as opportunities; design is iterative
- **Provide rationale** - Always explain the "why" behind recommendations
- **Use consistent ratings** - ⭐ ratings (1-5) for each area help track progress
- **Include code examples** - Tailwind classes make recommendations immediately actionable
