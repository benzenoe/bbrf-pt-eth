# bbrf-pt.eth — On-Chain Site Bundle

Static, IPFS-ready build of the **BBRF-PT** investor site (Bitcoin-Backed Real-Estate Fund — Portugal), prepared for deployment to the ENS name **`bbrf-pt.eth`**.

**Canonical web version:** https://eytan.com/pitches/bbrf-pt.html (source of truth for content — this repo is the on-chain mirror).

## What's in here

| Path | Contents |
|---|---|
| `index.html` | Entry point — English crypto-investor version (with the 3-audience gate) |
| `bbrf-pt[-fr\|-pt].html` | Crypto-investor version — EN / FR / PT |
| `bbrf-pt-private[-fr\|-pt].html` | Traditional-investor version — EN / FR / PT |
| `bbrf-pt-partners[-fr\|-pt].html` | Real-estate partner programme — EN / FR / PT |
| `BBRF-PT-Investor-Memorandum.pdf` | 19-page memorandum (EN) |
| `BBRF-PT-Memorandum-Investisseur.pdf` | 19-page memorandum (FR) |
| `BBRF-PT-Memorando-Investidor.pdf` | 19-page memorandum (PT) |
| `properties/pebble-stone/` | Pilot asset — brochure, aerial gallery, estate PDF, photography |

All internal links and assets are **relative** — the bundle is fully self-hosting from any directory root or IPFS CID.

## Deploy to bbrf-pt.eth (runbook)

1. **Pin to IPFS.** Easiest: [Fleek](https://fleek.xyz) — connect this GitHub repo, framework "None / static", publish directory `/`. Every push re-pins automatically. (Alternatives: upload the folder to Pinata or web3.storage and note the CID.)
2. **Set the contenthash.** In the [ENS Manager](https://app.ens.domains) → `bbrf-pt.eth` → **Records → Content Hash** → `ipfs://<CID>` (Fleek can also manage this automatically via its ENS integration). One wallet signature.
3. **Verify.**
   - Gateway (everyone): **https://bbrf-pt.eth.limo**
   - Native: `bbrf-pt.eth` in Brave / MetaMask browser
4. **Recommended text records** (same screen in the ENS app):
   - `url` → `https://eytan.com/pitches/bbrf-pt.html`
   - `email` → `eytan@benzeno.com`
   - `description` → `Bitcoin-Backed Real-Estate Fund — Portugal. The Bitcoin is never sold.`
   - `avatar` → hosted logo URL (optional)

## Notes

- **Updates:** IPFS content is immutable. Without Fleek, each content update = re-pin + new contenthash. With Fleek + ENS integration, a `git push` here is enough.
- **External calls:** pages load Google Fonts and Chart.js from CDNs, and the live BTC ticker calls the Coinbase API. All of this works through eth.limo and Brave. A fully self-contained (zero-CDN) build is possible if wanted.
- **Content changes** should be made on eytan.com first (canonical), then synced here.

---
*BBRF-PT · A Bittrees venture · Eytan Benzeno (eytan@benzeno.com) · Jonathan Hineline (jhineline@bittrees.io)*
