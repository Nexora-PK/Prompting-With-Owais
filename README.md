# Universal Prompt Engineering & Architecture Plugin

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Compatibility](https://img.shields.io/badge/AI%20Tools-Antigravity%20|%20Claude%20|%20Cursor%20|%20ChatGPT%20|%20Cline-brightgreen.svg)](#installation--setup)

A cross-platform toolkit and skill bundle that turns any AI assistant (**Google Antigravity**, **Claude Code**, **Cursor**, **ChatGPT / Custom GPTs**, **Cline / Roo Code**, **Windsurf**, and **Open WebUI**) into an expert Prompt Engineer and AI Workflow Architect.

---

## ⚡ What This Plugin Does

- **Project Decomposition:** Breaks complex requirements, briefs, or monolithic code specs into clean, dependency-ordered **Task Maps**.
- **Methodology Selection:** Automatically maps each task to the simplest effective prompting technique:
  - *Direct / Instruction Prompting*
  - *Structured Prompting* (Role, Context, Task, Constraints, Format)
  - *Zero-Shot & Few-Shot Prompting*
  - *Chain of Thought (CoT)*
  - *ReAct Framework* (Thought-Action-Observation loop)
  - *Tree of Thoughts (ToT)* (Multi-expert divergence & critique)
  - *Directional Stimulus & Keyword Prompting*
  - *Unstructured-to-Structured Data Extraction*
  - *Code Review & Refactoring*
  - *RAG Grounded Prompting* (Source-only constraints)
- **Framework Structuring:** Applies proven prompt frameworks (**RTF**, **CREATE**) with strict delimiter isolation and anti-hallucination protocols.
- **Production-Ready Generation:** Outputs numbered, copy-ready prompt blocks with explicit placeholders and quality readiness gates.

---

## 📂 Repository Structure

```text
prompt-engineering-plugin/
├── plugin.json                              # Universal plugin manifest (Antigravity & Agent tools)
├── README.md                                # Setup & usage documentation
├── skills/
│   └── prompt-engineering/
│       └── SKILL.md                         # Core skill with YAML frontmatter
├── rules/
│   └── AGENTS.md                            # Always-on baseline prompt hygiene rules
└── adapters/
    ├── cursor/
    │   └── prompt-engineering.mdc           # Cursor IDE rule (.cursor/rules/)
    ├── claude/
    │   └── CLAUDE.md                        # Claude Code configuration guide
    └── system-prompts/
        └── custom-gpt-system-prompt.txt     # ChatGPT / Claude Projects / LibreChat instructions
```

---

## 🚀 Installation & Setup

### 1. Google Antigravity & Gemini CLI

#### Global Installation (Available across all workspaces)
Clone directly into your global plugins folder:

**Windows (PowerShell):**
```powershell
git clone https://github.com/Nexora-PK/prompt-engineering-plugin.git "$HOME\.gemini\config\plugins\prompt-engineering-kit"
```

**macOS / Linux:**
```bash
git clone https://github.com/Nexora-PK/prompt-engineering-plugin.git ~/.gemini/config/plugins/prompt-engineering-kit
```

#### Workspace-Only Installation
Run inside your project root:
```bash
mkdir -p .agents/plugins
git clone https://github.com/Nexora-PK/prompt-engineering-plugin.git .agents/plugins/prompt-engineering-kit
```

---

### 2. Claude Code (Anthropic CLI)

**Option A (Project Skill):**
```bash
mkdir -p .claude/skills/prompt-engineering
cp skills/prompt-engineering/SKILL.md .claude/skills/prompt-engineering/SKILL.md
```

**Option B (Add to CLAUDE.md):**
Add this to your project's `CLAUDE.md`:
```markdown
## Prompt Engineering & Architecture Workflow
When asked to create, architect, or optimize prompts or AI workflows:
- Consult the full specification in `skills/prompt-engineering/SKILL.md`.
- Follow the 7-phase execution lifecycle (Phase A through Phase G).
- Ground all prompt structures in RTF, CREATE, CoT, ReAct, and Tree of Thoughts frameworks.
- Embed explicit delimiters, anti-hallucination protocols, and readiness checks.
```

---

### 3. Cursor IDE

Copy the pre-configured `.mdc` rule into your project's Cursor rules directory:

```bash
mkdir -p .cursor/rules
cp adapters/cursor/prompt-engineering.mdc .cursor/rules/prompt-engineering.mdc
```

---

### 4. ChatGPT / Custom GPTs / Claude.ai Projects

- **ChatGPT Custom GPT:**
  1. In the **GPT Builder**, open the **Configure** tab.
  2. Under **Knowledge**, upload `skills/prompt-engineering/SKILL.md`.
  3. Paste the contents of `adapters/system-prompts/custom-gpt-system-prompt.txt` into the **Instructions** box.
- **Claude.ai Projects:**
  1. In your Project, click **Add Content** -> upload `skills/prompt-engineering/SKILL.md`.
  2. Set project instructions to reference the skill for prompt design and workflow architecture.

---

### 5. Cline / Roo Code / Windsurf

- **Cline / Roo Code:** Add the rules from `rules/AGENTS.md` into your `.clinerules`.
- **Windsurf:** Copy `rules/AGENTS.md` to `.windsurfrules`.

---

## 💡 Suggested Starter Prompts

Once installed, try asking your AI:
- *"Design an end-to-end prompt workflow for my project brief."*
- *"Structure and optimize this mega-prompt using RTF and CREATE frameworks."*
- *"Decompose this application spec into sequenced, anti-hallucinating prompts."*
- *"Review this raw requirements text and extract a structured task map."*

---

## 📄 License

MIT License. Free for commercial and personal use.
