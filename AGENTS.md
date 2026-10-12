# AGENTS.md: Arkognito docs

Instructions for anyone (human or coding agent) editing this documentation site.

## About this project

- Documentation for [Arkognito](https://github.com/soumyacodes007/Arkognito): unlinkable ownership
  for Arkiv apps. A client SDK (`arkognito`) plus self-hostable relayer, token issuer and OHTTP relay.
- Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter; navigation and theme
  live in `docs.json`; the API Reference tab is generated from `openapi.json`.
- Preview with `npx mint dev`; check links with `npx mint broken-links`.

## Facts come from the code

Every number, default, error message, endpoint and environment variable must match the Arkognito
source (`packages/sdk/src`, `packages/relayer/src`, `spec/SPEC.md`). Check before you write; if the
code changes, update the docs in the same week.

- Never invent hosted URLs. Use `https://relay-1.example.com`, `https://ohttp.example.com` and similar.
- Never put a private key, access key, seed or real personal data in a page, example or screenshot.
- Say plainly what is not built or not proven (audit, mainnet, smart-contract wallets).

## Terminology

| Use | Not |
| --- | --- |
| one-time owner (`S`) | stealth address, burner |
| relayer | sequencer, server, node |
| token issuer, issuer | mint, authority |
| OHTTP relay | proxy |
| record | entity, when it is the app's data; "entity" for Arkiv's own term |
| key worker | enclave |
| tag (`vtag`) | label, hint |
| batch | block, bundle |
| Arkiv, Tiramisu | Arkiv chain, Arkiv network |

## Style

- Active voice, second person ("you"), present tense. One idea per sentence.
- Sentence case for headings and titles.
- Code formatting for file names, commands, paths, attribute names, env vars and code references.
- **Bold** for UI elements.
- Every page has `title` and `description` in frontmatter; add `keywords` for search.
- Lead with what the reader can do; put caveats in `<Warning>` or `<Note>`, not mid-paragraph.
- Prefer tables for options, defaults, status codes and env vars.

## MDX caveats

- A bare `{` or `<` in prose is parsed as JSX and breaks the build. Keep them inside code spans or
  code blocks.
- Comments are `{/* ... */}`, never `<!-- -->`.

## Diagrams

The maintainer draws all diagrams. Do not create images. Leave a placeholder where a diagram belongs:

```mdx
{/* DIAGRAM: <name>
    File: /images/diagrams/<name>.png
    Show: what the diagram must show. */}
```

Then add a row to `DIAGRAMS.md`. Reuse an existing name when the same diagram fits.

## Content boundaries

- Document the public SDK, relayer API, configuration, protocol and operations.
- Do not document internal test helpers or scripts beyond linking to them.
- `DIAGRAMS.md` and `AGENTS.md` are working notes and listed in `.mintignore`.
