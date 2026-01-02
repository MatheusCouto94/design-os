# Complete Audit Loop - Test Plan

**Created:** 2026-01-02
**Status:** Ready for Testing
**Commands Implemented:** `/add-screen`, `/audit-screen`, `/track-iteration`, `/check-consistency`

---

## The Complete Audit Loop

```
┌──────────────────────────────────────────────────────┐
│                  AUDIT LOOP CYCLE                     │
└──────────────────────────────────────────────────────┘

1. /add-screen
   └─> Import screen with context
       Output: /product/screens/[name].md

2. /audit-screen
   └─> Comprehensive 6-area analysis
       Output: /product/screens/[name]/audit.md

3. [User implements recommendations]

4. /track-iteration
   └─> Compare versions, measure progress
       Output: /product/screens/[name]/iteration-N.md

5. /check-consistency (optional, any time)
   └─> Validate design token usage
       Output: /product/screens/[name]/consistency-check.md

6. Return to step 3 (iterate)
```

---

## Test Scenario: Design OS Dashboard

**Objective:** Validate the complete audit loop using the Design OS Dashboard screen we already imported.

### Test 1: Screen Import ✅ PASSED

**Command:** `/add-screen`
**Status:** Already tested and passed

**Result:**
- Screen imported: `design-os-dashboard`
- Context captured: type, purpose, audience, flow, concerns
- File created: `/product/screens/design-os-dashboard.md`

### Test 2: Initial Audit ✅ PASSED

**Command:** `/audit-screen design-os-dashboard`
**Status:** Already tested and passed

**Result:**
- Comprehensive audit generated
- 23 recommendations across 6 areas
- Design tokens integrated (indigo/emerald/slate)
- File created: `/product/screens/design-os-dashboard/audit.md`
- User concerns addressed

### Test 3: Consistency Check ⏳ READY TO TEST

**Command:** `/check-consistency design-os-dashboard`
**Prerequisites:** Design tokens exist ✅

**Expected Process:**
1. Read colors.json (indigo/emerald/slate) ✅
2. Read typography.json (Inter/JetBrains Mono) ✅
3. Read dashboard screen file ✅
4. Analyze color, typography, spacing, component usage
5. Generate consistency score (0-100)
6. Create detailed violation list with fixes
7. Output to `/product/screens/design-os-dashboard/consistency-check.md`

**Expected Output:**
- Consistency score (likely 70-85 since it's description-based)
- Color violations (if any wrong palette colors detected)
- Typography violations (if any non-Inter fonts detected)
- Spacing violations (if arbitrary spacing detected)
- Component violations (if inconsistent patterns detected)
- Specific fixes for each violation

**How to test manually:**
1. Read the `/check-consistency` command file
2. Follow steps 1-7
3. Generate consistency report for dashboard
4. Validate that report structure matches template
5. Verify recommendations are specific and actionable

### Test 4: Implementation (Simulated) ⏳ READY TO TEST

**Action:** User implements 3-5 Quick Win recommendations from audit

**Simulated changes for testing:**
1. Increase Next Action button to `h-12 px-8`
2. Add spacing system: `space-y-12` for zones
3. Add visual progress bars to cards
4. Apply hero section with `text-4xl` heading
5. Use `bg-indigo-600` for primary CTA

### Test 5: Track Iteration ⏳ READY TO TEST

**Command:** `/track-iteration design-os-dashboard`
**Prerequisites:**
- Screen exists ✅
- Previous audit exists ✅
- User has made changes (simulated above)

**Expected Process:**
1. Read screen file ✅
2. Read previous audit ✅
3. Ask user for updated version (description of changes)
4. Re-analyze screen with 6-area framework
5. Compare with previous audit:
   - Which recommendations were addressed?
   - Which ratings improved?
   - Any new issues?
6. Calculate metrics:
   - Implementation rate (e.g., 5/23 = 22%)
   - Rating improvement (e.g., 3.0 → 4.2)
7. Generate iteration report
8. Output to `/product/screens/design-os-dashboard/iteration-1.md`

**Expected Output:**
- Iteration 1 report created
- Shows 5 recommendations fully addressed
- Rating improved from 3.0/5 to 4.2/5 (+1.2 points, +40%)
- 18 recommendations still pending
- Specific wins documented
- Remaining priorities identified

**How to test manually:**
1. Read the `/track-iteration` command file
2. Follow steps 1-10
3. Provide simulated changes (list above)
4. Generate iteration report
5. Validate comparison logic works
6. Verify metrics are calculated correctly

### Test 6: Second Iteration (Full Loop) ⏳ READY TO TEST

**Scenario:** After tracking iteration 1, user implements more recommendations

**Steps:**
1. Review iteration-1.md for remaining priorities
2. User implements 3-5 more recommendations
3. Run `/track-iteration design-os-dashboard` again
4. Should create `iteration-2.md`
5. Should show cumulative progress (10/23 recommendations now)
6. Should show rating improvement (4.2 → 4.7)

**Validates:**
- Multiple iterations can be tracked
- Progress accumulates correctly
- File naming increments properly (iteration-1, iteration-2, iteration-3...)

### Test 7: Consistency Re-Check ⏳ READY TO TEST

**Command:** `/check-consistency design-os-dashboard`
**After:** User has implemented recommendations from iteration tracking

**Expected:**
- Consistency score improved (e.g., 75 → 88)
- Fewer violations
- Some violations resolved
- New violations identified (if any)

**Validates:**
- Consistency check can be run multiple times
- Shows improvement over time
- Helps validate that fixes actually improved consistency

---

## Success Criteria

### For Complete Audit Loop

✅ **1. Screen Import Works**
- Screen file created with proper format
- Context captured completely
- User concerns documented

✅ **2. Initial Audit Works**
- Comprehensive 6-area analysis
- Specific, actionable recommendations
- Design tokens integrated
- Prioritized action plan

⏳ **3. Consistency Check Works**
- Validates token usage
- Identifies specific violations
- Provides clear fixes
- Generates meaningful score

⏳ **4. Iteration Tracking Works**
- Compares versions accurately
- Calculates meaningful metrics
- Shows clear progress
- Identifies remaining work

⏳ **5. Loop is Cohesive**
- Each command references others appropriately
- File outputs are interconnected
- User can navigate the loop intuitively
- Progress is trackable across iterations

---

## Test Execution Plan

### Phase A: Individual Command Testing

**Priority:** High
**Timeline:** 1 day

1. Test `/check-consistency` on design-os-dashboard
2. Simulate improvements
3. Test `/track-iteration` on design-os-dashboard
4. Validate outputs match specifications

### Phase B: Multi-Iteration Testing

**Priority:** High
**Timeline:** 0.5 days

1. Simulate 2-3 rounds of improvements
2. Run `/track-iteration` after each round
3. Validate progress accumulation
4. Check iteration file naming

### Phase C: Real-World Testing

**Priority:** Medium
**Timeline:** 1-2 days

1. Import a real screen (screenshot or actual URL)
2. Run full audit loop
3. Make actual improvements
4. Track real iterations
5. Validate workflow UX

---

## Known Testing Limitations

1. **Manual Execution Required**
   - Commands not yet automatically registered in skill system
   - Must read command files and follow steps manually
   - Workaround: Read `.claude/commands/design-os/[command].md` and execute

2. **No Screenshot Analysis Yet**
   - Currently testing with description-based screens
   - Screenshot analysis would require image processing
   - Future enhancement

3. **Simulated Changes**
   - Iteration tracking tests will use simulated improvements
   - Can't actually modify screens in test environment
   - Validates logic but not real implementation

---

## Test Results (To Be Filled)

### Test 3: Consistency Check

**Date:** _________
**Tester:** _________
**Result:** [ ] Pass [ ] Fail [ ] Partial

**Notes:**
- Consistency score: ___/100
- Violations found: ___
- Fixes provided: [ ] Specific [ ] Vague
- Report quality: [ ] Excellent [ ] Good [ ] Fair [ ] Poor

**Issues found:**
1. _________
2. _________

---

### Test 5: Track Iteration

**Date:** _________
**Tester:** _________
**Result:** [ ] Pass [ ] Fail [ ] Partial

**Notes:**
- Iteration report created: [ ] Yes [ ] No
- Metrics calculated: [ ] Correctly [ ] Incorrectly
- Comparison accurate: [ ] Yes [ ] Partial [ ] No
- Remaining work identified: [ ] Yes [ ] No

**Issues found:**
1. _________
2. _________

---

### Test 6: Second Iteration

**Date:** _________
**Tester:** _________
**Result:** [ ] Pass [ ] Fail [ ] Partial

**Notes:**
- Second iteration tracked: [ ] Yes [ ] No
- Progress accumulated: [ ] Yes [ ] No
- File naming correct: [ ] Yes [ ] No

**Issues found:**
1. _________
2. _________

---

## Next Steps After Testing

### If All Tests Pass

1. ✅ Mark Phase 1 as complete
2. Update MVP-STATUS.md with test results
3. Document any issues found during testing
4. Move to Phase 2: Enhance design-tokens with spacing

### If Tests Reveal Issues

1. Document specific failures
2. Fix command logic
3. Re-test
4. Update commands as needed

---

## Phase 1 Completion Checklist

- [x] `/add-screen` created and tested
- [x] `/audit-screen` created and tested
- [x] `/track-iteration` created
- [x] `/check-consistency` created
- [ ] `/track-iteration` tested
- [ ] `/check-consistency` tested
- [ ] Multi-iteration flow validated
- [ ] Documentation updated
- [ ] Test results recorded

**Estimated Completion:** When all checkboxes are marked

---

## Conclusion

The complete audit loop is now **implemented and ready for testing**. All four core commands exist with comprehensive logic and detailed output specifications.

**What's Working:**
- Command structure and patterns established
- File organization logical and consistent
- Output formats detailed and actionable
- Design token integration throughout

**What Needs Validation:**
- Actual execution of new commands
- Multi-iteration tracking accuracy
- Consistency scoring logic
- User experience through full loop

**Next Milestone:** Complete testing and validate the loop works end-to-end with real or simulated improvements.
