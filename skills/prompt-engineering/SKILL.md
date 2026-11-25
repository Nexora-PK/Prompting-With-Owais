---
name: prompt-engineering
description: Universal prompt engineering and workflow architecture skill. Analyzes project briefs or task descriptions, decomposes complex requirements into dependency-ordered task maps, selects optimal prompting techniques (Direct, Structured, Few-Shot, CoT, Instruction Boundaries, ReAct, Tree of Thoughts, Directional Stimulus, Data Extraction, Code Refactoring, RAG Grounding, RTF, CREATE), and generates copy-ready prompt sequences with explicit delimiters and anti-hallucination guardrails.
author: Nexora PK / Owais Kayani (https://github.com/Nexora-PK)
license: Proprietary (All Rights Reserved - Free to install and use, no redistribution)
repository: https://github.com/Nexora-PK/prompt-engineering-plugin
---

# universal-prompt-engineering-skill.md

## 1. Skill Name and Metadata

- **Name:** Universal Prompt Engineering & Workflow Architecture Skill
- **Author & Ownership:** Copyright © 2026 Nexora PK / Owais Kayani. All Rights Reserved.
- **Repository:** https://github.com/Nexora-PK/prompt-engineering-plugin
- **License:** Proprietary (Free to download, install, and execute; unauthorized re-uploading, republishing, or redistributing on GitHub or other platforms is strictly prohibited).
- **Purpose:** Analyse a user's project, task, or input material in any reasonable format; decompose multi-part work into logical tasks; select the simplest effective prompting approach grounded in the attached *Prompt Engineering Guide / Full Course* PDF; and generate ready-to-copy, sequenced prompts with clear input/output handoffs and anti-hallucination safeguards.
- **Version:** 1.0.0
- **Cross-Platform Compatibility:** Plain, vendor-neutral Markdown. Compatible with any Large Language Model (LLM) assistant (ChatGPT, Claude, Gemini, Perplexity, open-weights models, etc.) without proprietary APIs, hidden system prompts, or special agent frameworks.
- **Activation Triggers:**
  - The user asks for a prompt, a prompt sequence, or a prompt workflow to accomplish a project or task.
  - The user provides a project brief, specification, dataset description, document, or codebase and asks how to use AI to execute it step by step.
  - The user asks to optimize, structure, or troubleshoot an existing prompt or mega-prompt using structured prompt engineering principles.
- **When Not to Activate:**
  - The user wants a direct, immediate answer to a simple question (e.g., "What is the capital of India?") rather than a prompt or workflow design.
  - The user explicitly instructs you to execute a single self-contained task immediately without designing prompts first.
- **Required Inputs:**
  - A project goal, task description, or source material (text, document, code, data, requirements, or rough idea). If key details are missing, the skill will proceed with explicitly labelled assumptions or ask at most 1–3 essential clarifying questions.

---

## 2. Core Operating Principles

1. **Source-Grounding:**
   - All prompt types, techniques, frameworks, and components selected by this skill must be grounded in the primary reference PDF (*Master Prompt Engineering / Prompt Engineering Full Course*).
   - Preserve the PDF's exact terminology and distinctions. Never invent techniques or attribute external frameworks to the PDF.
   - Any operational advice added for practical workflow execution that is not explicitly stated in the PDF must be clearly labelled as `[General operational guidance — not stated in the PDF]`.

2. **Task-First Selection:**
   - Understand the requested outcome, inputs, constraints, and dependencies *before* choosing a prompting approach or writing prompts.
   - Match the prompting method to the actual demands of each task (e.g., data formatting vs. multi-step reasoning vs. creative ideation).

3. **Minimum Effective Technique:**
   - Prefer the simplest prompting approach that reliably achieves the task.
   - If a simple Direct Prompt or basic Structured Prompt suffices, do not force complex reasoning techniques like Tree of Thoughts or ReAct.
   - Never use every technique in the library merely because it exists.

4. **No Forced Frameworks:**
   - Prompt types, prompting techniques, and prompting frameworks are distinct categories. A task does not require an item from every category.
   - Use RTF or CREATE frameworks only when their specific structural components add clarity to the task. Mark categories as `"Not needed"` whenever they add no real value.

5. **Uncertainty and Anti-Hallucination Safeguards:**
   - Prompt engineering reduces errors and "hallucinations" (the AI fabricating facts or guessing intent), but **cannot eliminate them entirely**.
   - Never claim to have inspected files, URLs, databases, or code unless they were actually provided and read in the current session.
   - Explicitly separate facts (from user input/source text) from assumptions.
   - Build source-grounding rules (e.g., *"Based ONLY on the provided notes..."*), delimiters, and verification checks directly into generated prompts.

---

## 3. Prompt Engineering Knowledge Library

*All items below are extracted directly from the reference PDF. Each entry distinguishes its category, source coverage status, definition, usage criteria, and source pattern/example.*

### A. Prompt Types

#### 1. Direct Prompting (also referred to on p. 49 as Instruction Prompting)
- **Category:** Prompt Type
- **Source Coverage:** Explained in the PDF (p. 49). *(Note: The PDF uses "Instruction Prompting" in two ways: on p. 49 as a synonym for Direct Prompting, and on p. 56 as a 3-part boundary framework. This skill preserves both distinct meanings).*
- **Source-Supported Definition:** Giving the AI a straightforward, short, one-line, general task without extra context or detail.
- **When to Use:** Very simple, factual, or unambiguous tasks where extra context is unnecessary.
- **When Not to Use:** Complex, nuanced, or format-sensitive tasks where the AI would have to "guess" the desired length, audience, or tone.
- **PDF Example (p. 49):**
  - Good fit: `"What is the capital of India?"`
  - Poor fit (too vague): `"Write a blog post about coffee."` (The AI does not know the length, target audience, or tone).

#### 2. Structured Prompting
- **Category:** Prompt Type
- **Source Coverage:** Explained in the PDF (pp. 2, 50).
- **Source-Supported Definition:** Providing a structured set of instructions rather than a single sentence, guiding the LLM using five core components: **Role (Persona)**, **Context (Background)**, **Task (Action)**, **Constraints (Negative Constraints)**, and **Format (Output Structure)**.
- **When to Use:** Professional, multi-parameter tasks where accuracy, specific tone, clear boundaries, and structured outputs are required.
- **When Not to Use:** Trivial one-line lookups where full structural scaffolding adds unnecessary overhead.
- **PDF Example (p. 50):**
  - **Role:** `"Act as a Senior Content Marketer with 10 years of experience."`
  - **Context:** `"I am launching a new organic coffee brand for health-conscious Gen-Z."`
  - **Task:** `"Write an engaging blog post title and a 300-word intro."`
  - **Constraints:** `"Avoid using jargon like 'best-in-class'. Don't mention caffeine side effects."`
  - **Format:** `"Output should be in Markdown format with a catchy H1 header."`

---

### B. Prompting Techniques

#### 1. Zero-Shot Prompting ("The Direct Order")
- **Category:** Prompting Technique
- **Source Coverage:** Explained in the PDF (pp. 2, 53).
- **Source-Supported Definition:** Giving the AI an instruction without providing any prior examples ("shots"), relying on the model's pre-trained knowledge to generate the response.
- **When to Use:** Standard classification, summarization, drafting, or analysis tasks where the model already understands the expected output convention.
- **When Not to Use:** When Zero-Shot fails to produce a very specific, nuanced style or strict custom data schema (such as a custom JSON label mapping).
- **PDF Example (p. 53 — Sentiment Analysis):**
  - **Prompt:** `"Classify the sentiment of this review: 'The battery life of this laptop is amazing but the screen is a bit dull.'"`
  - **Output:** `"Sentiment: Mixed/Neutral"`

#### 2. Few-Shot Prompting ("The Pattern Maker")
- **Category:** Prompting Technique
- **Source Coverage:** Explained in the PDF (pp. 2, 43, 54).
- **Source-Supported Definition:** Providing the AI with 2 to 5 examples ("shots") of desired input-output pairs so the model can match the pattern, style, or specific format. (Page 2 specifies 3–5 examples; pages 43 and 54 specify 2–3 examples).
- **When to Use:** When Zero-Shot fails, especially when you need the output in a strict, specific format (e.g., custom JSON) or a nuanced writing style.
- **When Not to Use:** When no reliable examples are available, or when a simple format constraint in a Zero-Shot prompt already works reliably.
- **PDF Example (p. 54 — Formatting Customer Feedback into JSON):**
  - **Prompt:**
    `Example 1: "I loved the pizza!" -> {"sentiment": "positive", "label": 1}`
    `Example 2: "The delivery was late." -> {"sentiment": "negative", "label": 0}`
    `Example 3: "The food was okay." ->`
  - **Output:** `{"sentiment": "neutral", "label": 0.5}`

#### 3. Chain of Thought (CoT) ("The Logical Thinker")
- **Category:** Prompting Technique
- **Source Coverage:** Explained in the PDF (pp. 3, 55).
- **Source-Supported Definition:** Asking the model to `"Think step-by-step"` before giving a final answer. This forces the model to process logic linearly rather than jumping straight to a conclusion, reducing errors and hallucinations in multi-step problems.
- **When to Use:** Complex logic, math, coding logic, or strategy tasks where hasty answers frequently result in reasoning errors.
- **When Not to Use:** Simple factual recall or basic text formatting where step-by-step reasoning adds unnecessary tokens without improving accuracy.
- **PDF Example (p. 55 — Math/Logic Problem):**
  - **Prompt:** `"A farmer has 15 sheep. All but 8 die. How many are left? Let's think step by step."`
  - **Logic & Output:** `1. Total sheep = 15. 2. "All but 8 die" means only 8 survive and the rest died. 3. Therefore, 8 remain. Final Answer: 8`

#### 4. Instruction Prompting ("The Framework" / Boundaries Method)
- **Category:** Prompting Technique
- **Source Coverage:** Explained in the PDF (p. 56).
- **Source-Supported Definition:** Binding the AI within clear boundaries ("Deewar") rather than only stating a task, using three specific elements: **Persona (Role)**, **Constraints (Limit)**, and **Specific Instruction**.
- **When to Use:** Tasks requiring strict guardrails—such as code length/library restrictions, target reading-level explanations, or sensitive professional communications.
- **When Not to Use:** Open-ended brainstorming where strict boundaries would overly restrict useful exploration.
- **PDF Example (p. 56 — Professional Rejection Email):**
  - **Prompt:** `"Act as a Polite HR Manager. Write a rejection email for a candidate who cleared the interview but we can't hire due to budget cuts. Mention that we will keep their CV for future. Constraint: Keep it empathetic and don't mention the exact budget amount."`

#### 5. ReAct Framework (Reason + Act)
- **Category:** Prompting Technique / Framework *(Classified in PDF Module 3 as an Advanced Prompt Engineering Framework, used as an operational prompting technique)*
- **Source Coverage:** Explained in the PDF (pp. 57, 62).
- **Source-Supported Definition:** Operating in an iterative **Thought → Action → Observation** loop. The AI first formulates a **Thought** (what it needs to find), performs an **Action** (such as searching for specific data), reviews the **Observation** (summarizing what was found), and repeats until it can deliver a final recommendation or answer.
- **Trigger Phrase (p. 62):** `"Thought, Action, Observation loop"`
- **When to Use:** Logical execution and research tasks—especially when using an AI with web browsing, search, or external data lookup capabilities (or simulated multi-step investigation across supplied data).
- **When Not to Use:** Static, self-contained writing or simple transformation tasks where no external lookup, action, or iterative observation loop exists.
- **PDF Example (p. 57 — Market Trend Research):**
  - **Prompt:** `"Solve the following task using a Thought-Action-Observation loop. Task: Analyze the current stock performance of NVIDIA compared to its competitors in the last 7 days. Instructions: > 1. Start with a 'Thought' (What do you need to find?). 2. Perform an 'Action' (Search for specific data). 3. Provide an 'Observation' (Summarize what you found). 4. Repeat until you can provide a final 'Recommendation' for a short-term investor."`

#### 6. Tree of Thoughts (ToT)
- **Category:** Prompting Technique / Framework *(Module 3 Advanced Framework)*
- **Source Coverage:** Explained in the PDF (pp. 58, 62).
- **Source-Supported Definition:** An extension of Chain of Thought where, instead of thinking in a single linear line, the AI explores 3–4 distinct ideas or paths ("branches") simultaneously, critiques and evaluates their risks and costs, discards the weakest options, and combines the best elements into a single optimized master plan.
- **Trigger Phrase (p. 62):** `"Imagine 3 experts brainstorming..."`
- **When to Use:** Strategic planning, architectural design, or problem-solving under constraints where comparing multiple distinct alternatives is required before choosing an approach.
- **When Not to Use:** Routine, deterministic tasks where a single known procedure exists.
- **PDF Example (p. 58 — Strategy Comparison):**
  - **Prompt:** `"Imagine three different experts are brainstorming a solution to this problem: 'How can a small local bakery increase its sales by 50% in 3 months with a budget of only $500?' Step 1: Each expert will propose one unique 'thought' or strategy. Step 2: They will critique each other's ideas, identifying risks and costs. Step 3: Based on the critique, they will discard the weakest ideas and combine the best elements into a single, optimized master plan. Give me the final optimized master plan."`

#### 7. Directional Stimulus Prompting (Hint-Based Prompting)
- **Category:** Prompting Technique / Framework *(Module 3 Advanced Framework)*
- **Source Coverage:** Explained in the PDF (pp. 59, 62).
- **Source-Supported Definition:** Providing the main instruction alongside explicit "Keywords", "Stimulus", or "Direction" hints that guide the AI to focus specifically on those themes or dimensions.
- **Trigger Phrase (p. 62):** `"Focus specifically on these keywords..."`
- **When to Use:** Summarization, extraction, or targeted analysis where the output must concentrate on specific themes, priorities, or business dimensions rather than producing a generic overview.
- **When Not to Use:** When you need an unbiased, comprehensive summary of *all* topics in a document without pre-filtering.
- **PDF Example (p. 59 — Targeted Summarization):**
  - **Prompt:** `"Summarize the following article about Renewable Energy. Stimulus/Keywords to focus on: 'Government Subsidies', 'Solar Panel Efficiency', and 'Employment Opportunities'. Article: [Paste your text here]"`

#### 8. Data Extraction: Unstructured to Structured
- **Category:** Domain-Specific Prompting Technique (Module 4)
- **Source Coverage:** Explained in the PDF (p. 63).
- **Source-Supported Definition:** Using a targeted role, explicit field list, and strict output format (such as CSV/Excel or a valid JSON array of objects) to convert messy, unstructured text (emails, meeting notes, receipts, bios) into clean structured data.
- **When to Use:** Parsing messy text into database-ready JSON, tables, or spreadsheets.
- **When Not to Use:** Freeform narrative writing.
- **PDF Example (p. 63 — HR Candidate Bio Extraction):**
  - **Prompt:** `"Act as a Data Processing Expert. Extract the following information from the provided text: Name, Years of Experience, Current Role, and Primary Skills. Format the output as a valid JSON array of objects. Text: [Paste Candidate Bios here]"`

#### 9. Prompting for Coding: Code Review & Refactoring
- **Category:** Domain-Specific Prompting Technique (Modules 1 & 4)
- **Source Coverage:** Explained in the PDF (pp. 51, 64).
- **Source-Supported Definition:** Guiding the AI to review code for security vulnerabilities and logical errors (p. 51) or to **refactor** working code (cleaning and optimizing the code structure—such as replacing nested `if-else` blocks with a `switch` statement or Lookup Object—while strictly maintaining the original functionality) (p. 64).
- **When to Use:** Debugging, security auditing, improving code readability/efficiency, or explaining fixes with inline comments.
- **When Not to Use:** Non-technical tasks.
- **PDF Examples:**
  - **Security & Logic Review (p. 51):** `"Act as a Senior Python Developer. Review the following code for a 'Log-in Logic'. Identify potential security vulnerabilities and logical errors. Provide the corrected code with comments explaining each fix."`
  - **Code Refactoring (p. 64):** `"I have a working JavaScript function that uses multiple nested if-else statements. It is hard to read. Refactor this code using a switch statement or a 'Lookup Object' to make it cleaner and more efficient. Maintain the same functionality. Code: [Paste your code here]"`

#### 10. RAG (Retrieval-Augmented Generation) Grounded Prompting
- **Category:** Domain-Specific Prompting Technique / Architecture (Module 4)
- **Source Coverage:** Explained in the PDF (pp. 65–66).
- **Source-Supported Definition:** Providing the AI with a "Reference Book" (retrieved paragraphs from a Vector Database, PDF, or pasted notes) as context and instructing it to answer questions **based ONLY on the provided text** to prevent fabrications about internal policies, private notes, or recent events.
- **When to Use:** Answering questions, extracting key takeaways, formulas, dates, or summaries strictly from user-supplied documents, lecture notes, SOPs, or knowledge bases.
- **When Not to Use:** Creative ideation where the model is expected to invent new concepts outside a reference text.
- **PDF Example (p. 66 — Grounded Lecture Notes Analysis):**
  - **Prompt:**
    `Role: Act as an Academic Analyst and Study Partner.`
    `Task: Review the "LECTURE NOTES" provided below and identify the most critical information.`
    `Guidelines:`
    `- Based ONLY on the provided notes, extract the most important data, key concepts, and core takeaways.`
    `- Highlight any specific formulas, dates, or terms that are emphasized in the text.`
    `- If there are mentions of "Exam-specific" topics or "Important" points by the professor, list them separately.`
    `- Keep the summary concise and structured using bullet points for better readability.`
    `LECTURE NOTES: [Paste your notes here]`
    `QUESTION: "Based on the content, what is the most important data and key information from the lectures I have provided?"`

---

### C. Prompt Engineering Frameworks

#### 1. The RTF Framework (Role, Task, Format)
- **Category:** Prompt Engineering Framework
- **Source Coverage:** Explained in the PDF (p. 3).
- **Source-Supported Definition:** described as "the simplest professional framework for quick results," consisting of three elements:
  - **Role:** Who the AI is acting as.
  - **Task:** What specific action the AI must perform.
  - **Format:** How the output must be structured.
- **When to Use:** Fast, well-defined single tasks that need professional framing and a clean output format without heavy constraints or examples.
- **When Not to Use:** Complex multi-constraint tasks that require few-shot examples, negative constraints, or interactive clarification loops.
- **PDF Example (p. 3):**
  - **Role:** `"You are an expert career coach."`
  - **Task:** `"Review this resume for a software engineering role."`
  - **Format:** `"Provide feedback in a bulleted list categorized by 'Strengths' and 'Improvements'."`

#### 2. The CREATE Framework
- **Category:** Prompt Engineering Framework
- **Source Coverage:** Explained in the PDF (p. 3).
- **Source-Supported Definition:** A comprehensive 6-part framework designed "for more complex projects":
  - **C — Character:** Define the persona.
  - **R — Request:** State the specific task.
  - **E — Examples:** Provide a reference point.
  - **A — Adjustments:** Add constraints (e.g., `"Use a professional tone"`).
  - **T — Type of Output:** Specify the file type or layout.
  - **E — Extras:** Anything else (e.g., `"Ask me clarifying questions before starting"`).
- **When to Use:** Complex tasks or project phases that benefit from combining persona, clear instructions, reference examples, tone/constraint adjustments, layout specifications, and meta-instructions (like asking clarifying questions).
- **When Not to Use:** Simple tasks where examples (`E`) or extras (`E`) are unnecessary.

---

### D. Supporting Prompt Components and Practices

1. **The 5 Core Components of a Perfect Prompt (pp. 2, 50):**
   - **Role/Persona:** Telling the AI who it is (e.g., `"Act as a senior data scientist"`).
   - **Context:** Providing the background or "the why" behind the request.
   - **Task:** A clear, verb-driven instruction (e.g., `"Summarize"`, `"Calculate"`, `"Draft"`).
   - **Constraints:** What the AI *should not* do (e.g., `"Do not use jargon"`, `"Limit to 200 words"`).
   - **Output Format:** Specifying the structure (e.g., Markdown table, JSON, bullet points).

2. **Rule #1: Be Specific and Explicit (p. 2):**
   - Vague prompts lead to vague results. Providing explicit parameters (word count, genre, setting, plot/objective) reduces the need for the model to guess intent or hallucinate.

3. **Rule #2: Use Delimiters (p. 2):**
   - Clearly separate instructions from the data to be processed using:
     - Triple quotes: `"""`
     - Triple backticks: ```` ``` ````
     - XML-style tags: `<text></text>`
     - Markdown headers: `###`
     - Dashes: `---`

4. **Iterative Prompt Development / Iterative Refinement (pp. 3, 60–62):**
   - **Definition:** A systematic process (`Draft → Test → Analyze → Refine → Repeat`) used to tune a prompt from a vague initial version to a production-quality prompt by refining the persona, evaluation criteria, constraints, and numbered output format (demonstrated on p. 61 across Iteration 1, Iteration 2, and Iteration 3 of a Resume Reviewer prompt).
   - **Trigger Concept (p. 62):** `"Refine the persona and constraints"` to reach production quality.

5. **Token & Context Window Awareness (pp. 44–48):**
   - AI processes text as **tokens** (words, subwords, characters).
   - Every model has a **Context Window** ("Memory Limit" / Blackboard Analogy, p. 47): if a conversation or document exceeds the token limit (e.g., passing 10,000 tokens into an 8,000-token limit), the earliest tokens/instructions at the top of the "blackboard" are forgotten.
   - **Practical Implication:** Keep critical instructions close to the active task or re-state key constraints in multi-turn workflows so they are not lost as the context fills up.

6. **Domain Decomposition & Two-Layer AI Architecture Patterns (pp. 3–37 — Practical Examples in PDF):**
   - **Multi-Module Application Decomposition (pp. 3–30):** Large application prompts (FinTech, Social Media, Travel, Food Delivery, Entertainment, Business/Productivity, Real Estate, Logistics, AI-First, Government, Gaming) are broken down into 10–16 distinct functional modules covering: *User Roles & Permissions, Onboarding/Auth/KYC, Core Domain Workflows, Partner/Admin Dashboards, AI Intelligence Layer (with explainable AI and human-in-the-loop controls), Notifications, Support/Dispute Resolution, Security/Privacy/Compliance, Scalability/Performance/UX, and Future-Ready Modular Architecture*.
   - **Conversational + Knowledge/Workflow Split (pp. 30–37):** Across 25 AI Assistant use cases, the PDF demonstrates splitting AI systems into two logical responsibilities:
     1. **Conversational / Reasoning Layer** (illustrated with Gemini 3.0): Natural language understanding, asking follow-up questions, explaining concepts, empathetic dialogue, and intent interpretation.
     2. **Knowledge / State / Pipeline Layer** (illustrated with Notebook LM): Document ingestion, indexing, data cleaning, storing user history/context, running iterative exercises/simulations, and generating structured artifacts.

---

## 4. Project Analysis Workflow

Whenever this skill is activated, execute **Phases A through G** in order.

### Phase A — Understand the Request
1. **Identify the Goal & Final Deliverable:** Determine what the user ultimately wants to build, write, analyse, or solve.
2. **Extract Context Parameters:** Identify the target audience, platform/environment, available tools, input materials, constraints, timeline, and quality criteria if supplied.
3. **Separate Facts from Assumptions:** List explicit requirements stated by the user separately from inferred assumptions.
4. **Identify Material Gaps:** Determine if missing information would fundamentally change the prompt strategy.
5. **Clarify or Proceed:**
   - If the request is too ambiguous to design a reliable workflow, ask **at most 1–3 focused clarifying questions**.
   - If the work can proceed safely with reasonable defaults, state the **Labelled Assumptions** clearly and proceed immediately without interrogating the user.

### Phase B — Inspect the Project Material
1. **Identify Input Formats:** Note whether the user supplied text, documents, schemas, code snippets, spreadsheets, or a high-level brief.
2. **Inspect Actual Content:** Read the supplied material directly. Never guess contents from filenames or titles.
3. **Contextual Inspection for Long Material:** For large inputs, examine the relevant sections and surrounding context to identify hidden dependencies.
4. **Software / Code Specifics:** Distinguish existing behaviour, requested changes, technical constraints, and acceptance criteria.
5. **Document / Dataset Specifics:** Identify structure, key fields, missing values, and available evidence.
6. **Disclose Limitations:** Explicitly state any tool, file, execution, or browsing limitations that affect what could be inspected.

### Phase C — Decompose the Work
Create a structured **Task Map**. Break the project into distinct tasks only where separate reasoning, distinct inputs/outputs, or quality checkpoints make decomposition useful. Do not create artificial micro-tasks for simple requests.

For each task, define:
- **Task ID & Name** (e.g., `Task 1: Requirements Extraction & Role Matrix`)
- **Desired Result**
- **Required Inputs**
- **Expected Output / Deliverable**
- **Dependencies** (which Task IDs must finish first, or `None`)
- **Constraints & Acceptance Criteria**
- **Execution Mode:** `Independent (Parallelizable)`, `Sequential`, or `Iterative`

### Phase D — Choose the Prompting Strategy Task by Task
For every task in the Task Map, evaluate the Knowledge Library (Section 3) and select the simplest effective combination:
- **Selected Prompt Type:** `Direct Prompting`, `Structured Prompting`, or `Not needed`
- **Selected Prompting Technique:** `Zero-Shot`, `Few-Shot`, `Chain of Thought (CoT)`, `Instruction Prompting (Boundaries)`, `ReAct`, `Tree of Thoughts (ToT)`, `Directional Stimulus`, `Data Extraction (Unstructured to Structured)`, `Code Review/Refactoring`, `RAG Grounded Prompting`, or `Not needed`
- **Selected Framework:** `RTF`, `CREATE`, or `Not needed`
- **Supporting Prompt Components:** Select only relevant elements (`Role/Persona`, `Context`, `Task`, `Constraints`, `Output Format`, `Examples`, `Delimiters`, `Iterative Refinement loop`).
- **Justification:** Briefly explain *why* this combination fits the specific task.
- **Rejected Alternatives (Optional):** Note methods considered but rejected only when useful to prevent over-engineering (e.g., *"Rejected ToT because the data extraction schema is fixed and needs no multi-path brainstorming"*).

### Phase E — Design the Prompt Sequence
1. **Order by Dependency:** Sequence prompts according to data and logic dependencies, never by the order techniques appear in the PDF.
2. **Step Metadata:** For every prompt step, specify:
   - **Step Number & Descriptive Name**
   - **When to Run It** (preconditions)
   - **Input to Provide** (raw source material or exact output from a prior step)
   - **Expected AI Output**
   - **Readiness Gate** (how the user checks if the output is ready to pass to the next step)
   - **Execution Frequency:** `Run once`, `Repeat per item/module`, or `Conditional (run only if X occurs)`

### Phase F — Write the Ready-to-Use Prompts
Generate self-contained, copy-ready prompts in clean code blocks.
- Incorporate all known project details directly into the prompt so the user does not have to rewrite instructions.
- Use conspicuous uppercase placeholders delimited clearly (e.g., `""" [PASTE SOURCE TEXT HERE] """` or `<input_data>[PASTE OUTPUT FROM STEP 1 HERE]</input_data>`) for inputs the user must insert at runtime.
- Include only the sections that serve the task (Role, Context, Task, Input with Delimiters, Constraints, Process/Steps, Output Format, Verification/Uncertainty Handling).

### Phase G — Quality-Control the Workflow
Before returning the response, verify all items in the **Pre-Delivery QC Checklist**:
- [ ] Every generated prompt maps 1:1 to a real task in the Task Map.
- [ ] Every selected prompt type, technique, and framework is accurately grounded in the PDF (or explicitly marked as `[General operational guidance — not stated in the PDF]`).
- [ ] No technique or framework is included merely for decoration.
- [ ] All prompts use clear delimiters for user inputs and specify exact output formats.
- [ ] Handoffs between steps explicitly tell the user what output to copy and paste into the next step.
- [ ] Assumptions and tool/access limitations are transparently stated.
- [ ] Anti-hallucination instructions (e.g., grounding in source text, flagging missing info instead of guessing) are embedded inside the generated prompts.

---

## 5. Method Selection Decision Guide

Use this decision table to map task characteristics to the simplest effective method from the PDF. Remember that **"Not needed"** is always a valid choice for any category, and no method guarantees better results unless matched properly to the task.

| Task Characteristics & Goal | Recommended Prompt Type | Recommended Technique(s) | Recommended Framework | Key Supporting Components |
| :--- | :--- | :--- | :--- | :--- |
| **1. Simple factual lookup or one-step question** with one obvious answer | **Direct Prompting** (p. 49) | **Zero-Shot** (p. 53) | *Not needed* | Clear verb-driven Task |
| **2. Quick professional review, summary, or draft** with a standard layout | **Structured Prompting** (p. 50) | **Zero-Shot** (p. 53) | **RTF** (Role, Task, Format) (p. 3) | Role, Task, Output Format |
| **3. Strict boundary task** (e.g., sensitive HR email, code line/library limits, ELI5 explanation) | **Structured Prompting** (p. 50) | **Instruction Prompting (Boundaries)** (p. 56) | *Not needed* (or **RTF**) | Persona, Strict Constraints (Limits), Specific Instruction |
| **4. Converting messy text into a strict custom format/schema** (e.g., custom JSON labels or nuanced style) | **Structured Prompting** (p. 50) | **Few-Shot Prompting** (2–5 examples) (pp. 2, 54) + **Data Extraction** (p. 63) | **CREATE** (if complex) or *Not needed* | Examples (Shots), Delimiters, Explicit JSON/Table Output Format |
| **5. Complex math, multi-step logic, debugging, or linear deduction** | **Structured Prompting** (p. 50) | **Chain of Thought (CoT)** (`"Think step-by-step"`) (pp. 3, 55) | *Not needed* (or **RTF**) | Step-by-step reasoning instruction, Constraints |
| **6. Comparing multiple strategies, architectures, or creative solutions under constraints** | **Structured Prompting** (p. 50) | **Tree of Thoughts (ToT)** (`"Imagine 3 experts brainstorming..."`) (pp. 58, 62) | *Not needed* | Multi-expert proposal → mutual critique → combined master plan |
| **7. Targeted summarization or analysis focusing on specific priorities/themes** | **Structured Prompting** (p. 50) | **Directional Stimulus** (`"Focus specifically on these keywords..."`) (pp. 59, 62) | **RTF** or *Not needed* | Stimulus/Keywords list, Delimiters around source text |
| **8. Iterative research or investigation requiring data lookup / tool actions** | **Structured Prompting** (p. 50) | **ReAct Framework** (`Thought → Action → Observation loop`) (pp. 57, 62) | *Not needed* | Loop instructions, verification criteria |
| **9. Answering questions or extracting facts strictly from private notes/PDFs/policies** | **Structured Prompting** (p. 50) | **RAG Grounded Prompting** (`"Based ONLY on the provided notes..."`) (pp. 65–66) | *Not needed* | Delimiters, Strict source-only constraint, Bullet/Table format |
| **10. Auditing code for bugs/security or refactoring messy code without changing behaviour** | **Structured Prompting** (p. 50) | **Prompting for Coding (Review / Refactoring)** (pp. 51, 64) + **CoT** | *Not needed* | Senior Developer Persona, `"Maintain same functionality"` constraint, Delimiters |
| **11. Complex multi-requirement brief needing persona, examples, tone adjustments, and Q&A** | **Structured Prompting** (p. 50) | **Few-Shot** or **CoT** (as needed) | **CREATE** (Character, Request, Examples, Adjustments, Type of Output, Extras) (p. 3) | All 6 CREATE elements + Clarifying questions instruction |

---

## 6. Task Decomposition Rules

1. **When to Keep Work as a Single Task:**
   - The request has a single deliverable, fits easily within the model's context window and output generation limit, and does not require intermediate human review or distinct reasoning modes.
   - *Action:* Generate **1 optimized prompt** (plus an optional refinement tip). Do not invent multi-step workflows for single-step problems.

2. **When to Decompose into Multiple Tasks:**
   - **Large Multi-Module Systems:** As demonstrated in the PDF's full-scale application prompts (pp. 3–30, where apps like FinTech, Real Estate, or Logistics span 10–16 modules), a single monolithic prompt asking an AI to "Build a full-scale production-ready application" is too broad to execute in one shot. `[General operational guidance — not stated in the PDF: Decompose monolithic application briefs into sequential architectural, data/API, core module, AI layer, and security/QA tasks so each prompt produces concrete, usable specifications or code.]`
   - **Distinct Cognitive Modes:** Separate **divergent exploration** (e.g., Tree of Thoughts strategy comparison) from **convergent execution** (e.g., drafting the final specification or code) and **quality auditing** (e.g., compliance or security review).
   - **Context Window & Memory Protection (pp. 46–48):** When processing long documents or multi-stage projects, split ingestion/extraction from synthesis so early instructions are not pushed out of the model's context window ("blackboard").
   - **Two-Layer AI Assistant Workflows (pp. 30–37):** When designing AI assistants (like the PDF's Gemini 3.0 + Notebook LM examples), separate **Knowledge Ingestion & Data Structuring** tasks from **Conversational Interaction & Reasoning** tasks.

---

## 7. Prompt Construction Rules

1. **Tailor Components to the Task:**
   - Use the **5 Core Components** (Role, Context, Task, Constraints, Output Format) from p. 2 & p. 50 as your baseline checklist for Structured Prompts. Omit any component that adds no value to a simple task.

2. **Apply Frameworks Without Forcing Them:**
   - Use **RTF** (Role, Task, Format) when you need a clean, compact prompt.
   - Use **CREATE** (Character, Request, Examples, Adjustments, Type of Output, Extras) only when the task genuinely benefits from reference examples (`Examples`), tone/constraint tuning (`Adjustments`), and meta-instructions (`Extras`, such as `"Ask me clarifying questions before starting"`).

3. **Enforce Rule #1 (Be Specific and Explicit — p. 2):**
   - Replace vague verbs ("analyze", "improve", "build") with explicit parameters: exact target metrics, word/line limits, required sections, evaluation criteria (like the p. 61 Iteration 3 Resume Reviewer prompt), and target audience.

4. **Enforce Rule #2 (Use Delimiters — p. 2):**
   - Always wrap variable user inputs, pasted documents, or code blocks in explicit delimiters (`"""`, ```` ``` ````, `<text></text>`, `###`, or `---`) and refer to those delimiters in the instructions (e.g., `"Analyze the dataset delimited by triple backticks below"`).

5. **Use Examples (Rule #3 — Few-Shot Prompting — pp. 2, 54) Selectively:**
   - Include 2–5 input-output examples inside the prompt whenever the user requires a strict data schema (like custom JSON) or a specific stylistic pattern.

6. **Embed Anti-Hallucination & Grounding Rules:**
   - For document, data, or code analysis prompts, always include the RAG grounding constraint from p. 66: *"Base your output ONLY on the provided material. If required information is missing or unclear, state what is missing explicitly rather than guessing."*

---

## 8. Prompt Sequence and Handoff Rules

When a project requires multiple prompts, structure the execution sequence using these rules:

1. **Unique Step Numbering & Naming:**
   - Label every prompt clearly: `Step 1: [Descriptive Name]`, `Step 2: [Descriptive Name]`, etc.
2. **Explicit Input & Output Contracts:**
   - Before each prompt box, state:
     - **When to Run:** (e.g., *"Run first"* or *"Run after verifying Step 1's JSON output"*).
     - **Input Required:** Exactly what the user must paste into the placeholder (e.g., *"Paste your raw requirements doc into `<source_brief>`"* or *"Paste the Master Architecture Plan from Step 1 into `<architecture_context>`"*).
     - **Expected Output:** What artifact the AI will produce.
3. **Readiness Gates (Quality Checkpoints):**
   - Tell the user how to verify the output before moving to the next step (e.g., *"Verify that all 5 user roles and their permissions are listed accurately before copying this table into Step 2"*).
4. **Iteration & Conditional Execution:**
   - State clearly if a prompt is:
     - **One-off:** Run once for the project.
     - **Iterative / Loop:** Run once per module, chapter, or code file (using the Iterative Refinement cycle from p. 60: `Draft → Test → Analyze → Refine → Repeat`).
     - **Conditional:** Run only if errors, edge cases, or ambiguities are detected in a previous step.

---

## 9. Standard User-Facing Output Template

When this skill is activated to solve a user's project or task, present your response using the following clean structure:

```markdown
# AI Prompt Workflow & Execution Plan

## 1. Project Understanding & Goal
- **Final Deliverable:** [Concise statement of what the user wants to achieve]
- **Target Audience / Environment:** [Audience, stack, platform, or context]
- **Explicit Requirements:** [Bullet list of facts/constraints stated by the user]
- **Inspection & Access Notes:** [What supplied material was inspected, plus any tool/access limitations]

## 2. Assumptions & Essential Questions
- **Labelled Assumptions:** [Explicit assumptions made so work can proceed immediately]
- **Essential Clarifying Questions (if any):** [1–3 critical questions if blocked, or "None — ready to execute with the assumptions above"]

## 3. Task Breakdown (Task Map)
| Task ID & Name | Desired Result | Required Inputs | Expected Deliverable | Dependencies | Execution Mode |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Task 1:** [Name] | [Result] | [Inputs] | [Deliverable] | None | [Single / Sequential / Iterative] |
| **Task 2:** [Name] | [Result] | [Output of Task 1] | [Deliverable] | Task 1 | [Sequential / Parallel / Iterative] |

## 4. Prompting Strategy Selection
### Task 1: [Name]
- **Prompt Type:** [Direct / Structured / Not needed]
- **Prompting Technique:** [Zero-Shot / Few-Shot / CoT / Instruction Prompting / ReAct / ToT / Directional Stimulus / Data Extraction / Code Refactoring / RAG Grounded / Not needed]
- **Framework:** [RTF / CREATE / Not needed]
- **Supporting Components:** [e.g., Role, Context, Constraints, Delimiters, Output Format]
- **Why This Fits:** [1–2 sentence justification grounded in task requirements]

*(Repeat briefly for each task)*

## 5. Ordered, Ready-to-Copy Prompts

### Step 1: [Task 1 Descriptive Name]
- **When to Run:** [Precondition]
- **Execution Mode:** [Run once / Repeat per item / Conditional]
- **Input to Provide:** [What to paste into the placeholder]
- **Expected Output:** [Artifact produced]
- **Readiness Check:** [How to confirm the output is ready for Step 2]

```text
[READY-TO-COPY PROMPT WITH CLEAR DELIMITERS AND PLACEHOLDERS]
```

*(Repeat for each step in sequence)*

## 6. Handoff & Context Window Management Instructions
- [Clear instructions on how to pass outputs between steps and prevent Context Window / "Blackboard" overflow during long chats]

## 7. Final Validation & Quality Checklist
- [Checklist for the user to verify the final deliverables against accuracy, completeness, and anti-hallucination criteria]
```

---

## 10. Quality Assurance and Hallucination Controls

Every workflow generated by this skill—and every prompt inside that workflow—must enforce five operational safeguards:

1. **Evidence and Source Checks (RAG Grounding Principle — pp. 65–66):**
   - Instruct the AI to distinguish strictly between information present in the user's supplied text/data and general pre-trained knowledge.
   - When analysing user documents, notes, logs, or data, include the directive: *"Base your findings ONLY on the provided source text delimited below. Do not extrapolate or invent facts not supported by the text."*

2. **Missing-Information Handling:**
   - Instruct the AI within every generated prompt: *"If critical data, parameters, or requirements needed to complete the task are missing from the input, list the missing items under a `[Missing Information / Assumptions]` section instead of guessing."*

3. **Contradiction Checks:**
   - In multi-step workflows, instruct later prompts to flag any contradictions between earlier outputs and raw source constraints (e.g., budget limits vs. proposed features).

4. **Output Validation & Verifiable Criteria:**
   - Replace subjective quality goals ("make it good") with verifiable acceptance criteria (e.g., valid JSON schema, explicit evaluation rubrics like p. 61's Iteration 3 prompt, edge-case coverage, or preserving exact functional behaviour during code refactoring as on p. 64).

5. **Tool and Access Limitation Disclosures:**
   - Never pretend to execute code, query live databases, browse live URLs, or inspect external files if those tools are unavailable in the current environment.
   - When using **ReAct** (p. 57) in an environment *without* live search/browsing tools, instruct the AI either to pause after each `Action` so the user can supply the `Observation`, or to perform the `Action` across the user's supplied dataset.

---

## 11. Source Coverage and Gaps

To maintain strict source integrity, this section documents exactly what the attached 67-page PDF covers, what it only mentions in passing, what it demonstrates through examples, and what general operational guidance has been added separately.

### A. Fully Explained in the PDF (Included in the Core Knowledge Library)
- **Evolution & Foundations:** Discriminative AI vs. Generative AI (p. 41); Evolution from RNN (Vanishing Gradient Problem) to LSTM (Gates, sequential bottleneck) to Transformers (2017 *"Attention is All You Need"*, parallel processing, Long Context, Contextual Understanding, Few-Shot Learning) (pp. 42–43).
- **Tokens & Context Window:** Definition of tokens and tokenization (pp. 44–45); Context Window ("Memory Limit" & Blackboard Analogy) and model token limit comparison table for ChatGPT (~128K–256K), Google Gemini (~1M–2M), Anthropic Claude (~200K standard / up to ~1M enterprise), and Perplexity AI (~128K–200K) (pp. 46–48).
- **Core Prompt Components & Rules:** 5 Core Components of a Perfect Prompt (Role/Persona, Context, Task, Constraints, Output Format) (pp. 2, 50); Rule #1 Be Specific and Explicit (p. 2); Rule #2 Use Delimiters (p. 2); Rule #3 Provide Examples / Few-Shot vs. Zero-Shot (p. 2); Rule #4 Chain of Thought (CoT) (p. 3).
- **Prompt Types:** Direct Prompting (Instruction Prompting) vs. Structured Prompting (pp. 49–50).
- **Core & Advanced Prompting Techniques:** Zero-Shot Prompting (p. 53), Few-Shot Prompting (p. 54), Chain of Thought (CoT) (p. 55), Instruction Prompting ("The Framework" — Persona, Constraints, Specific Instruction) (p. 56), ReAct Framework (Reason + Act) (pp. 57, 62), Tree of Thoughts (ToT) (pp. 58, 62), Directional Stimulus Prompting (Hint-based Prompting) (pp. 59, 62).
- **Prompting Frameworks:** RTF Framework (Role, Task, Format) (p. 3) and CREATE Framework (Character, Request, Examples, Adjustments, Type of Output, Extras) (p. 3).
- **Systematic Process:** Iterative Prompt Development / Iterative Refinement (`Draft → Test → Analyze → Refine → Repeat`) with a 3-iteration Resume Reviewer progression (pp. 3, 60–62).
- **Professional Data, Coding & RAG Workflows:** Data Extraction: Unstructured to Structured (JSON/CSV) (p. 63); Prompting for Coding (Security/Logic Review on p. 51; Code Refactoring on p. 64); RAG (Retrieval-Augmented Generation — Vector Database, Retrieval, Augmentation flow and grounded lecture-notes prompt) (pp. 65–66).

### B. Demonstrated Through Practical Examples Only (Not Formally Defined as Theoretical Frameworks)
- **12 Full-Scale Domain Application Prompts (pp. 3–30):** E-Commerce, Healthcare/HealthTech, Education/EdTech, FinTech, Social Media/Community, Travel & Booking, Food & Grocery Delivery, Entertainment & Media, Business & Productivity, Real Estate, Logistics & Supply Chain, AI-First Application, Government/Utility, and Gaming applications. *(Note: The PDF numbers items 1–3 on pp. 3–4, then lists 11 unnumbered domain application prompts through p. 30, totalling 14 domain application prompts).* These demonstrate how complex systems decompose into user roles, core domain workflows, partner/admin dashboards, explainable AI layers, security/compliance, scalability, and future-ready modularity.
- **25 Gemini 3.0 + Notebook LM Assistant Prompts (pp. 30–37):** Practical prompts demonstrating a two-layer AI workflow splitting natural-language dialogue/reasoning from document/data/state management across tutoring, career coaching, BI analytics, tele-health, legal, shopping, study notes, executive assistance, ETL pipelines, creativity studio, coding mentor, inventory planning, finance, travel, wellness, market research, compliance, contracts, research papers, social listening, real estate investment, AIOps, internal Q&A, customer support, and culinary recipes.

### C. Mentioned Only in the Table of Contents (p. 40) — Not Explained in the PDF Body
The following topics appear in the *"Topics to be Covered"* slide on page 40, but **no explanatory slides or definitions appear for them in the rest of the PDF**:
1. **GIGO Principle** (Garbage In, Garbage Out)
2. **Technical Aspects & API Parameters** (e.g., temperature, top_p, max_tokens are not explained in the slides)
3. **Automating Workflows** (listed as a topic header on p. 40, though domain automation examples appear on pp. 21, 30–37)
4. **Practical Use Cases named on p. 40:** *"The Dynamic Mock Interviewer"*, *"The Legal/Contract 'Risk Finder'"*, and *"The Business Strategy Consultant"* (similar concepts appear in the pp. 30–37 assistant prompts—such as #2 Career Coach, #5 Legal Assistant, and #18 Smart Contract Assistant—but the specific Module 5 slides titled with those exact three names are omitted from the slide deck).

*Rule for this skill:* Do not attribute specific definitions or rules for the items in Section 11.C to the PDF. If any of these concepts are needed for a user's project, label them as `[General operational guidance — not stated in the PDF]`.

### D. Anomalies & Artifacts in the PDF
- Page 55 (the Chain of Thought slide) contains an stray text artifact `"show emoji of seahorse"` in the middle of the slide. This is recognized as an OCR/slide artifact and ignored.

### E. General Operational Guidance Added Beyond the PDF
The following workflow mechanics are marked as `[General operational guidance — not stated in the PDF]` to make the skill function as an end-to-end project architect:
- Breaking monolithic application prompts (like the single-block mega-prompts on pp. 3–30) into sequential, dependency-ordered prompt steps with explicit readiness gates and input/output handoffs.
- Explicit multi-step task table schemas (Task ID, Dependencies, Execution Mode) and pre-delivery quality assurance checklists.

---

## 12. Compact Quick-Start Instructions

Users can activate and run this skill in any AI assistant by pasting this short trigger instruction alongside their project details:

```text
Activate the Universal Prompt Engineering Skill.
Analyse the project brief / material below using Phases A through G:
1. Summarize my goal, deliverables, explicit constraints, and any labelled assumptions.
2. Decompose the project into a logical Task Map with clear dependencies.
3. For each task, select the simplest effective Prompt Type, Prompting Technique, and Framework from the Knowledge Library (or "Not needed") and explain why.
4. Generate numbered, self-contained, ready-to-copy prompts with delimiters, placeholders, readiness checks, and handoff instructions.

PROJECT BRIEF / MATERIAL:
"""
[PASTE YOUR PROJECT BRIEF, REQUIREMENTS, CODE, OR DOCUMENT HERE]
"""
```

---

## 13. Worked Example

This worked example demonstrates how the skill analyses a project grounded in the PDF's own domain examples (**Automated Compliance & Policy Checker / Smart Contract Review** from pp. 35, 63, 66 and **FinTech Compliance** from pp. 5–7), decomposes it into tasks, selects the appropriate PDF-grounded techniques, and produces a sequenced prompt workflow.

*(Note: The scenario details below—a fintech startup auditing its internal merchant onboarding SOP against regulatory rules—are illustrative project inputs designed to demonstrate the skill's execution on the PDF's compliance/contract use cases).*

### User Request (Illustrative Input)
> "We have an unstructured internal Standard Operating Procedure (SOP) document for Merchant Onboarding & KYC in our FinTech app, plus a set of regulatory KYC/AML compliance clauses. We want to use AI to extract our current onboarding rules into structured JSON, audit them against the regulatory clauses to flag compliance violations with severity levels, and design an remediation action plan when multiple compliance fixes compete for a small engineering budget."

---

### Skill Output for the Worked Example

#### 1. Project Understanding & Goal
- **Final Deliverable:** A 3-stage AI prompt workflow that (1) extracts structured JSON rules from an unstructured Merchant Onboarding SOP, (2) audits those rules strictly against regulatory KYC/AML clauses to identify violations and risk severity, and (3) evaluates competing remediation strategies under budget constraints to produce an optimized master compliance plan.
- **Target Audience / Environment:** FinTech compliance, legal, and engineering teams executing prompts in a standard LLM interface.
- **Explicit Requirements:**
  - Input 1: Unstructured Merchant Onboarding & KYC SOP text.
  - Input 2: Regulatory KYC/AML compliance clauses.
  - Output 1: Structured JSON extraction of current onboarding rules.
  - Output 2: Compliance gap analysis highlighting violations, risk severity levels, and remediation steps.
  - Output 3: Prioritized remediation master plan balancing competing fixes under a constrained engineering budget.
- **Inspection & Access Notes:** No actual SOP or regulatory PDF files were attached yet; prompts are built with explicit delimiters (`<sop_document>` and `<regulatory_clauses>`) ready for the user to paste the texts.

#### 2. Assumptions & Essential Questions
- **Labelled Assumptions:**
  - *Assumption 1:* Both the SOP text and the regulatory clauses fit within the chosen LLM's context window (e.g., <100,000 tokens, per p. 46).
  - *Assumption 2:* The compliance audit must be strictly grounded in the supplied regulatory text without inventing external legal statutes.
- **Essential Clarifying Questions:** None — the workflow can proceed immediately with the placeholders provided.

#### 3. Task Breakdown (Task Map)

| Task ID & Name | Desired Result | Required Inputs | Expected Deliverable | Dependencies | Execution Mode |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Task 1:** Unstructured SOP to Structured JSON Extraction | Convert messy SOP text into a clean, consistent JSON array of current onboarding & KYC controls. | Raw Merchant Onboarding SOP text | Valid JSON array of objects representing current SOP controls | None | Sequential (Run first) |
| **Task 2:** Grounded Regulatory Compliance Audit & Violation Checker | Compare extracted SOP controls against regulatory clauses to flag violations, risk severity levels, and specific remediation steps. | Output JSON from Task 1 + Regulatory KYC/AML clauses | Structured Markdown Compliance Audit Table + Violation Summary | Task 1 | Sequential (Run after Task 1) |
| **Task 3:** Multi-Path Remediation Strategy & Budget Optimization | Explore and critique competing engineering/operational remediation plans under budget constraints and synthesize one master plan. | High/Critical Violations from Task 2 + Engineering budget & timeline constraints | Optimized Master Remediation Plan | Task 2 | Sequential (Run after Task 2) |

#### 4. Prompting Strategy Selection

##### Task 1: Unstructured SOP to Structured JSON Extraction
- **Prompt Type:** Structured Prompting (p. 50)
- **Prompting Technique:** Data Extraction: Unstructured to Structured (p. 63) + Few-Shot Prompting (pp. 2, 54)
- **Framework:** Not needed *(Structured Prompting with 5 core components + Few-Shot JSON pattern is cleaner and more direct than forcing RTF or CREATE)*.
- **Supporting Components:** Role/Persona, Task, Constraints, Output Format (valid JSON array), 2 Few-Shot Examples, XML/Triple-Quote Delimiters (p. 2).
- **Why This Fits:** Converting messy narrative SOP paragraphs into a strict JSON schema benefits directly from **Data Extraction** (p. 63) paired with **Few-Shot Prompting** (p. 54) so the model follows the exact key-value pattern without guessing field names.

##### Task 2: Grounded Regulatory Compliance Audit & Violation Checker
- **Prompt Type:** Structured Prompting (p. 50)
- **Prompting Technique:** RAG Grounded Prompting (pp. 65–66) + Chain of Thought (CoT) (pp. 3, 55) + Directional Stimulus (pp. 59, 62)
- **Framework:** RTF (Role, Task, Format) (p. 3) extended with Grounding Constraints.
- **Supporting Components:** Role, Context, Task, Stimulus Keywords (from p. 5 FinTech KYC/MFA/Verification themes), Grounding Constraint (`"Based ONLY on the provided texts"`), Step-by-step evaluation (CoT), Markdown Table Format.
- **Why This Fits:** Auditing internal policies against regulations requires **RAG Grounded Prompting** (p. 66) to prevent the AI from hallucinating outside laws, **Directional Stimulus** (p. 59) to keep focus on core FinTech KYC dimensions (identity verification, bank verification, MFA, audit trails), and **Chain of Thought** (p. 55) to reason carefully before assigning risk severity levels (p. 35, Use Case #17).

##### Task 3: Multi-Path Remediation Strategy & Budget Optimization
- **Prompt Type:** Structured Prompting (p. 50)
- **Prompting Technique:** Tree of Thoughts (ToT) (pp. 58, 62)
- **Framework:** Not needed *(ToT provides its own explicit 3-step multi-expert evaluation structure)*.
- **Supporting Components:** Context, 3-Expert Brainstorming Trigger (`"Imagine three different experts..."`), Mutual Critique (risks/costs), Consolidated Master Plan Output Format.
- **Why This Fits:** Choosing how to fix compliance gaps under a tight budget involves trade-offs between engineering speed, cost, and regulatory safety. **Tree of Thoughts** (p. 58) explicitly explores 3 distinct strategies, critiques their costs and risks, discards weak ideas, and merges the best elements into one master plan.

---

#### 5. Ordered, Ready-to-Copy Prompts

##### Step 1: Extract Structured Controls from Unstructured SOP
- **When to Run:** Run first.
- **Execution Mode:** Run once (or repeat per SOP chapter if the document is very long).
- **Input to Provide:** Paste your raw Merchant Onboarding & KYC SOP text inside the `<sop_text>` tags.
- **Expected Output:** A valid JSON array of objects detailing every onboarding rule in the SOP.
- **Readiness Check:** Verify that the output is valid JSON, that every key control in your SOP is captured, and that missing details are marked `"NOT_SPECIFIED"` rather than invented.

```text
Role: Act as a Senior Data Processing Expert and FinTech Operations Analyst.

Context: We are preparing our internal Merchant Onboarding & KYC Standard Operating Procedure (SOP) for a regulatory compliance audit. First, we need to convert the unstructured SOP text into a clean, structured JSON dataset.

Task: Extract every onboarding, identity verification, bank verification, and security rule from the SOP text delimited by <sop_text></sop_text> tags below. Format the output as a valid JSON array of objects matching the exact pattern shown in the examples.

Examples (Few-Shot Pattern):
Example Input 1: "Merchants must register with a mobile number and verify via OTP before uploading business tax documents."
Example Output 1:
[
  {
    "control_id": "SOP-01",
    "category": "Authentication & Onboarding",
    "actor_role": "Merchant",
    "requirement_summary": "Register via mobile number with mandatory OTP verification prior to document upload.",
    "verification_method": "OTP",
    "failure_handling": "NOT_SPECIFIED"
  }
]

Example Input 2: "Once business documents are uploaded, the compliance team reviews them within 48 hours. If rejected, the merchant is notified via email with the reason."
Example Output 2:
[
  {
    "control_id": "SOP-02",
    "category": "KYC & Business Verification",
    "actor_role": "Compliance Team / Admin",
    "requirement_summary": "Review uploaded merchant business documents within 48 hours.",
    "verification_method": "Manual Document Review",
    "failure_handling": "Send rejection email with specific reason."
  }
]

Constraints:
- Base your extraction ONLY on the text inside <sop_text></sop_text>.
- Do NOT invent controls, timelines, or verification methods not explicitly stated in the text.
- If a field (such as failure_handling or verification_method) is not mentioned in the SOP for a specific rule, set its value to "NOT_SPECIFIED".
- Output ONLY the valid JSON array and a brief "Extraction Notes" bullet list at the end flagging any ambiguous sentences in the original SOP.

<sop_text>
[PASTE YOUR UNSTRUCTURED MERCHANT ONBOARDING & KYC SOP TEXT HERE]
</sop_text>
```

---

##### Step 2: Conduct Grounded Regulatory Compliance & Violation Audit
- **When to Run:** Run after confirming Step 1 produced a complete JSON array of your current SOP controls.
- **Execution Mode:** Run once.
- **Input to Provide:**
  1. Paste the JSON output from Step 1 inside `<extracted_sop_json></extracted_sop_json>`.
  2. Paste the target Regulatory KYC/AML Policy clauses inside `<regulatory_clauses></regulatory_clauses>`.
- **Expected Output:** A step-by-step compliance reasoning audit followed by a categorized Markdown Violation Table with Risk Severity Levels (`Critical`, `High`, `Medium`, `Low`) and specific remediation steps.
- **Readiness Check:** Confirm that every flagged violation cites both a specific `control_id` (or missing control) from Step 1 and an exact clause from `<regulatory_clauses>`.

```text
Role: Act as a Senior FinTech Compliance Auditor and Regulatory Policy Specialist.

Context: We need to audit our current Merchant Onboarding & KYC controls (extracted as JSON in Step 1) against official regulatory requirements to identify compliance violations, gaps, and risk severity levels.

Task: Compare the extracted SOP controls inside <extracted_sop_json> against the regulatory rules inside <regulatory_clauses>. Think step-by-step to evaluate compliance for every regulatory requirement before generating the final violation report.

Stimulus / Keywords to Focus On:
Focus specifically on these core FinTech compliance dimensions:
- "OTP & Multi-Factor Authentication (MFA)"
- "KYC Identity & Business Verification Workflows"
- "Bank Account & Settlement Verification"
- "Data Encryption, Consent Management & Audit Trails"
- "Dispute & Fraud Investigation Controls"

Guidelines & Constraints:
1. Based ONLY on the provided <extracted_sop_json> and <regulatory_clauses>, evaluate whether each regulatory requirement is Fully Met, Partially Met, or Violated/Missing.
2. Think step-by-step: For each regulatory clause, state the required rule, check the matching SOP control(s), identify any discrepancy, and determine the risk severity.
3. Do NOT assume a control exists if its value is "NOT_SPECIFIED" or absent from the JSON.
4. Do NOT cite external laws or regulations that are not present inside <regulatory_clauses>.

Output Format:
1. **Step-by-Step Compliance Reasoning Log:** Concise linear evaluation of each regulatory clause against the SOP JSON.
2. **Compliance Violations & Remediation Table (Markdown Table):**
   Columns: `Violation ID` | `Regulatory Clause Reference` | `Related SOP Control ID (or MISSING)` | `Gap / Violation Description` | `Risk Severity (Critical / High / Medium / Low)` | `Recommended Remediation Step`
3. **Missing Information / Clarifications Needed:** List any areas where the regulatory text or SOP JSON was too vague to make a definitive judgment.

<extracted_sop_json>
[PASTE THE JSON ARRAY OUTPUT FROM STEP 1 HERE]
</extracted_sop_json>

<regulatory_clauses>
[PASTE THE REGULATORY KYC / AML POLICY CLAUSES HERE]
</regulatory_clauses>
```

---

##### Step 3: Tree of Thoughts (ToT) Remediation Master Plan
- **When to Run:** Run after reviewing the Step 2 Compliance Violations Table.
- **Execution Mode:** Run once.
- **Input to Provide:**
  1. Paste the **Compliance Violations & Remediation Table** from Step 2 inside `<violations_table></violations_table>`.
  2. Fill in your actual budget, team size, and deadline inside `<project_constraints></project_constraints>`.
- **Expected Output:** A structured 3-expert brainstorming critique followed by a single, unified Master Remediation Plan that resolves all Critical/High violations within budget and timeline limits.
- **Readiness Check:** Verify that the final Master Plan addresses every `Critical` and `High` severity violation from Step 2 while respecting the budget and timeline in `<project_constraints>`.

```text
Imagine three different experts are brainstorming a solution to this problem:
"How can our FinTech team remediate all Critical and High compliance violations identified in our KYC/Onboarding audit within our strict budget and timeline constraints?"

The three experts are:
- Expert 1: A Regulatory Risk Officer (prioritizes zero compliance exposure and immediate audit-readiness).
- Expert 2: A Lead FinTech Systems Architect (prioritizes scalable automation, third-party KYC APIs, and clean modular architecture).
- Expert 3: A Lean Operations & Product Manager (prioritizes low-cost manual/semi-automated interim workflows to meet deadlines without overspending).

Follow these exact steps:
Step 1: Based ONLY on the violations in <violations_table> and the limits in <project_constraints>, each expert will propose one unique "thought" or remediation strategy covering how to fix the Critical and High violations.
Step 2: The experts will critique each other's strategies, explicitly identifying compliance risks, engineering costs, implementation bottlenecks, and timeline trade-offs.
Step 3: Based on the critique, they will discard the weakest ideas and combine the best elements into a single, optimized Master Remediation Plan.

Output Format:
- **Section 1: Three Expert Proposals (Step 1)**
- **Section 2: Cross-Expert Critique — Risks & Costs (Step 2)**
- **Section 3: Final Optimized Master Remediation Plan (Step 3)** — Include a phased execution schedule (Week-by-Week), estimated cost breakdown, immediate manual guardrails vs. automated product fixes, and verification sign-off criteria for each Violation ID.

<violations_table>
[PASTE THE COMPLIANCE VIOLATIONS & REMEDIATION TABLE FROM STEP 2 HERE]
</violations_table>

<project_constraints>
- Maximum Budget: [e.g., $15,000]
- Maximum Timeline before Regulatory Audit: [e.g., 6 weeks]
- Available Team: [e.g., 2 Backend Engineers, 1 Compliance Operations Analyst]
</project_constraints>
```

---

#### 6. Handoff & Context Window Management Instructions
1. **Sequential Handoff:** Run **Step 1** first. Copy *only* the validated JSON block from Step 1 and paste it into Step 2's `<extracted_sop_json>` placeholder.
2. **Preventing Context Window ("Blackboard") Overflow (p. 47):** If your original SOP document in Step 1 is very long (e.g., dozens of pages), run **Step 2** and **Step 3** in a **fresh chat session** or after clearing the raw SOP text, passing forward only the compact JSON output from Step 1 and the Violation Table from Step 2. This keeps the model's context window clean and prevents early instructions from being forgotten.
3. **Iterative Refinement (p. 60):** If any JSON field in Step 1 or severity rating in Step 2 needs tuning, apply the **Draft → Test → Analyze → Refine → Repeat** loop by tightening the constraint in that specific step before advancing.

#### 7. Final Validation & Quality Checklist
- [ ] **No Fabricated Controls:** Every item in Step 1's JSON traces directly to a paragraph in the raw SOP.
- [ ] **Strict Regulatory Grounding:** Every violation in Step 2 cites a real clause from the supplied `<regulatory_clauses>` text.
- [ ] **Complete Coverage of High-Risk Gaps:** Every `Critical` and `High` violation from Step 2 is accounted for in Step 3's Final Master Remediation Plan.
- [ ] **Constraint Compliance:** Step 3's Master Plan stays within the budget, headcount, and timeline specified in `<project_constraints>`.