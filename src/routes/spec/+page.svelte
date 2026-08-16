<svelte:head>
  <title>Specs — HL7 Rust</title>
</svelte:head>

<section class="section">
  <div class="section-inner">
    <h1>Specs</h1>
    <p>
      This site doesn't restate the conversion rules. Each project's own <code>spec/index.md</code>
      is the normative, section-by-section specification and the single source of truth for its
      behavior:
    </p>
    <ul>
      <li>
        <a href="https://github.com/hl7-rust/hl7-v2-from-er7-into-xml/blob/main/spec/index.md"
          >hl7-v2-from-er7-into-xml spec</a
        > — ER7 → v2.xml XML
      </li>
      <li>
        <a href="https://github.com/hl7-rust/hl7-v2-from-xml-into-er7/blob/main/spec/index.md"
          >hl7-v2-from-xml-into-er7 spec</a
        > — v2.xml XML → ER7
      </li>
      <li>
        <a href="https://github.com/hl7-rust/hl7-v2-from-er7-into-json/blob/main/spec/index.md"
          >hl7-v2-from-er7-into-json spec</a
        > — ER7 → typed JSON
      </li>
      <li>
        <a href="https://github.com/hl7-rust/hl7-v2-from-json-into-er7/blob/main/spec/index.md"
          >hl7-v2-from-json-into-er7 spec</a
        > — typed JSON → ER7
      </li>
    </ul>
    <p>
      The two <em>forward</em> specs (ER7 → XML, ER7 → JSON) are kept consistent with each other
      except where the target format forces a difference (see each one's own §0 for exactly
      where they're meant to diverge: JSON uses real arrays/<code>null</code>, XML follows
      v2.xml's element/attribute constructs). Each <em>reverse</em> spec documents, in its own
      §1.1, why it needs no HL7 v2.5 data-type dictionary at all: every element or key name its
      forward counterpart writes already carries its own position, so reversing the conversion
      is a purely structural, position-based rebuild.
    </p>
  </div>
</section>

<style>
  .section-inner {
    max-width: 64rem;
    margin: 0 auto;
    padding: 2.5rem 1.5rem;
  }
</style>
