# Short Lead Studio website

Static site for [shortleadstudio.co.uk](https://shortleadstudio.co.uk), served by GitHub Pages from `main`.

- `index.html` – the one-page site
- `privacy.html`, `404.html`
- `assets/site.css` – all styles (brand tokens at the top)
- `assets/fonts/` – self-hosted Bricolage Grotesque and IBM Plex (SIL Open Font License)
- `assets/media/` – clips (540px wide, H.264, about 1–2 MB each) and poster frames
- `assets/brand/` – logo, favicons, social share image

## Updating clips

Re-encode a new clip to match the others:

```
ffmpeg -i source.mp4 -vf scale=540:-2 -c:v libx264 -crf 26 -preset slow -c:a aac -b:a 96k -movflags +faststart assets/media/name.mp4
ffmpeg -ss 3 -i source.mp4 -frames:v 1 -vf scale=540:-2 -q:v 4 assets/media/name.jpg
```

## Domain

Add a `CNAME` file containing `shortleadstudio.co.uk` when the domain goes live. DNS lives at GoDaddy: apex `A` records to GitHub Pages and `www` `CNAME` to `neil-paddock-tech.github.io`. Never change the `MX`, SPF or DKIM records; they carry Google Workspace email.
