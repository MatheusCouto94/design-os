# Track Iteration

You are helping the user track improvements to a screen by comparing versions and measuring progress. This completes the improvement feedback loop: import → audit → improve → track → iterate.

## Step 1: Check Prerequisites

First, verify the screen exists and has been audited:

Ask the user: "Which screen would you like to track an iteration for?"

If they don't provide a screen name, list available screens by reading `/product/screens/` directory.

Once they specify a screen name, verify:
1. Screen file exists at `/product/screens/[screen-name].md`
2. Previous audit exists at `/product/screens/[screen-name]/audit.md`

If screen doesn't exist:
"I don't see a screen named **[screen-name]**. Please run `/add-screen` first to import the screen."

If audit doesn't exist:
"I don't see an audit for **[screen-name]** yet. Please run `/audit-screen [screen-name]` first to establish a baseline."

Stop here if prerequisites are missing.

## Step 2: Explain the Process

"Let's track your improvements to **[Screen Name]**.

I'll help you:
1. **Provide the updated version** — screenshot, URL, or description of changes
2. **Re-analyze the screen** — evaluate the current state
3. **Compare with previous audit** — identify what improved and what's pending
4. **Calculate improvement metrics** — measure progress across design areas
5. **Generate iteration report** — document changes and remaining work

This helps you see the impact of your design changes and guides the next round of improvements."

## Step 3: Gather Updated Screen Information

Ask the user how they want to provide the updated version:

"How would you like to provide the updated version of this screen?"

Options:
1. **Screenshot** - Provide path to new screenshot
2. **URL** - Link to updated live page
3. **Description** - Describe what you changed
4. **Figma/Design file** - Link to updated design

Based on their choice:

### Method A: Screenshot
"Please provide the path to the new screenshot."

Verify the file exists and read it (if image). Compare visually with the original if original was also a screenshot.

### Method B: URL
"Please provide the URL to the updated page."

Save the URL for reference.

### Method C: Description
"Please describe what changes you made. Be as specific as possible:
- Which recommendations from the audit did you implement?
- What design elements did you change? (spacing, colors, typography, layout, etc.)
- Any new concerns or issues that appeared?"

Gather detailed description of changes.

### Method D: Figma/Design File
"Please provide the link to the updated design file."

Save the link.

## Step 4: Read Previous Audit

Read the previous audit at `/product/screens/[screen-name]/audit.md`.

Extract:
- Overall assessment rating (1-5)
- Ratings for each of the 6 design areas
- All recommendations (Quick Wins, High Priority, Medium, Low)
- Specific issues identified
- User's original concerns

This establishes the baseline for comparison.

## Step 5: Re-Analyze the Updated Screen

Perform a fresh analysis of the updated screen using the same 6-area framework:

1. Visual Hierarchy & Information Architecture
2. Layout & Composition
3. Spacing & Rhythm
4. Typography & Readability
5. Color & Contrast
6. Accessibility

For each area:
- Assess the current state
- Identify improvements from previous version
- Note any new issues that emerged
- Rate the area (1-5 stars)

Be specific about what changed and whether it improved or regressed.

## Step 6: Compare Versions

Create a detailed comparison:

### 6.1 Improvements Identified

For each recommendation from the previous audit, determine:
- ✅ **Fully addressed** - Implemented as recommended
- 🔄 **Partially addressed** - Implemented but not completely or differently than suggested
- ⏳ **Not yet addressed** - Still pending

Document specific evidence of implementation:
- "Quick Win #1: Button size increased to h-12 ✅"
- "High Priority #2: Hero section created with text-4xl heading ✅"
- "Medium Priority #1: Progress bars added 🔄 (implemented but using different colors)"

### 6.2 Rating Changes

Compare ratings across all areas:

```
Area                    | Before | After | Change
------------------------|--------|-------|--------
Visual Hierarchy        | ⭐⭐⭐   | ⭐⭐⭐⭐⭐ | +2 ⬆️
Layout & Composition    | ⭐⭐⭐   | ⭐⭐⭐⭐  | +1 ⬆️
Spacing & Rhythm        | ⭐⭐    | ⭐⭐⭐⭐  | +2 ⬆️
Typography             | ⭐⭐⭐⭐  | ⭐⭐⭐⭐⭐ | +1 ⬆️
Color & Contrast       | ⭐⭐⭐⭐  | ⭐⭐⭐⭐  | 0 ➡️
Accessibility          | Good   | Excellent| ⬆️
```

### 6.3 New Issues

Identify any new problems that weren't present before:
- Unintended side effects of changes
- New accessibility issues
- Different problems that emerged

### 6.4 Calculate Improvement Metrics

Generate quantitative metrics:

**Implementation Rate:**
- X out of Y recommendations fully addressed (X/Y = Z%)
- Quick Wins: X/Y implemented
- High Priority: X/Y implemented
- Medium Priority: X/Y implemented
- Low Priority: X/Y implemented

**Quality Improvement:**
- Average rating before: X.X/5.0
- Average rating after: X.X/5.0
- Improvement: +X.X points (+XX%)

**Overall Progress:**
- Recommendations addressed: X/Y (Z%)
- Rating improvement: +X.X points
- New issues introduced: X
- **Net progress: [Significant/Moderate/Minimal/Regressed]**

## Step 7: Generate Iteration Report

Create a comprehensive iteration report at `/product/screens/[screen-name]/iteration-[n].md`.

Determine iteration number by counting existing iteration files (iteration-1, iteration-2, etc.).

Use this exact format:

```markdown
# Iteration [N]: [Screen Name]

**Iteration Date:** [Current date]
**Previous Audit Date:** [Date from audit.md]
**Changes Source:** [Screenshot/URL/Description/Figma]
**Time Between Iterations:** [X days]

---

## Executive Summary

[2-3 sentence summary of what changed and overall impact]

**Overall Progress:** [Significant/Moderate/Minimal/Regressed]

**Key Improvements:**
- [Improvement 1]
- [Improvement 2]
- [Improvement 3]

**New Issues:**
- [Issue 1] (if any)
- [Issue 2] (if any)

**Next Focus:**
- [Top remaining priority]
- [Second priority]

---

## Changes Made

**User-Reported Changes:**
[What the user said they changed, if description method used]

**Observed Changes:**
[What you can observe from the new version]

---

## Recommendation Implementation Status

### ✅ Fully Addressed (X recommendations)

1. **[Recommendation title]** (from [Priority level])
   - **Previous state:** [Brief description]
   - **Change made:** [What was implemented]
   - **Assessment:** [Why this successfully addresses the issue]

2. **[Recommendation title]**
   - **Previous state:** [Brief]
   - **Change made:** [What was done]
   - **Assessment:** [Impact]

### 🔄 Partially Addressed (X recommendations)

1. **[Recommendation title]** (from [Priority level])
   - **Previous state:** [Brief]
   - **Change made:** [What was done]
   - **Why partial:** [What's missing or different from recommendation]
   - **Remaining work:** [What still needs to be done]

### ⏳ Not Yet Addressed (X recommendations)

1. **[Recommendation title]** (from [Priority level])
   - **Original recommendation:** [Brief summary]
   - **Status:** Not yet implemented
   - **Priority for next iteration:** [Keep same/Elevate/Defer]

---

## Design Area Comparisons

### 1. Visual Hierarchy & Information Architecture

**Previous Rating:** ⭐⭐⭐☆☆ (3/5)
**Current Rating:** ⭐⭐⭐⭐⭐ (5/5)
**Change:** +2 ⬆️ **Significant Improvement**

**What Improved:**
- [Specific improvement 1 with evidence]
- [Specific improvement 2 with evidence]

**What Remained the Same:**
- [Element that didn't change]

**New Observations:**
- [Anything new to note]

---

### 2. Layout & Composition

**Previous Rating:** ⭐⭐⭐☆☆ (3/5)
**Current Rating:** ⭐⭐⭐⭐☆ (4/5)
**Change:** +1 ⬆️ **Moderate Improvement**

[Same structure as above]

---

### 3. Spacing & Rhythm

[Same structure]

---

### 4. Typography & Readability

[Same structure]

---

### 5. Color & Contrast

[Same structure]

---

### 6. Accessibility

**Previous Rating:** Good
**Current Rating:** Excellent
**Change:** ⬆️ **Improvement**

[Same structure]

---

## New Issues Identified

[If any new problems appeared]

### Issue 1: [Title]
**Description:** [What the new issue is]
**Severity:** [High/Medium/Low]
**Likely Cause:** [Why this appeared - related to changes made?]
**Recommendation:** [How to fix]

### Issue 2: [Title]
[Same structure]

---

## Improvement Metrics

### Implementation Rate

**Overall:** X/Y recommendations addressed (Z%)

**By Priority:**
- Quick Wins: X/Y implemented (Z%)
- High Priority: X/Y implemented (Z%)
- Medium Priority: X/Y implemented (Z%)
- Low Priority: X/Y implemented (Z%)

**By Design Area:**
- Visual Hierarchy: X/Y addressed
- Layout: X/Y addressed
- Spacing: X/Y addressed
- Typography: X/Y addressed
- Color: X/Y addressed
- Accessibility: X/Y addressed

### Quality Metrics

**Rating Changes:**
- Average rating before: X.X/5.0
- Average rating after: X.X/5.0
- **Improvement: +X.X points (+XX%)**

**Individual Area Changes:**
- Visual Hierarchy: +X
- Layout: +X
- Spacing: +X
- Typography: +X
- Color: +X
- Accessibility: [Improved/Same]

### Progress Assessment

**Velocity:**
- Recommendations implemented: X
- Days since last audit: Y
- Implementation rate: X/Y recommendations per day

**Quality vs Speed:**
- [Assessment of whether changes were thorough or rushed]
- [Note on quality of implementation]

---

## Remaining Work

### High Priority (Implement Next)

1. **[Recommendation that's still pending and most important]**
   - From: [Original priority level]
   - Why critical: [Rationale]
   - Estimated effort: [Low/Medium/High]

2. **[Second most important]**
   [Same structure]

### Medium Priority

[List remaining medium priority items]

### Low Priority

[List remaining low priority items]

### Newly Identified

[Any new recommendations from this iteration's analysis]

---

## Next Steps

1. **Immediate focus:** [Top 1-2 remaining priorities]
2. **When ready:** Run `/track-iteration [screen-name]` again to measure next round of improvements
3. **For new screens:** Consider running `/add-screen` for other screens to expand your audit coverage
4. **Consistency:** Run `/check-consistency [screen-name]` to validate design token usage

---

## Iteration History

- **Iteration 1:** [Date] - [Brief summary]
- **Iteration 2:** [This iteration] - [Brief summary]
[Add line for each iteration]

---

## Congratulations!

[Encouraging message about progress made, highlighting specific wins]

Design is iterative - each round of feedback and improvement brings you closer to a polished, professional product. Your implementation of [X] recommendations shows commitment to design quality.

**Keep going!** [Motivational statement based on progress]
```

## Step 8: Update Screen File

Update the main screen file at `/product/screens/[screen-name].md`:

1. Update **Status** field to "Iteration [N]"
2. Update **Date** to current date
3. Add an **Iteration History** section if it doesn't exist
4. Append the new iteration to the history

Example addition:
```markdown
## Iteration History

- **Iteration 1:** 2026-01-05 - Implemented hero section, added progress bars, applied spacing system. Rating improved from 3.0 to 4.2/5.0.
- **Iteration 2:** 2026-01-10 - [Summary when created]
```

## Step 9: Archive Previous Version (Optional)

If a screenshot was provided for this iteration, and a previous screenshot exists:

Copy the old screenshot to an archive:
```bash
cp product/screens/[screen-name]/screenshot.png product/screens/[screen-name]/screenshot-v[n-1].png
cp [new-screenshot-path] product/screens/[screen-name]/screenshot.png
```

This preserves history while keeping the main screenshot current.

## Step 10: Confirm Completion

Let the user know:

"I've completed tracking Iteration [N] for **[Screen Name]**!

**Iteration report saved:** `/product/screens/[screen-name]/iteration-[N].md`

**Progress Summary:**
- **Implementation rate:** X/Y recommendations addressed (Z%)
- **Rating improvement:** From X.X/5.0 to X.X/5.0 (+X.X points, +XX%)
- **Recommendations fully addressed:** X
- **Partially addressed:** Y
- **Still pending:** Z
- **New issues:** N (if any)

**Overall Assessment:** [Significant/Moderate/Minimal] progress

**Key Wins:**
1. [Top improvement]
2. [Second improvement]
3. [Third improvement]

**Remaining Priorities:**
1. [Top remaining item]
2. [Second remaining item]

[If significant progress:]
Excellent work! Your design improvements are measurable and impactful. The screen has improved from [X] to [Y] across multiple areas.

[If moderate progress:]
Good progress! You've addressed [X] key recommendations. Continue with the remaining high-priority items for even greater impact.

[If minimal progress:]
Some progress made, but there's still significant opportunity for improvement. Focus on the high-priority recommendations for the biggest impact.

[If new issues:]
⚠️ Note: [N] new issues were identified. These should be addressed in the next iteration to avoid regression.

**Next steps:**
1. **Review the full iteration report** for detailed analysis
2. **Focus on remaining high-priority items** for next iteration
3. **Run `/track-iteration [screen-name]`** again after making more improvements
4. **Run `/check-consistency [screen-name]`** to validate design token usage

Would you like me to clarify any findings or suggest specific next steps?"

## Important Notes

- **Be encouraging:** Celebrate wins, even small ones. Design iteration is hard work.
- **Be specific:** "Improved spacing" is vague. "Applied 48px gap between sections" is specific.
- **Be honest:** If something regressed or didn't improve, say so respectfully
- **Quantify progress:** Metrics make progress tangible and motivating
- **Compare fairly:** Rate the current version against the same criteria used previously
- **Acknowledge context:** If the user only addressed Quick Wins, that's still progress
- **Guide next steps:** Help prioritize remaining work based on impact
- **Track history:** Iteration reports build a narrative of continuous improvement
- **Motivate continuation:** The goal is to encourage ongoing iteration, not perfection in one round
