# Screen Design & Audit Workflows

The main workspace for analyzing, critiquing, and improving individual UI screens with AI-powered feedback on hierarchy, layout, and UX decisions.

---

## 1. Screen Import & Setup Workflow

**Purpose:** Add a new screen to the project with proper context and metadata to enable meaningful analysis.

**Steps:**
1. Choose import method (screenshot upload, URL, Figma link, or text description)
2. Upload/provide the screen
3. Add screen context:
   - Screen name and type (homepage, dashboard, login, settings, etc.)
   - Purpose (what should users accomplish on this screen?)
   - Target audience (which user type from target-audience.md uses this?)
   - User flow context (where does the user come from? where do they go next?)
   - Section tag (which product section does this screen belong to?)
4. Extract/identify key elements (if screenshot or visual)
5. Create screen entry in project

**Inputs:**
- Screen source (image file, URL, Figma link, or text description)
- Screen context and metadata

**Outputs:**
- `/product/screens/[screen-name].md` with screen info, context, and metadata
- Creates Screen entity with all context

**Command:** `/add-screen` (to be implemented)

---

## 2. Comprehensive Audit Workflow

**Purpose:** Deep analysis covering hierarchy, layout, spacing, typography, color, accessibility, and AI critique with actionable recommendations.

**Steps:**
1. Read screen data and context (purpose, audience, user flow)
2. Analyze visual hierarchy (what draws attention first, information architecture, focal points)
3. Evaluate layout and composition (balance, whitespace, alignment, grouping)
4. Check spacing consistency (gaps, padding, margins against spacing scale)
5. Review typography usage (hierarchy, readability, font sizes against type scale)
6. Assess color usage (contrast, semantic meaning, accessibility, palette adherence)
7. Check accessibility (WCAG compliance, keyboard navigation, screen reader support, focus states)
8. Generate AI critique with prioritized recommendations
9. Identify quick wins vs major improvements
10. Present findings with specific, actionable suggestions
11. Create comprehensive audit report

**Inputs:**
- Screen entity with context
- Design system tokens (if available)
- Target audience definition

**Outputs:**
- `/product/screens/[screen-name]/audit.md` with comprehensive analysis, prioritized recommendations, and action items
- Creates Critique entity linked to Screen

**Command:** `/audit-screen` (to be implemented)

---

## 3. Design System Consistency Check Workflow

**Purpose:** Validate the screen uses established design tokens correctly and maintains consistency with other screens in the product.

**Steps:**
1. Read design system tokens (colors, spacing, typography)
2. Analyze screen for token usage
3. Identify deviations from established tokens:
   - Colors not in defined palette
   - Spacing values not in spacing scale
   - Font sizes not in type scale
   - Inconsistent component patterns
4. Compare with other screens for cross-screen consistency
5. Generate consistency report with specific token violations
6. Suggest corrections using proper design tokens
7. Calculate consistency score
8. Create consistency check report

**Inputs:**
- Screen entity
- DesignSystem and DesignToken entities
- Other Screen entities in project for comparison

**Outputs:**
- `/product/screens/[screen-name]/consistency-check.md` with violations, corrections, and consistency score
- Creates/Updates Critique entity with consistency findings

**Command:** `/check-consistency` (to be implemented)

---

## 4. Iteration & Improvement Tracking Workflow

**Purpose:** Re-analyze improved versions of a screen and compare changes to track progress and validate improvements.

**Steps:**
1. Select screen to iterate on
2. Upload new version (screenshot, URL, or description of changes made)
3. Run analysis on new version
4. Compare with previous version:
   - What improved? (hierarchy, spacing, color, accessibility)
   - What new issues appeared?
   - Which recommendations were addressed?
   - What's still pending?
5. Generate side-by-side comparison
6. Calculate improvement metrics (accessibility score, consistency score, issues resolved)
7. Update screen with new version
8. Archive previous version for history

**Inputs:**
- Screen entity with existing audit/critique
- New version source (image, URL, or description)
- Previous audit and critique data

**Outputs:**
- `/product/screens/[screen-name]/iteration-[n].md` with comparison, improvement metrics, and remaining issues
- Updates Screen entity with new version
- Creates new Critique for iteration

**Command:** `/track-iteration` (to be implemented)

---

## Workflow Sequence

These workflows support an iterative design improvement process:

1. **Screen Import & Setup** - Start here to add a screen with context
2. **Comprehensive Audit** - Get deep analysis and recommendations (run this first)
3. **Design System Consistency Check** - Validate against your design system (optional, run after establishing design tokens)
4. **Iteration & Improvement Tracking** - After making changes, compare versions and track progress

**Typical user flow:**
- Add screen → Audit → Review recommendations → Make changes → Track iteration → Repeat
- Or: Add screen → Audit → Check consistency → Address both critiques → Track iteration

Once screens are audited and improved, users can move to the UX Writing & Content section to refine microcopy and messaging.
