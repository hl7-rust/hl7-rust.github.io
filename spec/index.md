# Specs

This site doesn't restate the conversion rules. Each project's own
`spec/index.md` is the normative, section-by-section specification and the
single source of truth for its behavior:

- [hl7-2-5-to-xml-using-rust spec](https://github.com/hl7-rust/hl7-2-5-to-xml-using-rust/blob/main/spec/index.md)
- [hl7-2-5-to-json-using-rust spec](https://github.com/hl7-rust/hl7-2-5-to-json-using-rust/blob/main/spec/index.md)

The two specs are kept consistent with each other except where the target
format forces a difference (see each spec's own §0 for exactly where they're
meant to diverge: JSON uses real arrays/`null`, XML follows v2.xml's
element/attribute constructs).
