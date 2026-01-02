# Design OS Dashboard

## Screen Information

- **Type:** Dashboard
- **Status:** Imported
- **Date Added:** 2026-01-02
- **Source:** Description

## Context

### Purpose
Help users understand where they are in the Design OS process and guide them to the next logical step.

### Target Audience
Developers and founders with little to moderate design knowledge.

### User Flow
- **From:** Login
- **To:** Review progress → Choose next workflow → Continue building or auditing

### Product Section
Foundation & Setup (entry point to all sections)

## Screen Source

**Description:**

This is the main dashboard users see after logging in. It shows their current project, progress across sections (Foundation, Design System, Screens, Content, Export), and quick actions to start workflows like "Define Design Tokens" or "Audit a Screen".

**Key Elements:**
- Current project display
- Progress indicators across 5 sections:
  - Foundation & Setup
  - Design System
  - Screen Design & Audit
  - UX Writing & Content
  - Export & Handoff
- Quick action buttons for common workflows
- Next recommended step guidance

## Current Concerns

1. **Visual hierarchy** - May not clearly emphasize the next recommended action
2. **Text-heavy** - Dashboard might feel overwhelming with too much text
3. **Spacing and grouping** - Not sure if spacing clearly separates different sections

## Design Considerations for Audit

When auditing this screen, focus on:
- How clearly the "next action" stands out visually
- Balance between information density and scannability
- Whether progress indicators are intuitive
- Grouping and spacing between different functional areas
- Mobile responsiveness for on-the-go access

## Next Steps

- Run `/audit-screen design-os-dashboard` to get comprehensive design analysis
- Run `/check-consistency design-os-dashboard` to validate against design tokens (indigo/emerald/slate palette)
