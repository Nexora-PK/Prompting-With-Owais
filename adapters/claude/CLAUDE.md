# Claude Code Integration Guide

To use the Universal Prompt Engineering skill with Claude Code:

### Option 1: Project-Level Skill
Copy `skills/nexora-prompting/SKILL.md` to `.claude/skills/nexora-prompting/SKILL.md` in your project root.

### Option 2: Append to CLAUDE.md
Add the following instruction to your project's `CLAUDE.md`:
```markdown
## Prompt Engineering & Architecture Workflow
When asked to create, architect, or optimize prompts or AI workflows:
- Consult the full specification in `skills/nexora-prompting/SKILL.md`.
- Follow the 7-phase execution lifecycle (Phase A through Phase G).
- Ground all prompt structures in the RTF, CREATE, CoT, ReAct, and Tree of Thoughts frameworks.
- Embed explicit delimiters, anti-hallucination protocols, and readiness checks.
```
