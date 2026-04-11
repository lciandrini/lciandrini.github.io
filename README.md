# lciandrini.github.io

Personal academic website of **Luca Ciandrini**, Maître de Conférences at the University of Montpellier and the Institut Universitaire de France (IUF).

Live at: **https://lciandrini.github.io**

---

## Structure

| File / Folder | Description |
|---|---|
| `index.html` | Homepage — group intro, photo, news (latest 3 items) |
| `about/index.html` | About page — CV, bio |
| `publications/index.html` | Full publication list |
| `research/index.html` | Research themes |
| `team/index.html` | Current members and alumni |
| `teaching/index.html` | Teaching |
| `allnews.html` | Full news archive |
| `directions/index.html` | How to reach CBS |
| `hid-group-organisation/index.html` | Internal group organisation |
| `assets/main.css` | Main stylesheet (all custom styles appended at the bottom) |
| `assets/ref.bib` | BibTeX reference file (informational — does not auto-generate the publications page) |
| `assets/images/` | Photos, logos, SVG figures |
| `EDITING_GUIDE.md` | How to add news, team members, and publications |

## Deployment

The site is deployed via GitHub Actions on every push to `main`.
Build time: ~1 minute. Monitor at: https://github.com/lciandrini/lciandrini.github.io/actions

To update the site locally and deploy:

```bash
# Preview locally
bundle exec jekyll serve --port 4001

# Commit and push
git add -A
git commit -m "your message"
git push
```

## Notes

- The site is **static HTML** — Jekyll is used only to package files for GitHub Pages, not to generate content from templates.
- The publications page is hand-maintained HTML. The `.bib` file is a reference copy but does not drive the page automatically.
- See `EDITING_GUIDE.md` for step-by-step instructions on adding news, team members, and publications.
