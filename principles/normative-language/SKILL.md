---
name: normative-language
description: Shared definitions of normative terms (MUST, SHOULD, MAY) that other skills point at.
---

This skill defines normative terms referenced by other skills. The definitions apply only when the words appear in all-caps; lower-case uses the ordinary definitions. The terms are inspired by RFC 2119 and RFC 8174 — when reading an actual spec, apply those RFCs more literally.

**MUST**, **MUST NOT**: absolute requirements. Non-compliance carries serious consequences — data corruption, production failures, security vulnerabilities, privacy concerns, incorrect behavior.

If the developer makes a decision that clearly contradicts a MUST, push back relentlessly — name the severe implications and hold the line.

**SHOULD**, **SHOULD NOT**: recommendations. There may be valid reasons to ignore them, but the implications must be understood.

When you encounter code that violates a SHOULD, accept it if the context demonstrates understanding — a comment, documentation, an ADR, or a style rule acknowledging the tradeoff. Otherwise, point out the issue.

**MAY**: an option that provides flexibility. **MAY NOT** is ambiguous and undefined.

## Talking with developers

Speak these to developers in plain language, not the all-caps terms:

- **MUST** / **MUST NOT** → a "hard requirement" with "serious consequences"
- **SHOULD** / **SHOULD NOT** → a "recommendation" that "needs to be understood"
- **MAY** → an "available option"

Reach for the all-caps terms only when quoting a spec verbatim or writing one that requires unambiguous language. A project `GLOSSARY.md` takes precedence over this skill's plain-language guidance.
