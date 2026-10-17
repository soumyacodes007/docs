# Arkognito docs

Documentation for [Arkognito / Veil](https://github.com/soumyacodes007/Arkognito): reduced wallet linkage for
[Arkiv](https://arkiv.network) apps. Records are owned by one-time addresses, written by relayers in
shuffled batches, and found again through the user's wallet, passkey or recovery-backed vault.
Optional Semaphore integration adds anonymous group permissions. This is not complete anonymity.

Built with [Mintlify](https://mintlify.com).

## Preview locally

Needs Node 20 or later.

```bash
npx mint dev
```

Open `http://localhost:3000`. Check links before you push:

```bash
npx mint broken-links
```

## Structure

| Path | What |
| --- | --- |
| `docs.json` | Theme, navigation and tabs |
| `index.mdx`, `quickstart.mdx` | Introduction and a first private record |
| `guides/` | Task guides: add to an app, migrate from the Arkiv SDK, read records, proofs, private payloads, tokens, OHTTP |
| `guides/anonymous-membership.mdx` | Semaphore enrollment, proof-gated writes and independent verification |
| `integrations/` | Optional admission policies, including the experimental Anon Aadhaar boundary |
| `concepts/` | How it works: linkability, one-time owners, relayers and batching, envelopes, finding records, blind tokens, fingerprinting, threat model |
| `operations/` | Self-hosting, Railway and Vercel, OHTTP relay, security, troubleshooting |
| `reference/` | SDK, relayer API, configuration, entities, protocol, edge cases |
| `architecture/` | Architecture overview, linkage experiment, Semaphore validation, notes on Arkiv |
| `openapi.json` | Relayer and issuer API, rendered in the API Reference tab |
| `images/diagrams/` | Diagram images |
| `DIAGRAMS.md` | Every diagram placeholder still to draw |
| `AGENTS.md` | Writing rules for people and coding agents |

The Semaphore pages describe the `0.1.0` source package, with recorded integration evidence from
revision `a2255fe`. They distinguish measured functionality from remaining production work and
link the [published npm release](https://www.npmjs.com/package/arkognito/v/0.1.0), with a source-build fallback.

## Diagrams

Diagram spots are MDX comment placeholders. [`DIAGRAMS.md`](DIAGRAMS.md) lists each one, its file
name, the pages that use it and what it should show.

## Publishing

Install the Mintlify GitHub app on this repository from the Mintlify dashboard. Pushes to `main`
deploy automatically.

## License

MIT
