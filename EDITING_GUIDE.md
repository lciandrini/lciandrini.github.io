# Site Editing Guide

Quick reference for adding content to lciandrini.github.io.

---

## Adding a News Item

Edit **two files**:

### 1. `index.html` — homepage (keep to 3 items, remove the oldest)

Add at the top of the news block (around line 135):
```html
<div class="news-item"><b>Month Year</b><p>Your text. <a href="URL" target="_blank" style="background:#ddf4ed;color:#0f6e56;border-radius:12px;font-size:11px;padding:2px 9px;text-decoration:none;display:inline-block;">DOI</a></p></div>
```

Pill colour options:
- DOI: `background:#ddf4ed;color:#0f6e56`
- ArXiv: `background:#fef3d0;color:#7a5000`
- BioRxiv: `background:#f0e8f8;color:#5a2080`

### 2. `allnews.html` — full archive (add at the top of the jumbotron)

```html
<p>
  <strong>Month Year</strong> —
<br />
    Your text here. Optional: <a href="URL" target="_blank">link</a>
<br />
</p>
```

---

## Adding a Team Member

Edit **`team/index.html`** — three things:

### 1. Add a card inside `<div id="team-grid">` (copy and adjust `data-idx`)

```html
<div class="team-member-wrap" data-member="KEY" data-idx="N"
     style="text-align:center;border:2px solid #dde;border-radius:8px;padding:14px 6px 10px;cursor:pointer;transition:border-color 0.15s,background 0.15s;">
  <img src="https://lciandrini.github.io/assets/images/team/PHOTO.jpg"
       style="width:72px;height:72px;border-radius:50%;object-fit:cover;border:1px solid #e0e0e0;" />
  <div style="font-weight:600;font-size:12px;margin-top:8px;line-height:1.3;">Full Name</div>
  <div style="font-size:11px;color:#666;margin-top:3px;">since Mon YYYY</div>
  <span style="display:inline-block;margin-top:8px;font-size:10px;padding:2px 10px;border-radius:10px;BADGE_STYLE;font-weight:600;">LABEL</span>
</div>
```

Badge styles:
- PhD: `background:#fde8f0;color:#c0306a`
- M2 / Master: `background:#d4f5e4;color:#176b3a`
- Engineer: `background:#dce8f7;color:#1a4f8a`
- PI: `background:#ddf4ed;color:#0f6e56`

`data-idx` must be the 0-based position of the card in the grid (0 = first card). Update if inserting in the middle.

Photo: upload to `assets/images/team/`. If no photo, use the grey SVG avatar:
```html
<svg viewBox="0 0 72 72" xmlns="http://www.w3.org/2000/svg"
     width="72" height="72" style="border-radius:50%;background:#e8f0f0;display:block;margin:0 auto;">
  <circle cx="36" cy="23" r="13" fill="#a0aaa8"/>
  <path d="M16 72 Q16 48 36 48 Q56 48 56 72" fill="#a0aaa8"/>
</svg>
```

### 2. Add a bio panel after `</div>` closing the team-grid, before the closing jumbotron `</div>`

```html
<div class="reveal-panel" id="bio-KEY">
  <div class="rp-arrow"></div>
  <button class="rp-close" onclick="event.stopPropagation();closeTeam()">×</button>
  <div class="rp-name">Full Name</div>
  <div>Bio text goes here.</div>
</div>
```

### 3. When moving someone to Alumni

Remove their card and bio panel. Add a line in the Alumni jumbotron:
```html
<p style="margin-bottom:5px;"><strong>Full Name</strong> — What they are doing now</p>
```

---

## Adding / Moving a Publication

Edit **`publications/index.html`**.

The page has two `<ol class="bibliography" reversed="reversed">` lists:
- First one: **Preprints** (after `<h3 id="preprints">`)
- Second one: **Refereed journal articles** (after `<h3 id="refereed-journal-articles">`)

Order of `<li>` elements in HTML = visual order. The `reversed` attribute makes numbers count down automatically — no manual numbering needed.

**To add a new preprint**, insert a `<li>` at the top of the preprints `<ol>`:
```html
<li>
<div class="text-justify">
  <span id="CITEKEY">Authors. (YEAR). <i>Title</i>. <i>Journal/arXiv</i>.</span>
</div>
  <a href="URL" target="_blank" style="display:inline-block;font-size:11px;padding:2px 9px;border-radius:12px;background:#fef3d0;color:#7a5000;text-decoration:none;margin:2px 2px 2px 0;font-weight:500;">ArXiv</a>
</li>
```

**To mark a PhD student's name in pink** use:
```html
<span class="highlight-phd">Surname, F.</span>
```

**To mark a Master student's name in green** use:
```html
<span class="highlight-master">Surname, F.</span>
```

**To bold your own name** use:
```html
<b>Ciandrini, L.</b>
```

**When a preprint is accepted**, move its `<li>` from the preprints list to the refereed articles list (in the right year position), and update the citation text to include journal/volume/pages.

---

## Deploying to GitHub Pages

After editing files locally:

```bash
git add -A
git commit -m "your message"
git push
```

GitHub Actions then runs automatically (~1–2 minutes) and the live site at **lciandrini.github.io** updates. You can monitor progress at: `https://github.com/lciandrini/lciandrini.github.io/actions`
