---
name: opinions
description: Explains the `Opinions` headers and "opinionated" mentions across these skills — what they assert, and what to do when a case conflicts with one.
---

In engineering terms, being "opinionated" means going out on a limb and making assumptions that not everyone may agree with. These skills use `Opinions` headers and "opinionated" mentions to mark where clear principles end and subjective opinions begin.

When you see an `Opinions` header or mention that something is opinionated, here's what you should do:

1. Unless it is documented somewhere that it is untrue or needs to be modified, start from the assumption that it's true
2. When a decision conflicts with the opinion, or a case makes it impractical, raise it with the user and decide together whether to override or modify it
3. Figure out how or whether to document the outcome. Here are some ways to proceed:
   a. If it's merely a matter of coding preferences, document it in a `CONTRIBUTING.md` file, `CODING_STANDARDS.md` file, or any other place code style is documented.
   b. If it's an actual architectural or domain-level decision, create an ADR if there is a defined place to record them.
   c. If all else fails, document it in `AGENTS.md`
