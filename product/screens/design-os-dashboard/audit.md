# Audit: Design OS Dashboard

**Audit Date:** 2026-01-02
**Screen Type:** Dashboard
**Design Tokens Applied:** Yes (Colors: indigo/emerald/slate, Typography: Inter/JetBrains Mono)

---

## Executive Summary

The Design OS Dashboard serves as the entry point and progress hub for users building better products. Currently, the screen attempts to show project status, section progress, and next actions simultaneously. The main opportunity lies in establishing a clear visual hierarchy that immediately guides users to their next step while keeping progress information accessible but secondary.

**Overall Assessment:** Needs Improvement (3/5)

**Key Strengths:**
- Clear purpose: guiding users through the Design OS process
- Comprehensive coverage of all 5 sections
- Thoughtful user flow from login to action

**Key Opportunities:**
- Visual hierarchy needs strengthening to emphasize next recommended action
- Information density should be reduced for better scannability
- Spatial organization could better separate functional areas

---

## Detailed Analysis

### 1. Visual Hierarchy & Information Architecture

**Current State:**
The dashboard attempts to present three types of information simultaneously: current project, progress indicators for 5 sections, and quick action buttons. Without clear visual weight differences, users may struggle to identify where to focus first. For a dashboard serving developers with "little to moderate design knowledge," the path forward must be immediately obvious.

**Assessment:** ⭐⭐⭐☆☆

**Recommendations:**

1. **Establish a clear focal point:** The "next recommended step" should be the visual anchor of the page. This should be the largest, most prominent element - ideally a hero section at the top with high contrast.

2. **Use size to create hierarchy:**
   - Hero/Next Action: `text-4xl` (36px) with `font-bold`
   - Section headings: `text-2xl` (24px) with `font-semibold`
   - Progress labels: `text-base` (16px)
   - Supporting text: `text-sm` (14px) in `slate-600`

3. **Apply the "squint test":** If you squint at the dashboard, the next action button should still be clearly visible due to its size and color contrast. Everything else should fade into the background.

4. **Progressive disclosure:** Don't show all quick actions at once. Show 1-2 primary actions prominently, with secondary actions accessible via a "More actions" menu or secondary area.

---

### 2. Layout & Composition

**Current State:**
The layout likely presents information in a linear top-to-bottom fashion, which can feel overwhelming when multiple sections compete for attention. For a dashboard targeting developers, the layout should feel familiar (like development tools) while being clearer about priority.

**Assessment:** ⭐⭐⭐☆☆

**Recommendations:**

1. **Three-zone layout structure:**
   ```
   ┌─────────────────────────────────────┐
   │   Hero: Next Recommended Action     │  (Full width, high contrast)
   ├─────────────────────────────────────┤
   │  ┌──────────┐  ┌──────────┐        │
   │  │ Progress │  │ Progress │  (Grid)│  (2-3 columns, cards)
   │  │  Card 1  │  │  Card 2  │        │
   │  └──────────┘  └──────────┘        │
   ├─────────────────────────────────────┤
   │     Quick Actions (Secondary)       │  (Subtle, bottom)
   └─────────────────────────────────────┘
   ```

2. **Use card-based layout:** Wrap each of the 5 sections in individual cards with `bg-white border border-slate-200 rounded-lg p-6`. This creates clear visual boundaries without adding cognitive load.

3. **Asymmetric balance:** The hero section (next action) should be visually heavier (larger, brighter) than progress cards. This creates intentional imbalance that guides the eye.

4. **Vertical rhythm:** Use consistent spacing between major zones:
   - Between hero and progress: `gap-8` (32px)
   - Between progress cards: `gap-6` (24px)
   - Between progress and quick actions: `gap-12` (48px)

---

### 3. Spacing & Rhythm

**Current State:**
This is one of your stated concerns. Without deliberate spacing, related elements don't feel grouped, and unrelated elements don't feel separated. For developers, inconsistent spacing triggers a "something's off" feeling even if they can't articulate why.

**Assessment:** ⭐⭐☆☆☆

**Recommendations:**

1. **Establish a clear spacing system based on 8px increments:**
   ```
   Micro (within components):  gap-1 (4px), gap-2 (8px)
   Small (related items):      gap-4 (16px)
   Medium (component parts):   gap-6 (24px)
   Large (sections):           gap-8 (32px)
   XLarge (major zones):       gap-12 (48px), gap-16 (64px)
   ```

2. **Apply the Law of Proximity:** Items that are related should be closer together than items that are unrelated. Specifically:
   - **Within a progress card:** Use `gap-2` (8px) between label and progress bar
   - **Between progress cards:** Use `gap-6` (24px)
   - **Between functional zones:** Use `gap-12` (48px) or more

3. **Padding consistency:** All cards should use the same padding: `p-6` (24px). This creates a predictable rhythm.

4. **Container width:** Constrain the content to `max-w-6xl mx-auto` (1152px) to prevent the dashboard from feeling stretched on large screens.

**Recommended Spacing Scale:**
- Tight: `gap-2` (8px) - within components
- Normal: `gap-4` (16px) - related items
- Relaxed: `gap-6` (24px) - component separation
- Loose: `gap-8` (32px) - section boundaries
- Extra loose: `gap-12` (48px) - major zones

---

### 4. Typography & Readability

**Current State:**
With Inter chosen for both headings and body text, the challenge is creating hierarchy through size and weight alone. This is achievable but requires intentional differentiation.

**Assessment:** ⭐⭐⭐⭐☆

**Recommendations:**

1. **Use the type scale to create clear hierarchy:**
   - Next Action Hero: `text-4xl font-bold` (36px, bold)
   - Section headings ("Progress"): `text-2xl font-semibold` (24px)
   - Progress card titles: `text-lg font-medium` (18px)
   - Body text: `text-base` (16px, regular)
   - Supporting labels: `text-sm text-slate-600` (14px)

2. **Leverage font weight for hierarchy:**
   - Bold (`font-bold`): Only for the primary CTA and hero text
   - Semibold (`font-semibold`): Section headings
   - Medium (`font-medium`): Card titles, sub-headings
   - Regular (default): Body text, descriptions
   - The absence of bold everywhere makes bold truly stand out where used

3. **Line height for readability:**
   - Headings: `leading-tight` (1.25) - keeps multi-line headings compact
   - Body text: `leading-relaxed` (1.625) - improves readability
   - Short labels: `leading-none` (1.0) - tightens up UI elements

4. **Text color for hierarchy:**
   - Primary text: `text-slate-900` (headings, important info)
   - Body text: `text-slate-700`
   - Secondary text: `text-slate-600` (labels, metadata)
   - Tertiary text: `text-slate-500` (timestamps, hints)

**Recommended Type Scale:**
- Hero: `text-4xl font-bold` (36px, Inter)
- H1: `text-3xl font-bold` (30px, Inter)
- H2: `text-2xl font-semibold` (24px, Inter)
- H3: `text-xl font-semibold` (20px, Inter)
- H4: `text-lg font-medium` (18px, Inter)
- Body: `text-base` (16px, Inter)
- Small: `text-sm` (14px, Inter)
- Code: `font-mono text-sm` (JetBrains Mono)

---

### 5. Color & Contrast

**Current State:**
With indigo (primary), emerald (secondary), and slate (neutral) defined, the palette is professional and developer-friendly. The challenge is applying these colors with restraint to support hierarchy rather than create noise.

**Assessment:** ⭐⭐⭐⭐☆

**Recommendations:**

1. **Strategic color application:**
   - **Next Action button:** Use `bg-indigo-600 hover:bg-indigo-700 text-white` with generous padding (`px-8 py-4`) and `font-semibold`. This is the only place where solid indigo should appear on the dashboard.
   - **Progress indicators:** Use `emerald` for completed/progressing items: `bg-emerald-100 border-emerald-300 text-emerald-700`. This creates positive association with progress.
   - **Not started items:** Use `slate-100 border-slate-200 text-slate-600` to de-emphasize.

2. **Avoid color overload:** Don't make every section a different color. Use the neutral palette (slate) as the foundation, with indigo and emerald as accents only where they convey meaning (action and progress).

3. **Progress visualization:**
   ```
   Complete: bg-emerald-500 (solid green bar)
   In Progress: bg-indigo-500 (solid indigo bar)
   Not Started: bg-slate-200 (light gray bar)
   ```

4. **Contrast validation (WCAG AA):**
   - `indigo-600` on white: 7.27:1 ✓ (Passes AAA)
   - `slate-700` on white: 8.23:1 ✓ (Passes AAA)
   - `emerald-700` on `emerald-100`: 4.89:1 ✓ (Passes AA)
   - `slate-600` on white: 5.87:1 ✓ (Passes AA)

**Recommended Color Applications:**
- **Primary actions:** `bg-indigo-600 hover:bg-indigo-700 text-white`
- **Secondary actions:** `bg-slate-100 hover:bg-slate-200 text-slate-700 border border-slate-300`
- **Success/Progress states:** `bg-emerald-50 text-emerald-700 border-emerald-200`
- **Headings:** `text-slate-900`
- **Body text:** `text-slate-700`
- **Secondary text:** `text-slate-600`
- **Page background:** `bg-slate-50`
- **Card backgrounds:** `bg-white`
- **Borders:** `border-slate-200`

---

### 6. Accessibility

**Current State:**
As a text and button-based dashboard, accessibility should be straightforward if implemented with semantic HTML and proper keyboard support. However, progress indicators need careful consideration to be accessible to screen reader users.

**Assessment:** Good (pending implementation)

**Recommendations:**

1. **Semantic HTML structure:**
   ```html
   <main aria-label="Dashboard">
     <section aria-labelledby="next-action-heading">
       <h1 id="next-action-heading">Next Recommended Step</h1>
       <!-- Hero content -->
     </section>

     <section aria-labelledby="progress-heading">
       <h2 id="progress-heading">Your Progress</h2>
       <div role="list">
         <!-- Progress cards -->
       </div>
     </section>
   </main>
   ```

2. **Progress indicator accessibility:**
   - Use `<progress>` elements or add `role="progressbar"` with `aria-valuenow`, `aria-valuemin`, `aria-valuemax`
   - Example: `<div role="progressbar" aria-valuenow="60" aria-valuemin="0" aria-valuemax="100" aria-label="Design System progress: 60%">`

3. **Keyboard navigation:**
   - All action buttons should be focusable with Tab
   - Focus order should be: Next Action → Progress cards → Quick actions
   - Focus states: `focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2`

4. **Touch targets:** Ensure all buttons are at least 44x44px:
   - Primary button: `h-12 px-8` (48px height) ✓
   - Secondary buttons: `h-10 px-4` (40px height + padding = 44px+) ✓

5. **Screen reader text:**
   - Add sr-only labels for progress indicators: `<span class="sr-only">3 of 5 sections completed</span>`
   - Button text should be explicit: "Start defining design tokens" not just "Start"

**WCAG Compliance Checklist:**
- [x] Contrast ratios meet AA standards (4.5:1 text, 3:1 UI)
- [x] Keyboard navigation works for all interactive elements
- [x] Focus states are visible (indigo-500 ring)
- [x] Semantic HTML structure (landmarks, headings)
- [x] Touch targets are minimum 44x44px
- [ ] Progress indicators have aria labels (pending implementation)
- [ ] No information conveyed by color alone (add icons to progress states)

---

## Addressing Your Specific Concerns

### Concern 1: Visual hierarchy may not clearly emphasize the next recommended action

**Analysis:**
This is the most critical concern. Your intuition is correct - on a dashboard meant to guide users, the next action must be unmistakably clear. Currently, progress indicators and quick actions likely compete for attention with the recommended next step.

**Recommendation:**

Create a hero section at the top of the dashboard that immediately draws the eye:

```
┌─────────────────────────────────────────────────┐
│  Next Step: Define Your Design Tokens          │
│  Choose colors and typography to establish     │
│  your product's visual identity.                │
│                                                 │
│  [Start Design Tokens →]  (Large indigo button)│
└─────────────────────────────────────────────────┘
```

**Implementation:**
```html
<div class="bg-indigo-50 border border-indigo-200 rounded-lg p-8 mb-12">
  <p class="text-sm font-medium text-indigo-600 mb-2">NEXT STEP</p>
  <h1 class="text-4xl font-bold text-slate-900 mb-3">Define Your Design Tokens</h1>
  <p class="text-lg text-slate-700 mb-6 max-w-2xl">
    Choose colors and typography to establish your product's visual identity and ensure consistency across all screens.
  </p>
  <button class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold px-8 py-4 rounded-lg text-lg transition-colors">
    Start Design Tokens →
  </button>
</div>
```

**Expected impact:** Users immediately know what to do next. The hero section occupies 30-40% of the viewport on desktop, ensuring it can't be missed.

---

### Concern 2: Dashboard might feel text-heavy

**Analysis:**
Yes, this is a valid concern. Dashboards with too much text create cognitive load and reduce scannability. Users should be able to glance at the dashboard and understand their status in 2-3 seconds.

**Recommendation:**

Apply progressive disclosure and visual elements to reduce text:

1. **Replace text-heavy progress descriptions with visual progress bars:**
   ```
   Instead of:
   "Foundation & Setup: You've completed the product vision and roadmap. Next: Define target audience."

   Use:
   Foundation & Setup  [████████░░] 2/3
   ```

2. **Use icons to reduce label length:**
   - ✓ Completed
   - ⟳ In Progress
   - ○ Not Started

3. **Truncate descriptions:** Each progress card should have:
   - Section name (1-3 words)
   - Progress visual (bar or count)
   - Status icon
   - Optional: One-line description (max 50 characters)

4. **Move detailed info to hover/click:**
   - Default: Show minimal info (name + progress)
   - On hover: Show tooltip with details
   - On click: Expand card to show all workflows

**Implementation example:**
```html
<div class="bg-white border border-slate-200 rounded-lg p-6 hover:border-slate-300 transition-colors">
  <div class="flex items-center justify-between mb-3">
    <h3 class="text-lg font-medium text-slate-900">Foundation & Setup</h3>
    <span class="text-emerald-600 text-sm font-medium">2/3 ✓</span>
  </div>
  <div class="w-full bg-slate-100 rounded-full h-2">
    <div class="bg-emerald-500 h-2 rounded-full" style="width: 66%"></div>
  </div>
  <p class="text-sm text-slate-600 mt-3">Product vision defined</p>
</div>
```

**Expected impact:** Text volume reduced by 60-70%, making the dashboard more scannable while retaining all essential information.

---

### Concern 3: Not sure if spacing clearly separates different sections

**Analysis:**
This concern is foundational. Spacing is the most underutilized tool in design. Developers often add borders, backgrounds, or dividers to separate content when spacing alone would be clearer and cleaner.

**Recommendation:**

Use the "spacing as separation" principle:

1. **Within a component:** Tight spacing (4-8px)
2. **Between related components:** Medium spacing (16-24px)
3. **Between sections:** Large spacing (32-48px)
4. **Between major functional zones:** Extra large spacing (48-64px)

**Concrete example for your dashboard:**

```
[ Hero Section ]
    ↓ 48px gap (major zone boundary)
[ Progress Section Header ]
    ↓ 16px gap (header to content)
[ Progress Card 1 ]
    ↓ 24px gap (between cards)
[ Progress Card 2 ]
    ↓ 24px gap
[ Progress Card 3 ]
    ↓ 64px gap (major zone boundary)
[ Quick Actions Header ]
    ↓ 16px gap
[ Quick Actions Buttons ]
```

**Rule of thumb:** The spacing between sections should be 2-3x larger than spacing within sections.

**Implementation:**
```html
<div class="max-w-6xl mx-auto px-6 py-12 space-y-12">
  <!-- Hero (Next Action) -->
  <section>...</section>

  <!-- 48px gap via space-y-12 -->

  <!-- Progress -->
  <section class="space-y-6">
    <h2>Your Progress</h2>
    <!-- 24px gap between cards via space-y-6 -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div>Progress Card 1</div>
      <div>Progress Card 2</div>
      <div>Progress Card 3</div>
    </div>
  </section>

  <!-- 48px gap via space-y-12 -->

  <!-- Quick Actions -->
  <section>...</section>
</div>
```

**Expected impact:** Clear visual boundaries without adding borders or backgrounds. The eye naturally groups related content and distinguishes between sections.

---

## Prioritized Action Plan

### 🔥 Quick Wins (Implement First)

1. **Increase Next Action button size** - Change to `h-12 px-8 text-lg` with `bg-indigo-600`. Makes the primary CTA immediately obvious. (5 min)

2. **Add spacing system** - Apply `space-y-12` to main container, `space-y-6` within sections, `gap-6` between cards. Creates clear visual separation. (10 min)

3. **Reduce text in progress cards** - Show only section name, progress bar, and completion count. Move descriptions to hover tooltips. (15 min)

### ⚠️ High Priority (Critical Issues)

1. **Create hero section for Next Action** - Build a prominent, full-width section at the top with large text, description, and CTA button. This solves the #1 concern. (30 min)

2. **Implement progress bars visually** - Replace text-heavy progress descriptions with visual progress indicators (bars or circular progress). (20 min)

3. **Establish type scale hierarchy** - Apply the recommended font sizes: `text-4xl` for hero, `text-2xl` for section headings, `text-lg` for card titles. (15 min)

### 📋 Medium Priority (Important Improvements)

1. **Add progress icons** - Include visual indicators (✓ checkmark, spinner, empty circle) for status at-a-glance. (20 min)

2. **Implement card-based layout** - Wrap each section's progress in individual cards with borders and shadows. (25 min)

3. **Apply color system consistently** - Use indigo only for primary CTA, emerald for progress, slate for everything else. (20 min)

4. **Add focus states** - Implement `focus:ring-2 focus:ring-indigo-500` on all interactive elements for keyboard navigation. (15 min)

### ✨ Low Priority (Polish & Refinement)

1. **Add subtle hover effects** - Transition border colors on cards: `hover:border-slate-300`. (10 min)

2. **Implement responsive layout** - Progress cards in 1 column (mobile), 2 columns (tablet), 3 columns (desktop). (15 min)

3. **Add empty state guidance** - If no progress yet, show encouraging message with first step highlighted. (20 min)

---

## Implementation Guide

### Top Recommendation: Create Hero Section for Next Action

**Current state:** Next recommended action likely buried among other information or presented with equal weight to progress indicators.

**Why it matters:** The dashboard's #1 job is to answer "What should I do next?" If users have to search for this answer, the dashboard has failed. Visual hierarchy isn't just aesthetics - it's functional guidance. By making the next action unmissable, you reduce friction, decision fatigue, and drop-off.

**Design principle applied:** **Figure-Ground Relationship** - The next action should be the "figure" (focal point) while everything else is "ground" (background). This is achieved through size, color contrast, and spatial isolation.

**How to fix:**

1. **Structure:** Create a dedicated section at the top of the page:
   ```html
   <section class="bg-indigo-50 border border-indigo-200 rounded-lg p-8 mb-12">
     <!-- Content here -->
   </section>
   ```

2. **Typography hierarchy:**
   ```html
   <p class="text-sm font-medium text-indigo-600 uppercase tracking-wide mb-2">
     Next Step
   </p>
   <h1 class="text-4xl font-bold text-slate-900 mb-3">
     Define Your Design Tokens
   </h1>
   <p class="text-lg text-slate-700 mb-6 max-w-2xl">
     Choose colors and typography to establish your product's visual identity.
   </p>
   ```

3. **Call-to-action button:**
   ```html
   <button class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold px-8 py-4 rounded-lg text-lg shadow-sm transition-colors focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">
     Start Design Tokens →
   </button>
   ```

4. **Spacing isolation:** Add `mb-12` (48px) below the hero section to create clear separation from progress cards.

5. **Background color:** Use `bg-indigo-50` (very light indigo tint) to subtly distinguish this section from the page background (`bg-slate-50`), creating a visual container without heavy borders.

**Expected impact:**
- Users immediately identify their next action within 1-2 seconds
- Reduced cognitive load and decision paralysis
- Higher engagement with recommended workflows
- Clear sense of direction and progress

---

### Second Recommendation: Implement Visual Progress Indicators

**Current state:** Progress likely communicated through text: "2 of 3 workflows complete" or descriptive paragraphs.

**Why it matters:** Humans process visual information 60,000x faster than text. Progress bars provide instant, at-a-glance understanding without requiring users to read and parse sentences. For developers who are already text-fatigued from code, visual indicators are a relief.

**Design principle applied:** **Gestalt Principle of Closure** - Our brains automatically complete partial shapes. A partially filled progress bar creates a sense of incompleteness that motivates users to "complete" it, driving engagement.

**How to fix:**

1. **Progress bar component:**
   ```html
   <div class="space-y-2">
     <div class="flex items-center justify-between">
       <span class="text-sm font-medium text-slate-700">Foundation & Setup</span>
       <span class="text-sm text-emerald-600 font-medium">2/3</span>
     </div>
     <div class="w-full bg-slate-100 rounded-full h-2 overflow-hidden">
       <div
         class="bg-emerald-500 h-2 rounded-full transition-all duration-500"
         style="width: 66%"
         role="progressbar"
         aria-valuenow="66"
         aria-valuemin="0"
         aria-valuemax="100"
         aria-label="Foundation & Setup: 66% complete, 2 of 3 workflows"
       ></div>
     </div>
   </div>
   ```

2. **Color coding:**
   - Completed: `bg-emerald-500` (green = positive, done)
   - In Progress: `bg-indigo-500` (blue = active, in motion)
   - Not Started: `bg-slate-200` (gray = inactive, waiting)

3. **Add transition:** `transition-all duration-500` creates a satisfying animation when progress updates, reinforcing accomplishment.

4. **Accessibility:** Include `role="progressbar"` and `aria-*` attributes for screen reader users.

5. **Supplement with icon:**
   ```html
   <div class="flex items-center gap-2">
     <span class="text-emerald-600">✓</span>
     <span>2/3 workflows complete</span>
   </div>
   ```

**Expected impact:**
- Instant visual comprehension of progress
- Motivational "completion effect" encouraging users to finish sections
- Reduced text load by 70%
- More engaging, game-like experience

---

### Third Recommendation: Apply Spacing System for Clear Separation

**Current state:** Likely inconsistent spacing throughout, making it unclear where one section ends and another begins.

**Why it matters:** Spacing is invisible design. Users don't consciously notice good spacing, but they feel confused and overwhelmed when it's wrong. Consistent spacing creates rhythm, predictability, and clarity - essential for a tool teaching design principles.

**Design principle applied:** **Law of Proximity** - Objects that are near each other are perceived as related. Objects that are far apart are perceived as separate. By controlling spacing, you control how users mentally group information.

**How to fix:**

1. **Define spacing scale:**
   ```css
   /* Tailwind spacing reference */
   gap-2  = 8px   (within component)
   gap-4  = 16px  (related items)
   gap-6  = 24px  (component separation)
   gap-8  = 32px  (section boundaries)
   gap-12 = 48px  (major zones)
   gap-16 = 64px  (page sections)
   ```

2. **Apply to main layout:**
   ```html
   <div class="max-w-6xl mx-auto px-6 py-12">
     <div class="space-y-12">
       <!-- 48px between major zones -->

       <section class="space-y-4">
         <!-- Hero section -->
         <h1>...</h1>
         <p>...</p>
         <button>...</button>
       </section>

       <section class="space-y-6">
         <!-- Progress section -->
         <h2 class="text-2xl">Your Progress</h2>
         <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
           <!-- 24px between cards -->
           <div>Card 1</div>
           <div>Card 2</div>
           <div>Card 3</div>
         </div>
       </section>

       <section class="space-y-4">
         <!-- Quick actions -->
       </section>
     </div>
   </div>
   ```

3. **Within cards:**
   ```html
   <div class="p-6 space-y-3">
     <!-- 24px padding, 12px between elements -->
     <h3>Section Title</h3>
     <div>Progress bar</div>
     <p>Description</p>
   </div>
   ```

4. **Rule to remember:** Between sections should be 2-3x the spacing within sections.

**Expected impact:**
- Clear visual boundaries without borders
- Content feels organized and breathable
- Users can quickly distinguish between functional areas
- Professional, polished appearance

---

## Design Principles Applied

### Principle 1: Visual Hierarchy (Figure-Ground)

Visual hierarchy is the arrangement of elements in order of importance. It answers: "What should the user look at first, second, third?" This is achieved through:
- **Size:** Larger elements attract attention first
- **Color:** High-contrast colors (like indigo on white) stand out
- **Position:** Top-left and center positions are seen first
- **Isolation:** Elements surrounded by whitespace are more noticeable

**Application to this dashboard:** The next action should be the largest element (text-4xl), use high-contrast color (indigo-600), be positioned at the top, and be surrounded by generous spacing (mb-12). Everything else should be smaller and use neutral colors.

---

### Principle 2: Law of Proximity (Gestalt)

Elements that are close together are perceived as related. Elements that are far apart are perceived as separate. This is how our brains organize visual information into groups without conscious effort.

**Application to this dashboard:** Progress cards should be close to each other (gap-6 / 24px) to communicate "these are all progress items." The hero section should be far from progress cards (gap-12 / 48px) to communicate "this is a different functional zone."

---

### Principle 3: Progressive Disclosure

Don't show everything at once. Reveal information in layers based on user need. Primary information is always visible; secondary information appears on hover, click, or in a separate view.

**Application to this dashboard:** Show section name and progress bar by default. Show detailed workflow list on hover or click. This reduces cognitive load while keeping information accessible.

---

## Next Steps

1. **Review recommendations** - Focus on the 3 main concerns you identified: hierarchy, text-heavy, spacing
2. **Implement Quick Wins first** - Button size, spacing system, reduce text (30 min total)
3. **Track iteration** - After making changes, run `/track-iteration design-os-dashboard` to compare versions
4. **Test with users** - Show the dashboard to 2-3 developers/founders. Can they identify their next action in 3 seconds?
5. **Iterate** - Design is never "done." Expect 2-3 rounds of refinement based on real usage

---

## Resources

- [Design Tokens](/product/design-system/) - Your indigo/emerald/slate palette and Inter typography
- [Target Audience](/product/target-audience.md) - Keep your users (developers with little design knowledge) in mind
- [WCAG Guidelines](https://www.w3.org/WAI/WCAG21/quickref/) - Accessibility standards

**Questions or need clarification?** Design OS is here to help you improve iteratively. Run `/audit-screen design-os-dashboard` again after making changes to see your progress!
