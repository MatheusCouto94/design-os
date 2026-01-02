# Data Model

## Entities

### Project
Represents the user's product/app being designed, capturing product vision, target audience, and overall context.

### Section
Represents major product areas from the roadmap (Foundation & Setup, Design System, Screen Design & Audit, UX Writing & Content, Export & Handoff) that organize workflows and screens.

### Workflow
A structured, multi-step exercise or command (like product vision definition, design system creation, UI audit) that guides users through decisions and generates outputs.

### DesignSystem
A visual language for a project containing design tokens, color palettes, typography scales, and spacing rules (projects can have multiple systems for themes or iterations).

### DesignToken
Individual design values (colors, spacing values, font sizes, type scales) that make up a design system.

### Screen
Individual UI screens that users want to audit, critique, and improve (e.g., login page, dashboard, settings).

### Critique
AI-generated analysis and feedback on a specific screen, with recommendations for improvements.

### ExportPackage
The final output bundle containing specs, tokens, documentation, and code-ready specifications for implementation.

## Relationships

- Project has many DesignSystems
- DesignSystem belongs to Project and contains many DesignTokens
- DesignToken belongs to DesignSystem
- Project has many Screens
- Screen belongs to Project and can be tagged/grouped by Section
- Screen has many Critiques
- Critique belongs to Screen (analyzes one screen, though may reference others for comparison)
- Workflow is a global template
- When a Workflow is executed, it creates outputs (such as DesignSystem, Screen, or Critique) tied to a specific Project
- Section groups related Workflows conceptually
- Project has many ExportPackages
- ExportPackage belongs to Project and bundles DesignSystems, Screens, Critiques, and documentation
