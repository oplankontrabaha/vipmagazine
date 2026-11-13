# OKB Magazine + Accomplishment — public page

The public, read-only **Oplan Kontra Baha** showcase: regions → sites → waterways
with their accomplishment, the map of waterways, and the photo gallery, on the
two-screen "duo" device. No sign-in.

Live at **https://oplankontrabaha.github.io/vipmagazine/**

## How it works

| Part | Where | What it does |
|---|---|---|
| `index.html` (this repo) | GitHub Pages | The page. It asks the Apps Script backend for data over a small JSON API. |
| `Code.gs` (Apps Script project) | Google | Reads the OKB SSOT and the photo-uploads sheet, caches the results, and answers `…/exec?api=core` and `…/exec?api=photos`. It also still serves the same page itself at `…/exec`, for anything that embeds that link. |

The backend link is the `API_BASE` constant near the top of the script in
`index.html`. If the Apps Script deployment is ever recreated (new `/exec` ID),
change that one line.

## Links

```
https://oplankontrabaha.github.io/vipmagazine/                                     opens on the default waterway
https://oplankontrabaha.github.io/vipmagazine/?region=region-vi                    a region
https://oplankontrabaha.github.io/vipmagazine/?region=region-vi&waterway=buntatala-creek   a waterway
https://oplankontrabaha.github.io/vipmagazine/region-vi/buntatala-creek            same, path style (404.html redirects it)
```

As you browse, the address bar follows the selection, so any view can be copied
and shared, and Back / Forward step through what was looked at.

## Files

- `index.html` — the page (also pasteable into the Apps Script project as its `index.html`; it detects where it runs).
- `404.html` — turns path-style links into `?region=…&waterway=…`.
- `README.md` — this guide.

## Updating

- Page changes: edit `index.html` here and commit; Pages republishes in about a minute.
- Data or API changes: edit `Code.gs` in Apps Script → Deploy → Manage deployments → ✎ → New version (same link).
- The `warmPublicCache` 10-minute trigger in Apps Script keeps the figures fresh for both the page here and the one at `/exec`.
