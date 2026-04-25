# PRD Writing Skill

`prd-write` is a Codex/OpenSkills skill for turning product ideas, drafts, Feishu docs, screenshots, and prototypes into structured PRDs.

It is designed for product managers and builders who want a repeatable workflow:

1. Clarify requirements with Superpowers `using-superpowers` and `brainstorming`.
2. Generate a first-pass visual prototype with image2/imagegen.
3. Build or inspect an interactive HTML demo to validate real interactions.
4. Capture demo screens and optionally redraw them for cleaner PRD presentation.
5. Write the final PRD with business background, roles, permissions, process flow, requirement descriptions, analytics events, and acceptance criteria.

## What It Helps With

- Writing PRDs from rough product ideas.
- Rewriting or restructuring existing PRD drafts.
- Turning HTML prototypes into product requirements.
- Creating Feishu-ready PRDs with flowcharts and screenshots.
- Describing app, mini-program, and PC page requirements consistently.
- Keeping prototype visuals, interactions, analytics, and acceptance criteria aligned.

## Workflow

### 1. Requirement Clarification

The skill first clarifies:

- Business background and goals.
- User roles and permissions.
- Product scope and non-goals.
- Main workflow and exception paths.
- Platform type: app, mini-program, PC web, backend, or mixed.
- Compliance, money, data, audit, and operational risks.

If [Superpowers](https://github.com/obra/superpowers) is installed, the skill asks Codex to use `using-superpowers` and `brainstorming` first.

### 2. First-Pass Visual Prototype

After clarification, the skill can use image2/imagegen to generate static visual prototypes from the product description.

This step helps align page hierarchy, product feel, and workflow coverage before building an interactive demo.

### 3. Interactive HTML Demo

The skill then uses the visual prototype as the basis for an interactive HTML demo.

The HTML demo is treated as the source of truth for:

- Page inventory.
- Navigation.
- Branching.
- State transitions.
- Empty/error states.
- Required fields and backend dependencies.

### 4. PRD Screenshots

Before writing the final PRD, screenshots from the interactive demo can be redrawn with image2/imagegen for a cleaner presentation.

The redraw step must preserve the original interaction, fields, wording, page states, and information hierarchy. It should not invent new requirements.

### 5. PRD Writing

The final PRD includes:

- Requirement background and goals.
- Scope and non-goals.
- Roles and permissions.
- Business process flowchart.
- Requirement description.
- Status rules or state machine.
- Data/interface requirements when needed.
- Analytics events.
- Risk and exception handling.
- Acceptance checklist.

## Screenshot Layout Rules

For app or mini-program screens:

- Use a two-column layout.
- Left: prototype screenshot.
- Right: requirement details.

For PC pages:

- Use a vertical layout.
- Screenshot on top.
- Requirement details below.

## Installation

### Option 1: Clone Into Your Skills Directory

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/moirafe1094-Fe/prd-writing-skill.git ~/.agents/skills/prd-write
```

Restart Codex, then verify:

```bash
npx openskills read prd-write
```

### Option 2: Copy The Skill Folder

Copy this repository folder to:

```bash
~/.agents/skills/prd-write
```

or:

```bash
~/.codex/skills/prd-write
```

Then restart Codex.

## Recommended Companion Skill

Install Superpowers if you want stronger requirement clarification and design exploration:

```bash
git clone https://github.com/obra/superpowers.git ~/.codex/superpowers
mkdir -p ~/.agents/skills
ln -s ~/.codex/superpowers/skills ~/.agents/skills/superpowers
```

Restart Codex after installing.

## Repository Contents

```text
SKILL.md
agents/openai.yaml
references/prd-template.md
references/page-description-layout.md
```

## License

MIT
