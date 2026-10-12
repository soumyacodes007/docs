# Arkognito docs

Documentation for [Arkognito](https://github.com/soumyacodes007/Arkognito): unlinkable ownership for
[Arkiv](https://arkiv.network) apps. Records are owned by one-time addresses, written by relayers in
shuffled batches, and found again with nothing but the user's wallet.

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
| `concepts/` | How it works: linkability, one-time owners, relayers and batching, envelopes, finding records, blind tokens, fingerprinting, threat model |
| `operations/` | Self-hosting, Railway and Vercel, OHTTP relay, security, troubleshooting |
| `reference/` | SDK, relayer API, configuration, entities, protocol, edge cases |
| `architecture/` | Architecture overview, linkage experiment, notes on Arkiv |
| `openapi.json` | Relayer and issuer API, rendered in the API Reference tab |
| `images/diagrams/` | Diagram images |
| `DIAGRAMS.md` | Every diagram placeholder still to draw |
| `AGENTS.md` | Writing rules for people and coding agents |

## Diagrams

Diagram spots are MDX comment placeholders. [`DIAGRAMS.md`](DIAGRAMS.md) lists each one, its file
name, the pages that use it and what it should show.

## Publishing

Install the Mintlify GitHub app on this repository from the Mintlify dashboard. Pushes to `main`
deploy automatically.

## License

MIT
