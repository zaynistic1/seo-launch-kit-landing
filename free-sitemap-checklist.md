# Sitemap hygiene checklist

Run through this every time you publish or edit pages. Takes five minutes, prevents the silent indexing failures.

- [ ] **No BOM.** The file must not start with a UTF-8 byte-order mark. Check: `xxd sitemap.xml | head -1` — if it starts with `ef bb bf`, strip it (re-save as UTF-8 without BOM).
- [ ] **Absolute canonical URLs only.** Every `<loc>` is `https://` + the canonical version (matches your 301 rules — no `.html` variants if your canonicals are clean).
- [ ] **lastmod is honest.** Set `<lastmod>` to the date the page actually changed, and bump it on every content edit. Don't fake fresh dates on untouched pages.
- [ ] **No junk URLs.** No `404.html`, no drafts, no `noindex` pages, no URLs that 404 or redirect.
- [ ] **Submitted everywhere.** Google Search Console → Sitemaps, and Bing Webmaster Tools → Sitemaps. Both, not just Google — Bing feeds IndexNow's ecosystem too.
- [ ] **Spot-check the live file.** Open `https://yoursite.com/sitemap.xml` in a browser after deploy and confirm it reflects your latest edits.
