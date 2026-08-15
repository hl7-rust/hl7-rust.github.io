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
        <a href="https://github.com/hl7-rust/hl7-2-5-to-xml-using-rust/blob/main/spec/index.md"
          >hl7-2-5-to-xml-using-rust spec</a
        >
      </li>
      <li>
        <a href="https://github.com/hl7-rust/hl7-2-5-to-json-using-rust/blob/main/spec/index.md"
          >hl7-2-5-to-json-using-rust spec</a
        >
      </li>
    </ul>
    <p>
      The two specs are kept consistent with each other except where the target format forces a
      difference (see each spec's own §0 for exactly where they're meant to diverge: JSON uses
      real arrays/<code>null</code>, XML follows v2.xml's element/attribute constructs).
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
