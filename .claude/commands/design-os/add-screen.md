# Add Screen

You are helping the user import an existing screen into Design OS for auditing, critique, and improvement tracking. This is the first step in the Screen Auditor workflow.

## Step 1: Check Prerequisites

First, verify that the product overview exists:

Read `/product/product-overview.md` to understand what the product is.

If it doesn't exist:

"Before adding screens, you'll need to establish your product vision. Please run `/product-vision` first."

Stop here if the prerequisite is missing.

## Step 2: Explain the Process

"Let's import a screen from **[Product Name]** for design analysis.

I'll help you:
1. **Import the screen** — via screenshot, URL, or description
2. **Add context** — purpose, target audience, user flow
3. **Set up for audit** — prepare for comprehensive analysis

Once imported, you can run `/audit-screen` to get detailed feedback on hierarchy, layout, spacing, typography, colors, and accessibility.

What screen would you like to analyze?"

Wait for their response.

## Step 3: Choose Import Method

Ask how they want to provide the screen using AskUserQuestion:

"How would you like to provide this screen?"

Options:
1. **Screenshot upload** - Upload an image file (PNG, JPG, or image path)
2. **URL** - Link to a live page or staging environment
3. **Description** - Describe the screen in text (for early-stage concepts)
4. **Figma/Design file** - Link to Figma, Sketch, or other design file

Based on their choice, proceed with the appropriate method.

### Method A: Screenshot Upload

"Please provide the path to the screenshot file, or describe where it's located."

Once they provide the path, verify the file exists and read it (if it's an image, use the Read tool to view it).

"Great! I can see the screenshot. Let me analyze what's on this screen..."

### Method B: URL

"Please provide the URL of the screen you'd like to audit."

Note: We'll store the URL and the user can visit it. In a future enhancement, we could fetch and screenshot the page automatically.

"I've saved the URL. When you run `/audit-screen`, I'll reference this URL for analysis."

### Method C: Description

"Please describe the screen in as much detail as possible. Include:
- What type of screen is it? (dashboard, form, list, detail page, etc.)
- What elements are on the screen?
- What's the current layout?
- Any specific design concerns you have?"

Gather their detailed description.

### Method D: Figma/Design File

"Please provide the Figma link (or link to your design file)."

Save the link for reference.

"I've saved the design file link. When you run `/audit-screen`, I'll use this as a reference."

## Step 4: Gather Screen Context

Now collect essential context about the screen using AskUserQuestion or conversation:

Ask about:

1. **Screen name and type**
   "What would you like to call this screen? (e.g., 'Dashboard', 'Login Page', 'Invoice List')"

   "What type of screen is this?"
   - Homepage/Landing
   - Dashboard
   - List/Index view
   - Detail/Show view
   - Form/Input
   - Settings
   - Authentication (login/signup)
   - Profile
   - Other

2. **Purpose**
   "What should users accomplish on this screen? What's the primary goal?"

3. **Target audience** (if target-audience.md exists, reference it)
   Check if `/product/target-audience.md` exists. If it does, read it and ask:
   "Which user type from your target audience primarily uses this screen?"

   If it doesn't exist:
   "Who primarily uses this screen? (e.g., 'end users', 'admins', 'developers')"

4. **User flow context**
   "Where does the user come from before seeing this screen?"
   "Where do they typically go next?"

5. **Section tag** (optional, if product-roadmap.md exists)
   Check if `/product/product-roadmap.md` exists. If it does, read it and ask:
   "Which section of your product does this screen belong to?"

   Present the sections as options.

6. **Current concerns** (optional but helpful)
   "Do you have any specific design concerns about this screen? (e.g., 'layout feels cluttered', 'colors don't pop', 'hard to find the CTA')"

## Step 5: Analyze Visual Elements (if screenshot/image)

If they provided a screenshot or image, analyze what you see:

"Let me analyze the visual elements on this screen..."

Identify and document:
- Main layout structure (header, sidebar, main content, footer)
- Key UI elements (buttons, forms, cards, tables, navigation)
- Color usage (what colors are prominent)
- Typography (heading styles, body text)
- Spacing and density
- Visual hierarchy (what draws attention first)

Provide a brief summary:
"I can see this is a [type] screen with [key elements]. The layout follows a [structure] pattern with [prominent features]."

## Step 6: Create the Screen File

Create a markdown file at `/product/screens/[screen-name].md` (use kebab-case for the filename).

Use this exact format:

```markdown
# [Screen Name]

## Screen Information

- **Type:** [Screen type]
- **Status:** Imported
- **Date Added:** [Current date]
- **Source:** [Screenshot/URL/Description/Figma]

## Context

### Purpose
[What users should accomplish on this screen]

### Target Audience
[Who primarily uses this screen]

### User Flow
- **From:** [Where user comes from]
- **To:** [Where user goes next]

### Product Section
[Section this screen belongs to, if applicable]

## Screen Source

[If screenshot: Path to screenshot file]
[If URL: The URL]
[If description: The full description]
[If Figma: The Figma link]

## Visual Analysis (Initial)

[If screenshot/image was provided, include your analysis of layout, elements, colors, typography, spacing]

## Current Concerns

[Any specific concerns the user mentioned]

## Next Steps

- Run `/audit-screen [screen-name]` to get comprehensive design analysis
- Run `/check-consistency [screen-name]` to validate against design tokens (if defined)
```

## Step 7: Copy Screenshot to Product Folder (if applicable)

If they provided a screenshot file from another location, copy it to the product folder:

```bash
mkdir -p product/screens/[screen-name]
cp [source-path] product/screens/[screen-name]/screenshot.png
```

Update the markdown file to reference the copied screenshot.

## Step 8: Confirm Completion

Let the user know:

"I've imported **[Screen Name]** into Design OS:

**Screen file:** `/product/screens/[screen-name].md`
[If screenshot: **Screenshot:** `/product/screens/[screen-name]/screenshot.png`]

**Context captured:**
- Type: [Type]
- Purpose: [Purpose]
- Target audience: [Audience]
- User flow: [From] → [To]

**Next steps:**

1. **Run `/audit-screen [screen-name]`** to get comprehensive analysis covering:
   - Visual hierarchy and information architecture
   - Layout and composition
   - Spacing consistency
   - Typography usage
   - Color usage and accessibility
   - WCAG compliance

2. **Run `/check-consistency [screen-name]`** (optional) to validate against your design system tokens

3. After making improvements, **run `/track-iteration [screen-name]`** to compare versions and measure progress

You can import more screens by running `/add-screen` again."

## Important Notes

- Screen names should be descriptive and unique (use kebab-case for filenames)
- Always gather context - it's essential for meaningful audits
- The screen file format must be followed exactly for other commands to work
- Screenshots should be copied to `/product/screens/[screen-name]/` for consistency
- If design tokens don't exist yet, that's okay - audits will still provide valuable feedback
- The status field helps track which screens have been audited, improved, etc.
