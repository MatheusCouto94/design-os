# UX Writing & Content Workflows

Focuses on improving clarity, microcopy, error messages, and overall content strategy to make the product easier to understand and use.

---

## 1. Voice & Tone Foundation Workflow

**Purpose:** Establish brand voice, personality, and writing guidelines that will guide all content decisions.

**Steps:**
1. Review product overview and target audience
2. Ask about brand personality (formal/casual, playful/serious, technical/simple, friendly/professional)
3. Define voice attributes (consistent characteristics that never change)
4. Define tone variations (how voice adapts to different contexts: onboarding, errors, success, settings)
5. Create writing guidelines (dos and don'ts, preferred terminology)
6. Provide examples for different contexts
7. Define standard terminology and word choices
8. Present draft and refine
9. Create voice & tone guide document

**Inputs:**
- Product overview and vision
- Target audience definition
- Brand personality preferences
- Any existing brand guidelines

**Outputs:**
- `/product/content/voice-and-tone.md` with voice attributes, tone guidelines, examples, and terminology standards
- Creates Voice & Tone guidelines that inform all content work

**Command:** `/voice-and-tone` (to be implemented)

---

## 2. Content Audit Workflow

**Purpose:** Review all existing copy across screens for clarity, tone consistency, and effectiveness.

**Steps:**
1. Read all screens in the project
2. Extract all copy (headings, body text, buttons, labels, messages)
3. Evaluate each piece of content for:
   - Clarity (is it easy to understand?)
   - Brevity (is it concise without losing meaning?)
   - Tone consistency (matches voice & tone guide?)
   - Action-oriented (does it guide the user to next steps?)
   - Accessibility (plain language, appropriate reading level)
4. Identify problematic copy
5. Flag jargon, passive voice, unclear instructions, confusing language
6. Generate improvement suggestions with rationale
7. Prioritize issues (critical clarity issues vs nice-to-have improvements)
8. Create comprehensive audit report

**Inputs:**
- All Screen entities in project
- Voice & Tone guidelines (if available)
- Target audience reading level

**Outputs:**
- `/product/content/content-audit.md` with findings, issues categorized by severity, and prioritized recommendations
- Creates Content audit report

**Command:** `/audit-content` (to be implemented)

---

## 3. Microcopy & Messaging Workflow

**Purpose:** Deep dive into specific copy types with targeted improvements and best practices.

**Steps:**
1. Select copy type(s) to focus on (or review all):
   - Button text and CTAs (calls-to-action)
   - Error messages and validation feedback
   - Empty states and zero-data scenarios
   - Success messages and confirmations
   - Tooltips and help text
   - Form labels and placeholders
   - Loading states and progress indicators
2. For each copy type:
   - Review current copy across all screens
   - Evaluate clarity and usefulness
   - Check tone consistency
   - Ensure actionability (what should the user do?)
   - Verify accessibility (clear for screen readers, plain language)
3. Provide best practices and patterns for each type
4. Generate improved versions with explanations
5. Show before/after comparisons
6. Create microcopy guide with reusable patterns

**Inputs:**
- Screen entities with specific copy types
- Voice & Tone guidelines
- Copy type focus areas

**Outputs:**
- `/product/content/microcopy-guide.md` with best practices, improved copy examples, before/after comparisons, and reusable patterns
- Creates/Updates content recommendations for screens

**Command:** `/optimize-microcopy` (to be implemented)

---

## 4. Content Consistency Check Workflow

**Purpose:** Validate tone consistency and terminology across all screens to ensure a cohesive user experience.

**Steps:**
1. Read Voice & Tone guidelines
2. Read all screens in project
3. Check for:
   - Tone inconsistencies (switches between formal/casual inappropriately)
   - Terminology inconsistencies (same concept called different names)
   - Voice violations (doesn't match established voice attributes)
   - Writing guideline violations (uses forbidden phrases or patterns)
4. Identify screens with inconsistencies
5. Compare similar copy types across screens (all error messages, all CTAs, all empty states)
6. Generate consistency report with specific violations
7. Suggest corrections to align with guidelines
8. Calculate consistency score

**Inputs:**
- Voice & Tone guidelines
- All Screen entities
- Terminology standards

**Outputs:**
- `/product/content/consistency-check.md` with inconsistencies, violations, corrections, and consistency score
- Creates consistency report with actionable fixes

**Command:** `/check-content-consistency` (to be implemented)

---

## Workflow Sequence

These workflows support a systematic approach to content improvement:

1. **Voice & Tone Foundation** - Start here to establish your brand's writing guidelines
2. **Content Audit** - Review all existing copy to identify issues (run after adding screens)
3. **Microcopy & Messaging** - Deep dive into specific copy types for targeted improvements
4. **Content Consistency Check** - Validate consistency after making changes (run periodically)

**Typical user flow:**
- Define Voice & Tone → Audit Content → Address issues → Optimize Microcopy → Check Consistency → Repeat
- Or: Add screens → Audit Content → Optimize Microcopy → Check Consistency

Once content is clear and consistent, users can move to the Export & Handoff section to package everything for implementation.
