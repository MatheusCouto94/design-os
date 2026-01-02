# Foundation & Setup Workflows

This section helps users define their product vision, understand their target audience, and establish the foundational design thinking before diving into specifics.

---

## 1. Product Vision Workflow

**Purpose:** Help users define their product's core vision, including what problem it solves and for whom.

**Steps:**
1. Gather initial input - Ask user to share raw notes, ideas, or thoughts about their product
2. Ask clarifying questions about the product name, core problems, target users, and solutions
3. Present a draft summary with product description, problems/solutions, and key features
4. Refine based on user feedback
5. Create `/product/product-overview.md` file

**Inputs:**
- User's raw notes and ideas
- Answers to clarifying questions about product, problems, and users

**Outputs:**
- `/product/product-overview.md` containing product name, description, problems & solutions, key features
- Creates the Project entity with vision data

**Command:** `/product-vision`

---

## 2. Target Audience Workflow

**Purpose:** Define primary and secondary user types, their context, goals, pain points, and constraints, and synthesize this into clear design implications.

**Steps:**
1. Ask user to identify their primary and secondary user types
2. For each user type, gather information about:
   - Context (where/when they use the product)
   - Goals (what they're trying to achieve)
   - Pain points (what frustrates them)
   - Constraints (technical, time, skill limitations)
3. Ask if they want to create lightweight personas (optional)
4. Synthesize design implications based on user characteristics
5. Present draft and refine
6. Create `/product/target-audience.md` file

**Inputs:**
- User type definitions (primary and secondary)
- Context, goals, pain points, constraints for each type
- Optional: persona details (name, background, scenario)

**Outputs:**
- `/product/target-audience.md` containing user types, their characteristics, and design implications
- Creates Audience entities that can be referenced by Screen critiques and UX decisions

**Command:** `/target-audience` (to be implemented)

---

## 3. Product Roadmap Workflow

**Purpose:** Break the product down into 3-5 major development sections that organize features and workflows.

**Steps:**
1. Read the product overview to understand features
2. Analyze and propose 3-5 logical sections
3. Get user approval and refine section breakdown
4. Create `/product/product-roadmap.md` file

**Inputs:**
- Product overview (from Product Vision workflow)
- User's preferences on organization and priority

**Outputs:**
- `/product/product-roadmap.md` with numbered sections and descriptions
- Creates Section entities for the product

**Command:** `/product-roadmap`

---

## Workflow Sequence

These workflows are designed to be run in order:

1. **Product Vision** - Establishes what you're building and why
2. **Target Audience** - Defines who you're building for and their needs
3. **Product Roadmap** - Organizes the product into logical development sections

Once these foundational workflows are complete, users can move on to the Design System section to define their visual language.
