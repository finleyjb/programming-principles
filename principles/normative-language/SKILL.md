---
name: normative-language
description: Definitions of the words "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", and "MAY"
---

This skill defines normative language that may be referenced in other skills. It serves to remove ambiguity of language you may see in other skills. What follows are definitions of these words and the behaviors they imply. Note that these definitions only apply when they are written in all-caps. If these words are in lower-case, they should use the more common definitions of the words. These words are inspired by RFC 2119 and RFC 8174.

Note that if you are reading an actual spec, you should apply [RFC 2119](https://www.rfc-editor.org/info/rfc2119/) and [RFC 8174](https://www.rfc-editor.org/info/rfc8174/) more literally.

**MUST**, **MUST NOT**: These imply absolute requirements. There are serious consequences of making a decision such as data corruption, production failures, security vulnerabilities, privacy concerns, incorrect behavior or other consequences. **MUST** implies that these consequences are a result of not doing something that must be done. **MUST NOT** implies that there are consequences for doing something that must not be done.

Here are some behaviors that you should engage in with relation to this terminology:

- Unless specified otherwise, assume these things are common knowledge and that there is no need to explain them. If it is specified that something is not common knowledge, briefly explain them to the developer, but do not belabor the point. If the developer wants more info, they'll ask.
- If you encounter code that violates these requirements, very clearly point out the issue and offer to patch the code.
- If a user makes a decision, and it is unclear that the user understands the implications of that decision, plainly point it out. For example, the user might suggest a decision that will only function if you use the language's `eval` functionality (if it exists). They may not be aware that this is the case, and will need the reasoning for not doing that very clearly spelled out to them.
- If the developer makes a decision that clearly contradicts these requirements, push back very hard. You should explain that there are very severe implications for the decision they make.

**SHOULD**, **SHOULD NOT**: These imply that there might be valid reasons to ignore something, but the implications of ignoring them must be understood. **SHOULD** implies that there is behavior that is recommended. **SHOULD NOT** implies that behavior is not recommended.

Here are behaviors that you should engage in with relation to this terminology:

- The key consideration is whether the developer is aware of these recommendations and understands the consequences for deciding against them. If the developer clearly understands these things, do not mention them. If the developer does not clearly understand these things, casually explain the issue to them and accept any pushback.
- If you encounter code that violates one of these recommendations, look at the context of the code. If there are comments or documentation explaining the problem and demonstrate understanding of the situation, accept the code. If the behavior is in line with an ADR or style rule, you should also accept it.
- If you write code that violates these recommendations, briefly point it out to the developer.
- When doing any form of planning, offer solutions that follow these recommendations. If it is clear that breaking recommendations is necessary for the project, briefly explain that and the reasoning.

**MAY**: This implies that there is an option developers have that would provide them with flexibility. Note that **MAY NOT** is ambiguous and undefined.

Here are behaviors you should engage with in relation to this terminology:

- Generally, assume that this does not need to be explained unless it is relevant to a given decision.
- If the option genuinely provides options that significantly benefit the project, point them out.

Avoid using any of this language directly with developers. Also avoid using it in documentation or code. Here is language you should prefer:

- **MUST**/**MUST NOT**: You should discuss this as a "hard requirement" with "serious consequences".
- **SHOULD**/**SHOULD NOT**: You should discuss this as a "recommendation" that "needs to be understood"
- **MAY**: You should discuss this as an "available option"

There are two situations where you might want to use this language:

- You are quoting from an actual spec that uses this language
- You are writing a spec that requires unambiguous language. But note that there may be a `GLOSSARY.md` file that recommends alternate language.
