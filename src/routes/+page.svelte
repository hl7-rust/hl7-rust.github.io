<script lang="ts">
  import Card from 'lily-design-system-svelte-headless/components/Card/Card.svelte';
  import Badge from 'lily-design-system-svelte-headless/components/Badge/Badge.svelte';

  const xmlExample = `<PID>
  <PID.1>1</PID.1>
  <PID.3><CX.1>241900</CX.1></PID.3>
  <PID.5><XPN.1><FN.1>TEST</FN.1></XPN.1><XPN.2>FOUAZ</XPN.2></PID.5>
</PID>`;

  const jsonExample = `{
  "PID": {
    "PID.1": "1",
    "PID.3": { "CX.1": "241900" },
    "PID.5": { "XPN.1": { "FN.1": "TEST" }, "XPN.2": "FOUAZ" }
  }
}`;

  const features = [
    'ER7 parsing at every level: segments, fields, repetitions (~), components (^), and subcomponents (&).',
    'Dynamic delimiters, read from MSH-1/MSH-2 rather than hardcoded.',
    'Typed names: built-in HL7 v2.5 tables map each field of the common segments and composite types to its data type — Z-segments and uncommon types still convert, using positional generic names.',
    'Message-structure groups for ACK, ADT_A01, ORM_O01, and ORU_R01.',
    'Graceful fallback rather than failure: unknown structures render flat, unknown fields use positional generic names.',
    'Neither crate is a validator — no schema, cardinality, or table checking is performed.'
  ];
</script>

<svelte:head>
  <title>HL7 Rust</title>
</svelte:head>

<section class="hero">
  <div class="hero-inner">
    <p class="eyebrow"><Badge label="Organization">hl7-rust</Badge></p>
    <h1>HL7 Rust</h1>
    <p class="lede">
      Rust libraries and command-line tools that convert HL7 version 2.5 messages from the
      traditional pipe-delimited ER7 encoding into other representations.
    </p>
    <div class="cta-row">
      <a class="button" href="https://github.com/hl7-rust">GitHub organization</a>
    </div>
  </div>
</section>

<section class="section">
  <div class="section-inner">
    <h2>Projects</h2>
    <div class="card-grid">
      <Card
        heading="hl7-2-5-to-xml-using-rust"
        href="https://github.com/hl7-rust/hl7-2-5-to-xml-using-rust"
        headingLevel={3}
      >
        <p>
          ER7 to the official HL7 <strong>v2.xml</strong> XML representation
          (<code>urn:hl7-org:v2xml</code>).
        </p>
      </Card>
      <Card
        heading="hl7-2-5-to-json-using-rust"
        href="https://github.com/hl7-rust/hl7-2-5-to-json-using-rust"
        headingLevel={3}
      >
        <p>
          ER7 to a typed <strong>JSON</strong> representation designed to preserve everything
          v2.xml preserves, using idiomatic JSON instead of XML's constructs.
        </p>
      </Card>
    </div>
    <p>
      Both crates share the same ER7 parser
      (<a href="https://crates.io/crates/er7"><code>er7</code></a> on crates.io), the same
      HL7 v2.5 data-type tables, and the same message-structure grammars — only the rendered
      output format differs.
    </p>
  </div>
</section>

<section class="section section-alt">
  <div class="section-inner">
    <h2>Example</h2>
    <p>An ER7 fragment such as:</p>
    <pre><code>PID|1||241900||TEST^FOUAZ</code></pre>
    <div class="example-grid">
      <div>
        <h3>converts to XML</h3>
        <pre><code>{xmlExample}</code></pre>
      </div>
      <div>
        <h3>and to JSON</h3>
        <pre><code>{jsonExample}</code></pre>
      </div>
    </div>
  </div>
</section>

<section class="section">
  <div class="section-inner">
    <h2>What they do</h2>
    <ul class="feature-list">
      {#each features as feature (feature)}
        <li>{feature}</li>
      {/each}
    </ul>
    <p>See <a href="/spec/">Specs</a> for where each project's normative conversion rules live.</p>
  </div>
</section>

<style>
  .hero-inner,
  .section-inner {
    max-width: 64rem;
    margin: 0 auto;
    padding: 2.5rem 1.5rem;
  }

  .eyebrow {
    margin: 0 0 0.75rem;
  }

  .lede {
    max-width: 42rem;
    font-size: 1.125rem;
  }

  .cta-row {
    margin-top: 1.5rem;
  }

  /* The theme's baseline .button uses --color-primary as its background,
     which is also the hero's own background — invert it here so the CTA
     stays visible against the hero. */
  .cta-row :global(.button) {
    background-color: var(--color-base-100, #fff);
    color: var(--color-primary, #4f39f6);
  }

  .cta-row :global(.button:hover) {
    background-color: var(--color-base-200, #f5f5f4);
  }

  .section-alt {
    background: var(--color-base-200, #f5f5f4);
  }

  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr));
    gap: 1.5rem;
    margin: 1.5rem 0;
  }

  .example-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr));
    gap: 1.5rem;
    margin-top: 1rem;
  }

  .example-grid pre {
    overflow-x: auto;
  }

  .feature-list {
    display: grid;
    gap: 0.5rem;
  }
</style>
