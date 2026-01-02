# Export & Handoff Workflows

Packages all design decisions, tokens, and specifications into formats that can be implemented directly in code or handed off to AI coding assistants.

---

## 1. Design System Code Export Workflow

**Purpose:** Export design tokens and component patterns as production-ready code in multiple formats for direct integration.

**Steps:**
1. Read design system tokens (colors, spacing, typography)
2. Read component patterns and specifications
3. Ask which format(s) to export:
   - CSS custom properties (variables)
   - SCSS/Sass variables
   - JSON (for design tools or frameworks)
   - JavaScript/TypeScript objects
   - Tailwind CSS config
   - Style Dictionary format
4. Generate code for selected format(s)
5. Include usage examples and best practices
6. Create file structure for easy integration
7. Generate import/setup instructions
8. Add inline documentation and comments
9. Create export package

**Inputs:**
- DesignSystem and DesignToken entities
- Component patterns
- Export format preferences
- Framework/tooling preferences (React, Vue, vanilla CSS, etc.)

**Outputs:**
- `/product/export/design-system/` with code files in selected formats, usage documentation, integration guide, and examples
- Creates ExportPackage entity for design system

**Command:** `/export-design-system` (to be implemented)

---

## 2. Screen Implementation Package Workflow

**Purpose:** Export selected screens with audits, critiques, implementation specs, and content for developer handoff.

**Steps:**
1. Select screens to export (individual, multiple, or all)
2. For each screen, gather:
   - Screen context and metadata
   - Audit findings and recommendations
   - Critique with prioritized improvements
   - Design token references (which tokens to use where)
   - Content and microcopy
   - Accessibility requirements
3. Generate implementation specifications:
   - HTML structure recommendations
   - CSS/styling specifications with token references
   - Component breakdown (which components to use/build)
   - Spacing and layout details (exact values from spacing scale)
   - Typography usage (which type scale levels)
   - Color usage (which palette colors)
   - Responsive design considerations and breakpoints
4. Include before/after recommendations
5. Add accessibility checklist (WCAG requirements, ARIA attributes)
6. Create code examples and snippets
7. Generate comprehensive documentation per screen

**Inputs:**
- Selected Screen entities
- Critique entities
- DesignToken entities
- Content guidelines
- Implementation priorities

**Outputs:**
- `/product/export/screens/[screen-name]/` with implementation specs, audits, critiques, code examples, and accessibility checklist
- Creates ExportPackage entity for screens

**Command:** `/export-screens` (to be implemented)

---

## 3. Complete Handoff Package Workflow

**Purpose:** Generate full project documentation combining all sections for comprehensive handoff to developers or teams.

**Steps:**
1. Gather all project data:
   - Product vision and roadmap
   - Target audience definitions
   - Design system (tokens, components, patterns)
   - All screens (audits, critiques, specs)
   - Content guidelines (voice/tone, microcopy standards)
2. Generate master table of contents
3. Create project overview document with vision and goals
4. Include complete design system documentation
5. Include all screen implementation specs organized by section
6. Include content guidelines and writing standards
7. Create implementation priority guide (what to build first)
8. Add quick start guide for developers
9. Include troubleshooting, common pitfalls, and FAQ
10. Package everything with clear folder structure
11. Generate README with navigation

**Inputs:**
- All project entities (Project, DesignSystem, DesignTokens, Screens, Critiques, Content guidelines, Voice & Tone)
- Implementation priorities

**Outputs:**
- `/product/export/complete-handoff/` with comprehensive documentation, organized file structure, master README, implementation guide, and quick start
- Creates complete ExportPackage entity

**Command:** `/export-complete` (to be implemented)

---

## 4. AI Assistant Format Workflow

**Purpose:** Optimize any package for AI coding assistant consumption with structured prompts, clear context, and implementation guidance.

**Steps:**
1. Select package to optimize (design system, specific screen, or complete handoff)
2. Read package contents
3. Restructure for AI assistant consumption:
   - Add clear context and objectives at the top
   - Structure as implementation prompts with clear instructions
   - Include decision rationale (why these choices were made)
   - Add acceptance criteria for verification
   - Format design tokens as copy-paste ready code
   - Include examples and patterns for reference
4. Create AI-friendly file structure (single files or well-organized folders)
5. Generate starter prompts for common tasks:
   - "Implement this design system in [framework]"
   - "Build the [screen name] following these specifications"
   - "Apply these design tokens to existing components"
   - "Implement these accessibility requirements"
6. Add tips for working with AI assistants
7. Include verification checklist (how to confirm correct implementation)
8. Create optimized package with prompt templates

**Inputs:**
- Any ExportPackage entity (design system, screens, or complete)
- AI assistant target (Claude Code, GitHub Copilot, Cursor, etc.)
- Framework/technology preferences

**Outputs:**
- `/product/export/ai-assistant/[package-name]/` with AI-optimized documentation, structured prompts, implementation templates, and verification guides
- Creates AI-optimized ExportPackage entity

**Command:** `/format-for-ai` (to be implemented)

---

## Workflow Sequence

These workflows support flexible export based on what you need:

1. **Design System Code Export** - Export just the design system when you need tokens and components
2. **Screen Implementation Package** - Export specific screens when working on particular features
3. **Complete Handoff Package** - Export everything when doing a full handoff or starting implementation
4. **AI Assistant Format** - Optimize any of the above for AI coding assistant consumption

**Typical user flows:**
- **For AI-assisted development**: Complete Handoff Package → AI Assistant Format → Share with Claude Code
- **For design system first**: Design System Code Export → Implement → Screen Implementation Package → Iterate
- **For specific features**: Screen Implementation Package (selected screens) → AI Assistant Format → Implement
- **For full team handoff**: Complete Handoff Package → Share with development team

This completes the end-to-end Design OS workflow from product vision to AI-ready implementation.
