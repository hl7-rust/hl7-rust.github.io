# hl7-rust.github.io

Source for the [HL7 Rust](https://hl7-rust.github.io) GitHub Pages site — a
landing page linking to the [hl7-rust](https://github.com/hl7-rust)
organization's HL7 v2.5 ER7 converters:

- [hl7-v2-from-er7-into-xml](https://github.com/hl7-rust/hl7-v2-from-er7-into-xml)
- [hl7-v2-from-er7-into-json](https://github.com/hl7-rust/hl7-v2-from-er7-into-json)

Built with [SvelteKit](https://svelte.dev/docs/kit) (static adapter) and the
[Lily Design System](https://github.com/LilyDesignSystem) headless Svelte
components (`lily-design-system-svelte-headless`), styled with Lily's `light`
theme stylesheet.

## Development

```sh
pnpm install
pnpm dev      # http://localhost:5173
pnpm build    # static output in build/
pnpm preview  # preview the production build
pnpm check    # svelte-check
```

Deployment is automatic: `.github/workflows/deploy.yml` builds and publishes
`build/` to GitHub Pages on every push to `main`.

## Layout

```
src/routes/+layout.svelte   Site chrome — skip link, header, nav, footer
src/routes/+page.svelte     Home page
src/routes/spec/+page.svelte  Links out to each project's normative spec
static/lily-light.css       Lily Design System "light" theme (copied from
                             lily-design-system/themes/light.css)
```
