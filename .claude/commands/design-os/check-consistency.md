# Check Consistency

You are helping the user validate that a screen follows the established design system tokens and maintains consistency with other screens. This ensures design system adherence and cross-screen coherence.

## Step 1: Check Prerequisites

First, verify that design tokens exist:

Check for:
- `/product/design-system/colors.json`
- `/product/design-system/typography.json`

If neither file exists:

"Before checking consistency, you need to define your design system. Please run `/design-tokens` first to establish your color palette and typography."

Stop here if design tokens don't exist.

Next, verify the screen exists:

Ask the user: "Which screen would you like to check for consistency?"

If they don't provide a screen name, list available screens by reading `/product/screens/` directory.

Once they specify a screen name, read the screen file at `/product/screens/[screen-name].md`.

If it doesn't exist:

"I don't see a screen named **[screen-name]**. Please run `/add-screen` first to import the screen."

Stop here if the screen doesn't exist.

## Step 2: Read Design System Tokens

Read all available design system files:

**Colors:**
```json
{
  "primary": "[color]",
  "secondary": "[color]",
  "neutral": "[color]"
}
```

**Typography:**
```json
{
  "heading": "[font]",
  "body": "[font]",
  "mono": "[font]"
}
```

**Spacing (if exists):**
If `/product/design-system/spacing.json` exists, read it.
Otherwise, use standard Tailwind spacing scale as the reference.

Store these as the "source of truth" for consistency checking.

## Step 3: Read Screen Context

Read the screen file to understand:
- Screen type and purpose
- Screen source (screenshot, URL, description, Figma)
- Any existing audit or context

This helps provide relevant consistency feedback.

## Step 4: Analyze Design Token Usage

Based on the screen source, analyze how design tokens are (or should be) applied:

### 4.1 Color Usage Analysis

Check for:

**Primary Color Usage:**
- Is the primary color (`[primary]`) used for primary CTAs and key actions?
- Are buttons using the correct primary color shades?
- Expected: `bg-[primary]-600`, `hover:bg-[primary]-700`, `text-[primary]-600` for links

**Secondary Color Usage:**
- Is the secondary color (`[secondary]`) used for secondary elements appropriately?
- Expected: Tags, highlights, success states, progress indicators

**Neutral Color Usage:**
- Are neutral colors (`[neutral]`) used for text, backgrounds, and borders?
- Expected:
  - Text: `text-[neutral]-900` (headings), `text-[neutral]-700` (body), `text-[neutral]-500` (secondary)
  - Backgrounds: `bg-[neutral]-50` (page), `bg-white` (cards)
  - Borders: `border-[neutral]-200`

**Non-Token Colors:**
Identify any colors that don't match the defined palette:
- Using different Tailwind colors (e.g., using `blue` when primary is `indigo`)
- Using semantic colors appropriately (red for errors, green for success is acceptable)

**Violations to Flag:**
- Primary CTA using wrong color: "Button uses `bg-blue-600` instead of `bg-[primary]-600`"
- Text using non-neutral colors: "Body text uses `text-gray-700` instead of `text-[neutral]-700`"
- Inconsistent color application: "Some buttons use primary, others use blue"

### 4.2 Typography Usage Analysis

Check for:

**Heading Font:**
- Are headings using the defined heading font (`[heading]`)?
- Expected: `font-sans` class with the heading font loaded globally

**Body Font:**
- Is body text using the defined body font (`[body]`)?
- Expected: Default font or explicit `font-sans`

**Mono Font:**
- Is code/technical content using the defined mono font (`[mono]`)?
- Expected: `font-mono` class

**Type Scale:**
Check if font sizes follow a logical scale:
- Hero: `text-4xl` or larger
- H1: `text-3xl`
- H2: `text-2xl`
- H3: `text-xl`
- H4: `text-lg`
- Body: `text-base`
- Small: `text-sm`

**Violations to Flag:**
- Using `font-serif` when not defined
- Skipping type scale levels (text-base directly to text-3xl without intermediate sizes)
- Inconsistent font weight application

### 4.3 Spacing Usage Analysis

Check for:

**Spacing Scale Consistency:**
If spacing scale is defined, check adherence.
Otherwise, check for logical spacing progression:
- Common scale: 4px (gap-1), 8px (gap-2), 16px (gap-4), 24px (gap-6), 32px (gap-8), 48px (gap-12)

**Spacing Violations:**
- Using arbitrary values: `gap-[17px]` instead of scale values
- Inconsistent spacing: Some cards use `gap-4`, others use `gap-5`
- Missing whitespace: Elements too cramped

**Padding/Margin Consistency:**
- All cards should use same padding (e.g., `p-6`)
- Consistent container margins
- Predictable spacing between sections

### 4.4 Component Pattern Consistency

Check for:

**Button Styles:**
- Are all primary buttons styled consistently?
- Do they use proper height (`h-10`, `h-12`)?
- Do they use consistent padding?
- Do they have focus states?

**Card Styles:**
- Do all cards use consistent border radius, padding, shadows?
- Expected: `rounded-lg`, `p-6`, `border border-[neutral]-200`

**Form Elements:**
- Are input fields styled consistently?
- Do they have proper focus states?

**Violations to Flag:**
- Inconsistent button heights across the screen
- Some cards with shadows, others without
- Different border radius values

## Step 5: Compare with Other Screens

Read other screen files in `/product/screens/` to check cross-screen consistency:

**Check for:**

1. **Color Application:**
   - Do all screens use the primary color for CTAs?
   - Is secondary color used consistently across screens?

2. **Typography Hierarchy:**
   - Do all screens use similar heading sizes for similar content?
   - Is the type scale applied consistently?

3. **Spacing Patterns:**
   - Do screens use similar spacing between sections?
   - Are cards padded consistently across screens?

4. **Component Patterns:**
   - Are buttons styled the same way across screens?
   - Do cards follow the same pattern?

**Violations to Flag:**
- "Dashboard uses `h-12` buttons, but Settings uses `h-10` buttons"
- "Login screen has `p-8` cards, but Dashboard has `p-6` cards"
- "Inconsistent heading sizes: Dashboard uses text-3xl for H1, Profile uses text-2xl"

## Step 6: Calculate Consistency Score

Generate a numerical score based on adherence:

**Scoring System:**

**Color Consistency (30 points):**
- Primary color used correctly: 10 points
- Secondary color used correctly: 10 points
- Neutral colors used correctly: 10 points
- Deduct 2 points for each violation

**Typography Consistency (25 points):**
- Correct fonts used: 10 points
- Type scale followed: 10 points
- Font weights consistent: 5 points
- Deduct 2 points for each violation

**Spacing Consistency (25 points):**
- Spacing scale followed: 15 points
- Padding/margins consistent: 10 points
- Deduct 2 points for each violation

**Component Consistency (20 points):**
- Buttons consistent: 7 points
- Cards consistent: 7 points
- Forms consistent: 6 points
- Deduct 2 points for each violation

**Total Score: X/100**

**Rating:**
- 90-100: Excellent ✅
- 75-89: Good ✓
- 60-74: Fair ⚠️
- Below 60: Needs Improvement ❌

## Step 7: Generate Consistency Report

Create a detailed report at `/product/screens/[screen-name]/consistency-check.md`.

Use this exact format:

```markdown
# Consistency Check: [Screen Name]

**Check Date:** [Current date]
**Design System Version:** [Colors + Typography defined]
**Screens Compared:** [List of other screens checked against]

---

## Consistency Score

**Overall Score:** X/100 - [Rating: Excellent/Good/Fair/Needs Improvement]

**Category Scores:**
- Color Consistency: X/30
- Typography Consistency: X/25
- Spacing Consistency: X/25
- Component Consistency: X/20

---

## Executive Summary

[2-3 sentence summary of consistency status]

**Strengths:**
- [What's consistent and well-applied]
- [Another strength]

**Opportunities:**
- [Main consistency issue]
- [Second issue]

---

## Design Token Adherence

### Colors

**Defined Tokens:**
- Primary: `[primary]`
- Secondary: `[secondary]`
- Neutral: `[neutral]`

#### ✅ Correct Usage

[List elements that correctly use tokens]

Example:
- Primary CTA button uses `bg-[primary]-600` ✓
- Links use `text-[primary]-600` ✓
- Page background uses `bg-[neutral]-50` ✓

#### ❌ Violations

[List violations with specific corrections]

**Violation 1: Wrong primary color shade**
- **Location:** Main action button
- **Current:** `bg-blue-600`
- **Should be:** `bg-[primary]-600` (using your [primary] palette)
- **Impact:** Breaks brand consistency
- **Fix:** Replace `bg-blue-600` with `bg-[primary]-600`

**Violation 2: Inconsistent text colors**
- **Location:** Body text
- **Current:** `text-gray-700`
- **Should be:** `text-[neutral]-700` (using your [neutral] palette)
- **Impact:** Subtle inconsistency with design system
- **Fix:** Replace `text-gray-700` with `text-[neutral]-700`

---

### Typography

**Defined Tokens:**
- Heading: [font name]
- Body: [font name]
- Mono: [font name]

#### ✅ Correct Usage

[List correct font applications]

Example:
- Headings use [heading font] ✓
- Body text uses [body font] ✓
- Code blocks use [mono font] ✓

#### ❌ Violations

**Violation 1: Type scale skipped**
- **Location:** Subheadings
- **Current:** Jumps from `text-base` to `text-3xl`
- **Should be:** Follow type scale progression (text-base → text-lg → text-xl → text-2xl → text-3xl)
- **Impact:** Creates jarring visual jumps
- **Fix:** Use `text-xl` for subheadings

**Violation 2: Inconsistent font weights**
- **Location:** Section headings
- **Current:** Some use `font-bold`, others use `font-semibold`
- **Should be:** Consistently use `font-semibold` for all section headings
- **Impact:** Reduces visual predictability
- **Fix:** Standardize on `font-semibold`

---

### Spacing

**Reference Scale:** 4px, 8px, 16px, 24px, 32px, 48px, 64px (Tailwind: gap-1, gap-2, gap-4, gap-6, gap-8, gap-12, gap-16)

#### ✅ Correct Usage

[List correct spacing applications]

Example:
- Card padding: `p-6` (24px) ✓
- Section gaps: `gap-8` (32px) ✓
- Major zone spacing: `gap-12` (48px) ✓

#### ❌ Violations

**Violation 1: Arbitrary spacing value**
- **Location:** Between progress cards
- **Current:** `gap-5` (20px) - not on standard scale
- **Should be:** `gap-6` (24px) or `gap-4` (16px)
- **Impact:** Creates non-standard spacing pattern
- **Fix:** Change to `gap-6` for medium spacing

**Violation 2: Inconsistent card padding**
- **Location:** Cards throughout screen
- **Current:** Some cards use `p-6`, others use `p-4`, one uses `p-8`
- **Should be:** All cards use consistent `p-6`
- **Impact:** Visual inconsistency and unpredictability
- **Fix:** Standardize all cards to `p-6`

---

### Component Patterns

#### ✅ Correct Usage

[List consistent component applications]

Example:
- Primary buttons: `h-10 px-4 bg-[primary]-600` ✓
- Cards: `rounded-lg border border-[neutral]-200` ✓

#### ❌ Violations

**Violation 1: Inconsistent button heights**
- **Location:** Primary CTA vs secondary buttons
- **Current:** Primary button is `h-12`, secondary buttons are `h-10`
- **Should be:** If intentionally different for hierarchy, OK. If unintentional, standardize.
- **Impact:** May be intentional hierarchy or unintentional inconsistency
- **Recommendation:** If primary button should stand out, keep `h-12`. Otherwise, use `h-10` for all.

**Violation 2: Missing focus states**
- **Location:** All interactive elements
- **Current:** No visible focus state for keyboard navigation
- **Should be:** `focus:ring-2 focus:ring-[primary]-500 focus:ring-offset-2`
- **Impact:** Accessibility issue for keyboard users
- **Fix:** Add focus rings to all buttons and links

---

## Cross-Screen Consistency

**Screens Analyzed:** [List of other screens]

### Consistent Patterns ✅

[List what's consistent across screens]

Example:
- All screens use `bg-[primary]-600` for primary CTAs ✓
- All screens use `p-6` for card padding ✓
- Typography hierarchy is consistent across screens ✓

### Inconsistencies Found ❌

**Inconsistency 1: Button sizing differs**
- **This screen:** Uses `h-12` for primary button
- **Other screens:** Use `h-10` for primary buttons
- **Recommendation:** Standardize on one height. `h-12` (48px) is better for touch targets and prominence.

**Inconsistency 2: Card border radius varies**
- **This screen:** Uses `rounded-lg` (8px)
- **Other screens:** Some use `rounded-md` (6px), others use `rounded-lg`
- **Recommendation:** Standardize all cards to `rounded-lg` for consistency

---

## Detailed Violations & Fixes

### High Priority (Fix These First)

1. **Primary color mismatch** (Color violation)
   - **Current:** Using `blue` instead of `[primary]`
   - **Impact:** Breaks brand identity
   - **Fix:**
     ```
     Replace: bg-blue-600
     With: bg-[primary]-600

     Replace: text-blue-600
     With: text-[primary]-600
     ```
   - **Estimated effort:** 5 minutes

2. **Missing focus states** (Accessibility violation)
   - **Current:** No focus indicators
   - **Impact:** Keyboard users can't navigate
   - **Fix:**
     ```
     Add to all interactive elements:
     focus:ring-2 focus:ring-[primary]-500 focus:ring-offset-2
     ```
   - **Estimated effort:** 10 minutes

### Medium Priority

[List medium priority violations with fixes]

### Low Priority

[List low priority violations with fixes]

---

## Recommended Actions

### Immediate (Critical Fixes)

1. **Replace all `blue` colors with `[primary]`** - Align with brand palette
2. **Add focus states to interactive elements** - Critical for accessibility
3. **Standardize card padding to `p-6`** - Ensure consistent component sizing

### Short-term (Polish)

1. **Review type scale** - Ensure smooth progression without jumps
2. **Standardize button heights** - Choose `h-10` or `h-12` and apply across all screens
3. **Audit spacing for scale adherence** - Replace arbitrary values with scale values

### Long-term (Systemic)

1. **Create component library** - Define button, card, form patterns once
2. **Document design system** - Write usage guidelines for future consistency
3. **Automate checks** - Consider linting rules for design token usage

---

## Design System Compliance

**Token Usage Rate:**
- Colors: X% of color applications use defined tokens
- Typography: X% of text uses defined fonts
- Spacing: X% of spacing values follow the scale
- Components: X% of components follow patterns

**Recommendation:**
[Based on compliance rate, suggest whether design system needs refinement or screen needs fixes]

---

## Next Steps

1. **Review violations** - Focus on high-priority fixes first
2. **Implement corrections** - Use the specific fixes provided above
3. **Re-check consistency** - Run `/check-consistency [screen-name]` again to verify fixes
4. **Apply to other screens** - Use these learnings to fix inconsistencies across all screens
5. **Update design system** - If many violations stem from unclear token definitions, enhance `/design-tokens`

---

## Resources

- [Design System Tokens](/product/design-system/) - Reference your defined colors, typography
- [WCAG Focus Requirements](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html) - Focus state guidelines
- [Tailwind Spacing Scale](https://tailwindcss.com/docs/customizing-spacing) - Standard spacing reference

**Consistency is key to professional design.** These fixes will bring your screen into alignment with your design system and create a more cohesive product experience.
```

## Step 8: Confirm Completion

Let the user know:

"I've completed the consistency check for **[Screen Name]**.

**Consistency report saved:** `/product/screens/[screen-name]/consistency-check.md`

**Consistency Score:** X/100 - [Rating]

**Summary:**
- **Color consistency:** X/30 - [X violations found]
- **Typography consistency:** X/25 - [X violations found]
- **Spacing consistency:** X/25 - [X violations found]
- **Component consistency:** X/20 - [X violations found]

**Top violations:**
1. [Violation 1] - [Fix]
2. [Violation 2] - [Fix]
3. [Violation 3] - [Fix]

**Cross-screen findings:**
[If checked against other screens]
- [X] patterns are consistent across screens ✓
- [Y] inconsistencies found that should be addressed

[If score >= 90:]
Excellent! Your screen adheres closely to the design system. The few violations found are minor and easy to fix.

[If score 75-89:]
Good consistency overall. Address the high-priority violations to bring the screen into full compliance with your design system.

[If score 60-74:]
Fair consistency, but there's room for improvement. Focus on the color and spacing violations first for the biggest impact.

[If score < 60:]
Significant inconsistencies detected. This screen would benefit from a systematic review against your design tokens. Start with high-priority violations and work through the list.

**Recommended next steps:**
1. **Review the full report** for detailed violations and specific fixes
2. **Implement high-priority fixes** - These have the biggest impact on consistency
3. **Re-run `/check-consistency [screen-name]`** after fixes to see improvement
4. **Apply learnings to other screens** - Use this as a template for fixing cross-screen inconsistencies

Would you like clarification on any violations or help prioritizing fixes?"

## Important Notes

- **Be specific:** "Button uses wrong color" is vague. "Button uses `bg-blue-600` instead of `bg-indigo-600`" is actionable.
- **Provide fixes:** Every violation should have a clear "change X to Y" solution
- **Consider intent:** Some variations may be intentional (hero buttons larger than regular buttons). Ask before flagging as violations.
- **Cross-screen context:** If checking multiple screens, violations consistent across all screens might indicate design system needs updating, not screens needing fixes.
- **Prioritize impact:** Not all violations are equal. Accessibility issues > Visual polish.
- **Be encouraging:** High consistency scores deserve recognition.
- **Link to resources:** Help users learn about design systems and consistency principles.
- **Estimate effort:** Knowing a fix takes 5 minutes vs 2 hours helps with prioritization.
- **Celebrate progress:** If re-running after fixes, acknowledge improvements.
