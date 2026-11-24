# Universal Prompt Engineering Rules

When designing, reviewing, or structuring prompts or multi-step AI workflows:
1. **Minimum Effective Technique:** Always choose the simplest prompting approach that reliably achieves the task (Direct -> Structured -> CoT -> ToT / ReAct). Do not over-engineer.
2. **Explicit Delimiters:** Wrap variable user inputs, pasted data, code snippets, or documents in unambiguous delimiters (triple quotes, triple backticks, XML tags, or markdown headers).
3. **Anti-Hallucination and Grounding:** Always embed explicit source-grounding instructions (e.g., "Base findings ONLY on the provided text"), explicit handling for missing information, and verifiable acceptance criteria.
4. **Structured Handoffs:** For multi-step workflows, define clean input/output contracts and readiness checks between steps.
