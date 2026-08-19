---
name: doc-comments
description: Doc comment depth scales with identifier visibility. Reach when writing, editing, or reviewing doc comments — JSDoc, Python docstrings, rustdoc, or similar.
---

Doc comments serve callers, not readers of the implementation. Depth scales with visibility: the wider an identifier's audience, the more its documentation must stand alone.

Visibility is determined by export status, not current usage. An identifier exported but unused elsewhere still has an audience and still needs documenting.

## Glossary

- **identifier**: named symbol that may be referenced elsewhere in code. Includes anything that may be named, including variables, constants, functions, methods, classes, interfaces, structs, or types. There may be other forms from language to language. For the purpose of this skill, an identifier must also be a name that can be documented.

## Rules

- Private identifiers (not used outside the current file) MUST NOT have doc comments. Readers of the file can see the implementation.
- Package-private identifiers (used outside the file but not outside the package) SHOULD have terse doc comments: one or two sentences stating purpose.
- Public identifiers (used outside the package) MUST have in-depth doc comments.

Before writing a file, classify every identifier by visibility — private, package-private, or public — and write doc comments only for the levels that get them.

## What in-depth means

A public doc comment is a contract. It documents:

- What the identifier does and when to use it
- Parameters and return values, including units and formats
- Error conditions: what it raises, throws, or rejects, and when
- Side effects such as I/O, mutation, or persistence
- Edge cases callers must know: empty input, rounding, overflow

For types, the contract lives on the members: every property, field, or method MUST have its own documentation — valid values, units, defaults, and invariants. The type itself MUST also have a doc comment stating what it represents, when to use it, and how it relates to the rest of the API; it MUST NOT restate anything documented on the members.

## Examples

The same function documented at each level of visibility:

```ts
// private — no doc comment
function roundCents(cents: number): number {
  return Math.sign(cents) * Math.round(Math.abs(cents));
}

// package-private — one or two sentences
/** Round fractional cents half-up to the nearest whole cent. */
function roundCents2(cents: number): number { ... }

// public — full contract
/**
 * Rounds fractional cents half-up to the nearest whole cent.
 *
 * @param cents - Amount in fractional cents; may be negative.
 * @returns Whole cents. Negative amounts round away from zero.
 */
export function roundCents3(cents: number): number { ... }
```

In Python, docstrings are doc comments and these rules apply to them. A leading underscore marks private; `__all__` and the package layout separate public from package-private.

```python
# private — no docstring
def _validate_sku(sku: str) -> None: ...

# package-private — one or two sentences
def parse_sku(raw: str) -> str:
    """Normalize a raw SKU string, raising ValueError if malformed."""

# public — full contract
def load_inventory(path: Path) -> Inventory:
    """Load an Inventory from *path*.

    Creates an empty inventory bound to *path* if the file does not
    exist. Raises ValueError if the file is not a JSON object of
    SKU to non-negative integer quantities.
    """
```

## Justification table

If asked for justification, print a table with one row per identifier in the file:

| Identifier | Visibility | Doc comment? | Justification |
|---|---|---|---|
| `roundCents` | Private | No | Not exported; readers of the file can see the implementation. |
| `calculateTotal` | Public | Yes — in-depth | Exported function consumed by other packages; documents params, returns, and error conditions. |

## Gotchas

- Documenting a private helper because it is "complex" — if it is not used outside the file, complexity is the implementation's problem.
- A one-line summary on a public API — public identifiers need the contract, not a summary.
- Judging visibility by usage ("nothing imports it yet") — export status decides.
- Documenting a private helper because its behavior surfaces through an exported function — users of exported members do not care about any private members they may refer to. Document the behavior on the exported member instead.
- Repeating type signatures in prose — the types already say that; document what they cannot.

## Conventions and style rules

Language conventions and style rules MUST supercede these instructions. Where a project's style guide, linter, or language conventions dictate their own doc comment rules, follow those instead.
