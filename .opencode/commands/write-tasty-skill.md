---
description: Create or revise a taste-related skill (code quality, style, conventions) using TDD with subagent testing.
argument-hint: <skill name or description>
---

# Write Tasty Skill

Use the superpowers:writing-skills skill for the fundamental TDD process — this command adapts it to taste-related skills (code quality, style, documentation conventions) whose tests are judged by the human partner rather than by pass/fail assertions.

## Process

Follow each phase in order. The human partner judges all quality outcomes — never score compliance on their behalf. It is not useful to define a set of tasks for this as the process will be fairly loose.

### 1. Review skill proposal

Your human partner will propose a skill change based on either changes she's made in the repo itself or specified on the first message. Review that change and propose suggestions.

### 2. Propose task

Before running the below steps, propose a task to have subagents execute in order to test that proposal. You might be given languages to make these tasks with, but default to Typescript and Go.

### 3. RED — Baseline

1. Load the writing-skills skill and read it before proceeding.
2. Write 2+ pressure scenarios in different languages or contexts that tempt the failure the skill should prevent (e.g., one Python, one TypeScript).
3. Dispatch each scenario to a subagent WITHOUT the skill, using the code-writer agent (human partner choicedetermines the skill; scenarios target its subject matter).
4. Have subagents write output files under `.tmp/` (gitignored scratch space) and print the complete file contents with a `// Language: X, Rep N` first line, inside a code fence.
5. Delete `.tmp/` contents yourself after reviewing — do not ask subagents to delete files.
6. Document baseline failures verbatim: what choices were made, what rationalizations appeared.

### 4. GREEN — Minimal Skill

1. Write the skill addressing only the observed baseline failures. Match the guidance form to the failure type (prohibition + rationalization table for discipline failures; positive recipe for wrong-shaped output; structural template for omitted elements).
2. Re-run the same scenarios WITH the skill text injected into the subagent prompt.
3. Run 3+ reps per scenario — single samples lie.
4. Present outputs and a scorecard table to the human partner for judgment.

### 5. REFACTOR — Close Loopholes

1. Identify NEW rationalizations or failure shapes from testing (agents invent "transitive audience", `@internal` tags, false self-reports).
2. Add explicit counters; prefer recipes over prohibitions for output-shape failures.
3. Re-run 3+ reps after each wording change.

### Debugging

When a failure is unclear, append to the subagent prompt: "After printing the code, print a justification table: one row per identifier (or unit under test), with visibility/classification, whether it received the treatment, and one sentence justifying the choice." The table reveals the agent's self-model — but manually verify against the actual output, as tables have been observed to falsely report compliance.

## Conventions Observed in This Session

- Output files go in `.tmp/` (add it to .gitignore if absent)
- Subagent prints code with `// Language: X, Rep N` header in a fenced block
- Human partner deletes `.tmp/` after review
- 3 reps minimum per variant; more when distinguishing noise from regression
- Report every run as a scorecard table plus notable failure shapes, flagging borderline calls for the human partner
- Use `.opencode/agents/code-writer.md` to run subagents

# User input

$ARGUMENTS
