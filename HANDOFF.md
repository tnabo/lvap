# LVAP Website — Handoff

## Where things stand

Static single-page storefront for **LVAP Industrial Products** is live at:

- **https://lvap-products.com** (custom domain, HTTPS enforced)
- **https://tnabo.github.io/lvap/** (fallback GitHub Pages URL)

Repo: **https://github.com/tnabo/lvap** — deploys from `main` / root via GitHub Pages.

## Repo layout

```
lvap/
├── index.html          # full single-page site (all markup, CSS, JS inline)
├── images/
│   ├── logo.svg        # LVAP wordmark (used in header + footer)
│   └── *.jpg           # 33 product photos
├── CNAME               # lvap-products.com
├── README.md
└── HANDOFF.md          # this file
```

No build step. What's committed is what's served.

## What's been done in this session

1. **Initial publish** — pushed the site to `tnabo/lvap` on `main`, enabled GitHub Pages (`Deploy from a branch` / `main` / `/ (root)`).
2. **Custom domain** — added `CNAME` file for `lvap-products.com`, walked user through Squarespace DNS setup (4 × A records to `185.199.108.153-111.153`, 1 × CNAME `www` → `tnabo.github.io`). HTTPS enforced.
3. **Logo swap** — replaced the CSS-drawn skewed "LVAP" box with a real `<img>` reference to `images/logo.svg`, which was extracted from the user's `LVAP_Logo.ai` file (converted via `pdftoppm` / `pdf2svg`). Footer uses `filter: invert(1)` to render the dark mark as white on the dark background.

Latest commits on `main`:

- `d93c6c0` Swap CSS logo box for real LVAP wordmark image
- `73d30cb` Use real LVAP wordmark in header and footer (added `images/logo.svg`)
- `38f23be` Add CNAME for lvap-products.com custom domain
- `b3a092d` Initial site publish — LVAP storefront

## Open items / things the next session should know

### 1. The logo file question is unresolved

The user has been showing screenshots of a **stylized italic "LVAP" wordmark with merged/connected letters inside a rounded rectangle** — but the `LVAP_Logo.ai` file they uploaded contains a **plain geometric sans-serif "LVAP"** (no stylized letters, no box). The AI file also has a black rectangle on it that was supposed to be a reversed-out variant, but the "white LVAP" text inside was flattened to black during export, so the interior text is invisible.

The current site uses the plain sans-serif version because that's what's in the actual asset file. If the user wants the italic/stylized version, they need to provide the correct source file (SVG or high-res transparent PNG).

### 2. Header still has "INDUSTRIAL PRODUCTS" text lockup

Right now the header is: `[LVAP logo image]  INDUSTRIAL PRODUCTS`. The user didn't answer my question about whether to keep or drop that text. Leave as-is unless they ask.

### 3. Amazon links

Every "Buy" button in `index.html` currently points to the user's Amazon **storefront** (`https://www.amazon.com/stores/page/2449504E-D60C-42A1-B336-D360D8B9F1D6`). They plan to swap individual product links later — do **not** change these unless the user explicitly asks per-product.

### 4. Contact email placeholder

Footer has `mailto:your@email.com` — that's from the original template. The user hasn't given a real email yet. Ask if they want it filled in.

## Environment notes for the next Claude session

- Repo is at `/home/user/lvap`, cloned fresh in each remote session.
- Development branch per system prompt is `claude/keen-tesla-NWd5i`, but the user explicitly directed the initial publish to `main`. All work in this session went to `main`.
- **Git push auth was flaky** partway through — the local git proxy port changed after an MCP disconnect/reconnect and re-authentication failed. Workarounds that worked:
  - `git ls-remote` and `git fetch` from the public `https://github.com/tnabo/lvap` URL (read-only, no auth needed).
  - `mcp__github__push_files` and `mcp__github__create_or_update_file` for pushes.
  - If direct `git push` fails again with `could not read Password for 'http://local_proxy@...'`, fall back to the MCP tools instead of trying to fix the proxy.
- The user's `LVAP_Logo.ai` file is at `/root/.claude/uploads/f87ace15-dd96-53ec-91b7-da37758449b7/c9af156b-LVAP_Logo.ai` (this session's upload dir; will not survive into a new session — they'd need to re-attach).
- **Do not create PRs** unless the user explicitly asks. All commits should go directly to `main` on the user's confirmation, matching how this session operated.

## User context

- User email: `tnabo@prosbranding.com`
- Registrar for `lvap-products.com`: Squarespace
- GitHub account: `tnabo`
- Domain DNS is set up, HTTPS cert issued and enforced — no more DNS/cert work needed unless they change domains.
