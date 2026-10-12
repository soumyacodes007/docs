# Diagrams to draw

Every diagram spot in the docs is an MDX comment placeholder. Nothing renders there until you add the
image. This file lists all of them. It is in `.mintignore`, so it never becomes a page.

## How to add one

1. Export the diagram as PNG (or SVG) to the path in the **File** column. Draw at about 1600 px wide,
   with a transparent or white background, and check it reads in dark mode too.
2. In each page listed, replace the whole `{/* DIAGRAM: ... */}` comment with:

   ```mdx
   <Frame caption="One-line caption">
     <img src="/images/diagrams/<name>.png" alt="What the diagram shows" />
   </Frame>
   ```

   For separate light and dark versions use two images with `className="block dark:hidden"` and
   `className="hidden dark:block"`.
3. Run `npx mint broken-links` and tick the box below.

## List

| Done | Name | File | Used on | What to show |
| --- | --- | --- | --- | --- |
| [ ] | `before-after` | `/images/diagrams/before-after.png` | `index.mdx` | Left, "Plain Arkiv": one wallet with arrows to 5 records, each `owner = 0xWallet`, `creator = 0xWallet`. Right, "Arkognito": the same 5 records, each with a different owner `S1`…`S5` and the same `creator = relayer`; the wallet connects to nothing on chain. |
| [ ] | `quickstart-flow` | `/images/diagrams/quickstart-flow.png` | `quickstart.mdx` | `quickstart.mjs`: wallet signs once → root key → one-time owner `S` + tag → POST to relayer → relayer waits for a batch → one Arkiv transaction (create + transfer to `S`) → client reads the batch back and verifies the signature. |
| [ ] | `key-derivation` | `/images/diagrams/key-derivation.png` | `concepts/one-time-owners.mdx`, `architecture/overview.mdx` | Wallet signs EIP-712 `"arkognito key v1"` → HKDF → root key (stays in the key worker) → per record: random 15-byte id → HKDF → one-time key `S_n`; and root → tag key → encrypted `vtag(id)`. |
| [ ] | `write-path` | `/images/diagrams/write-path.png` | `concepts/relayers-and-batching.mdx`, `architecture/overview.mdx` | Several users' clients → relayer queue → wait for `k` records or max wait → shuffle → one `executeBatch`: creates `[r1..rn]`, then ownership transfers `[r1→S1 .. rn→Sn]` → Arkiv. Each client reads the whole batch back and verifies its record. |
| [ ] | `read-path` | `/images/diagrams/read-path.png` | `concepts/finding-your-records.mdx`, `architecture/overview.mdx` | 1) download the app's list (keys, owners, tags; no payloads), the same for every user; 2) open tags locally in the key worker → "these are mine"; 3) fetch full records for those batches + 2 random cover batches; 4) verify signatures. |
| [ ] | `blind-tokens` | `/images/diagrams/blind-tokens.png` | `concepts/blind-tokens.mdx`, `architecture/overview.mdx` | Session start: client blinds 5 random messages → issuer (sees wallet + count) signs blind → client unblinds. Later, separately: client spends one token per record → relayer (sees token, not wallet) checks signature + spent list on Arkiv → writes record + spent marker in one transaction. |
| [ ] | `ohttp` | `/images/diagrams/ohttp.png` | `guides/oblivious-http.mdx`, `architecture/overview.mdx` | Browser → (encrypted to relayer key) → OHTTP relay [sees IP, not content] → relayer [sees content, not IP] → Arkiv. The relayer's gateway key comes from its heartbeat entity on Arkiv. |
| [ ] | `ownership-proof` | `/images/diagrams/ownership-proof.png` | `guides/ownership-proofs.mdx` | Verifier sends a random challenge → app calls `proveOwnership(entityKey)` → key worker signs `{ entityKey, challenge, verifier, expiresAt }` with that record's one-time key → verifier checks the signature and reads `$owner` of the entity from Arkiv. Other records stay unlinked. |
| [ ] | `deployment` | `/images/diagrams/deployment.png` | `operations/self-hosting.mdx`, `architecture/overview.mdx` | Docker Compose stack: relay-1 (relayer + issuer, volume `/data`) :8787, relay-2 :8788, ohttp-relay :8790, optional Caddy in front for HTTPS; all talk to the Arkiv Tiramisu RPC; clients discover relayers through heartbeat entities on Arkiv. |
| [ ] | `system-overview` | `/images/diagrams/system-overview.png` | `architecture/overview.mdx` | The user's browser (app + `arkognito` SDK + key worker), optional OHTTP relay, relayers (relay-1 with issuer, relay-2), and Arkiv Tiramisu holding app records (owner `S`, creator relayer), `arkognito.relayer` heartbeats, `arkognito.issuerKey`, `arkognito.spent`. Mark each trust boundary. |
| [ ] | `linkage-experiment` | `/images/diagrams/linkage-experiment.png` | `architecture/linkage-experiment.mdx` | 5 users × 10 records → relayer → 10 batches of 5 on Arkiv → observer reads only chain data and guesses "same person" pairs across consecutive batches → precision vs 1/5 chance. |

11 diagrams, 17 placeholders. To find them all:

```bash
grep -rn "DIAGRAM:" --include=*.mdx .
```
