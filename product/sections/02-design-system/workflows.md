# Design System Workflows

This section creates the core visual language: design tokens (colors, spacing, typography), component styles, and consistency rules that will be applied across all screens.

---

## 1. Design Tokens Foundation Workflow

**Purpose:** Establish the initial design token structure and make foundational decisions about the design system approach.

**Steps:**
1. Ask about design direction/style (minimal, bold, playful, professional, modern, etc.)
2. Understand brand constraints (existing colors, fonts, or design assets)
3. Establish token naming conventions (CSS variables, semantic naming)
4. Create initial token structure and organization
5. Generate starter tokens for colors, spacing, and typography
6. Create `/product/design-system/tokens-foundation.md`

**Inputs:**
- Design direction and style preferences
- Brand constraints or existing design assets
- Technical preferences (CSS variables, design token format)

**Outputs:**
- `/product/design-system/tokens-foundation.md` with token structure, naming conventions, and starter tokens
- Creates DesignSystem entity and initial DesignToken entities

**Command:** `/design-tokens` (to be implemented)

---

## 2. Color Palette Workflow

**Purpose:** Choose primary, secondary, neutral, and semantic colors with accessibility guidance and color theory education.

**Steps:**
1. Review existing brand colors if any
2. Ask about color preferences and brand personality
3. Provide color theory guidance (complementary, analogous, triadic schemes)
4. Generate color palette suggestions
5. Check accessibility (WCAG contrast ratios for text on backgrounds)
6. Define semantic colors (success, error, warning, info)
7. Create color scales/shades (light to dark variants)
8. Present draft and refine
9. Update design tokens with finalized color values

**Inputs:**
- Brand colors (if any)
- Color preferences and brand personality
- Accessibility requirements (WCAG AA or AAA)

**Outputs:**
- `/product/design-system/colors.md` with color palette, shades, semantic colors, accessibility notes, and CSS
- Creates/Updates DesignToken entities for colors

**Command:** `/color-palette` (to be implemented)

---

## 3. Typography System Workflow

**Purpose:** Select fonts, define type scale, and establish clear text hierarchy with readability guidance.

**Steps:**
1. Understand content needs (body text, headings, code, UI labels)
2. Provide font pairing guidance and recommendations
3. Suggest font options (Google Fonts, system fonts, custom fonts)
4. Define type scale (font sizes for h1-h6, body, small, etc.)
5. Set line heights and letter spacing for readability
6. Define font weights and when to use them
7. Provide accessibility considerations (minimum sizes, contrast)
8. Present draft and refine
9. Generate CSS and code-ready specifications

**Inputs:**
- Content needs and hierarchy requirements
- Brand personality (formal, casual, technical, friendly)
- Font preferences or constraints

**Outputs:**
- `/product/design-system/typography.md` with fonts, type scale, usage guidelines, and CSS
- Creates/Updates DesignToken entities for typography

**Command:** `/typography-system` (to be implemented)

---

## 4. Spacing & Layout System Workflow

**Purpose:** Define spacing scale, grid system, and layout patterns for consistent spacing throughout the product.

**Steps:**
1. Define base spacing unit (usually 4px or 8px)
2. Generate spacing scale (e.g., 4, 8, 12, 16, 24, 32, 48, 64, 96...)
3. Define grid system (columns, gutters, container widths)
4. Establish layout patterns (max-width, margins, padding conventions)
5. Define breakpoints for responsive design (mobile, tablet, desktop)
6. Provide usage guidelines for different spacing contexts
7. Present draft and refine
8. Generate CSS variables and code

**Inputs:**
- Base unit preference
- Layout approach (fluid vs fixed, responsive strategy)
- Content density preferences (tight vs spacious)

**Outputs:**
- `/product/design-system/spacing.md` with spacing scale, grid system, breakpoints, layout patterns, and CSS
- Creates/Updates DesignToken entities for spacing

**Command:** `/spacing-system` (to be implemented)

---

## 5. Component Patterns Workflow

**Purpose:** Define common component styles (buttons, inputs, cards, etc.) using the established design tokens.

**Steps:**
1. Identify needed components (buttons, forms, cards, navigation, modals, etc.)
2. For each component, define:
   - States (default, hover, active, disabled, focus, loading, error)
   - Variants (primary, secondary, tertiary, sizes: small/medium/large)
   - Spacing and sizing using established spacing tokens
   - Colors using established color tokens
   - Typography using established type scale
3. Provide accessibility guidance (focus states, contrast, ARIA patterns)
4. Generate code-ready specifications (HTML structure, CSS, component props)
5. Present draft and refine
6. Create comprehensive component documentation

**Inputs:**
- List of needed components
- Design tokens from previous workflows (colors, spacing, typography)
- Component priorities (which to define first)

**Outputs:**
- `/product/design-system/components.md` with component specs, states, variants, accessibility notes, and code
- Creates component pattern documentation that references DesignToken entities

**Command:** `/component-patterns` (to be implemented)

---

## Workflow Sequence

These workflows build on each other:

1. **Design Tokens Foundation** - Start here to establish the foundation
2. **Color Palette** → **Typography System** → **Spacing & Layout System** - Can be done in any order, but each refines the token system
3. **Component Patterns** - Should be done last, as it uses all the tokens from previous workflows

Once the Design System is established, users can move on to Screen Design & Audit to apply these tokens to actual UI screens.
