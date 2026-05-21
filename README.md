# LVAP Website — Quick Guide

## What's in this folder

```
LVAP-Website/
├── index.html       ← The website (open this in a browser to preview)
└── images/          ← All product photos (33 files)
```

## Preview it locally

Just **double-click `index.html`** — it'll open in your browser. No server needed.

---

## How to edit your products

Open `index.html` in any text editor (Notepad++, VS Code, Sublime, even Notepad).

### To change a product
Find the product in the file (search for part of its name, e.g. "Anti-Splash Urinal Screen"). Each product looks like this:

```html
<article class="product reveal" data-category="screens">
  <div class="product-img">
    <img src="images/screen-blue-12pk.jpg" alt="...">
  </div>
  <div class="product-body">
    <div class="product-cat">Urinal Screens</div>
    <div class="product-name">Anti-Splash Urinal Screen — Blue</div>
    <div class="product-desc">Wave-pattern deodorizing screen...</div>
    <div class="product-foot">
      <span class="product-pack">12-Pack</span>
      <a href="https://www.amazon.com/stores/page/2449504E..." target="_blank" rel="noopener" class="buy-btn">Buy</a>
    </div>
  </div>
</article>
```

You can edit:
- **Name** (`product-name`)
- **Description** (`product-desc`)
- **Pack info** (`product-pack`)
- **Amazon link** — change the `href="..."` to the exact product listing URL on Amazon
- **Image** — change `src="images/..."` to point to a different image

### To add a tag/badge
Inside `product-img`, add a line like:
```html
<span class="product-tag teal">Best Seller</span>
```
Available styles: `teal`, `orange`, or plain (just `product-tag`).

---

## Right now: all buttons go to your Amazon storefront

I set every "Buy" button to your storefront URL because I don't have your individual product listing links. When you have time, replace each link with the direct Amazon listing URL for that specific product. Find-and-replace works well for this.

---

## Putting it online with GitHub Pages

1. Go to **github.com** and create a free account (if you don't have one)
2. Click the green **"New"** button to create a new repository
   - Name: `lvap-website` (or whatever you like)
   - Set it to **Public**
   - Check "Add a README" → click **Create repository**
3. Click **"Add file" → "Upload files"**
4. Drag the **entire contents** of the `LVAP-Website` folder into the upload area (both `index.html` AND the `images` folder)
5. Scroll down, click **"Commit changes"**
6. Go to repo **Settings → Pages**
7. Under "Branch", select `main` and `/ (root)` → click **Save**
8. Wait 1–2 minutes. Refresh the Pages settings — you'll see your live URL (like `yourname.github.io/lvap-website`)

## Pointing your Squarespace domain at it

1. In Squarespace: **Settings → Domains → [your domain] → DNS Settings**
2. Add these records (GitHub's instructions are at https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site):
   - **4 × A records** pointing your apex domain (`yourdomain.com`) to GitHub's IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - **1 × CNAME record** for `www` pointing to `yourname.github.io`
3. In your GitHub repo Settings → Pages → **Custom domain**, type your domain → Save
4. Wait for DNS to propagate (can take a few hours, sometimes faster)
5. Once it works, check **"Enforce HTTPS"**

---

## Tips

- **Image file size:** all images are already optimized to ~200KB each. If you add new images, try to keep them under 500KB and around 1200px wide.
- **Filenames:** use lowercase letters, numbers, and hyphens only. No spaces, no parentheses. So `mop-bucket.jpg` ✓ not `Mop Bucket (1).jpg` ✗
- **Test before pushing:** open `index.html` in your browser after every change to make sure nothing broke.
