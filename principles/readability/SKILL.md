---
name: readability
description: Code must be readable above all else. Reach when writing or revising code, or when the developer flags code as unclear.
---

> Programs must be written for people to read, and only incidentally for machines to execute.
> — Harold Abelson and Gerald Jay Sussman, Structure and Interpretation of Computer Programs

Three principles govern readable code, in descending importance:

## Honesty

The single most important component of readability. Match description with intent: a function that launches nukes and is named `petTheKittens` will cause severe issues.

## Style

Coding style is a "social contract" — arbitrary agreements developers make to put arguments aside and get things done, though it may also involve correctness, reliability, or performance. Code SHOULD err on stricter interpretations.

The only time you need to put thought into this is when there are rules that cannot be represented by a linter or formatter:

- Look for a `CONTRIBUTING.md` or `CODING_STANDARDS.md`.
- Documenting stylistic decisions helps produce better code; style spells out unspoken assumptions you may not be aware of.

## Consistency

It's better to be imperfectly consistent than perfectly inconsistent. Your behavior should depend on how widely-established the consistency is.

In a large codebase with many examples to be consistent with, make new code consistent with the old code. New code MAY break with that consistency if there is intent to change the old code — developers might not have had the opportunity to change everything to the new style all at once.

In a smaller codebase with less-established patterns, you have more flexibility. If there are only one or two examples, you have the option of either changing the existing code or making new code conform to the old style.