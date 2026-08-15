# HL7 Rust

Rust libraries and command-line tools that convert HL7 version 2.5 messages
from the traditional pipe-delimited ER7 encoding into other representations.

## Projects

- [hl7-2-5-to-xml-using-rust](https://github.com/hl7-rust/hl7-2-5-to-xml-using-rust) —
  ER7 to the official HL7 **v2.xml** XML representation (`urn:hl7-org:v2xml`).
- [hl7-2-5-to-json-using-rust](https://github.com/hl7-rust/hl7-2-5-to-json-using-rust) —
  ER7 to a typed **JSON** representation designed to preserve everything
  v2.xml preserves, using idiomatic JSON instead of XML's constructs.

Both crates share the same ER7 parser ([`er7`](https://crates.io/crates/er7)
on crates.io), the same HL7 v2.5 data-type tables, and the same
message-structure grammars — only the rendered output format differs.

## Example

An ER7 fragment such as:

```
PID|1||241900||TEST^FOUAZ
```

converts to XML:

```xml
<PID>
  <PID.1>1</PID.1>
  <PID.3><CX.1>241900</CX.1></PID.3>
  <PID.5><XPN.1><FN.1>TEST</FN.1></XPN.1><XPN.2>FOUAZ</XPN.2></PID.5>
</PID>
```

and to JSON:

```json
{
  "PID": {
    "PID.1": "1",
    "PID.3": { "CX.1": "241900" },
    "PID.5": { "XPN.1": { "FN.1": "TEST" }, "XPN.2": "FOUAZ" }
  }
}
```

## What they do

- ER7 parsing at every level: segments, fields, repetitions (`~`),
  components (`^`), and subcomponents (`&`).
- Dynamic delimiters, read from MSH-1/MSH-2 rather than hardcoded.
- Typed names: built-in HL7 v2.5 tables map each field of the common
  segments and composite types to its data type. Anything outside the
  tables (Z-segments, uncommon types) still converts, using positional
  generic names instead.
- Message-structure groups for ACK, ADT_A01, ORM_O01, and ORU_R01.
- Graceful fallback rather than failure: unknown structures render flat,
  unknown fields use positional generic names.
- Neither crate is a validator — no schema, cardinality, or table checking
  is performed.

See [Specs](spec/) for where each project's normative conversion rules live.

## Source

Both projects are developed on
[GitHub](https://github.com/hl7-rust),
[GitLab](https://gitlab.com/hl7-rust), and
[Codeberg](https://codeberg.org/hl7-rust).
