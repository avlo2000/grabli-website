# GRABLI website

A compact English-language product page based on the approved GRABLI one-pager,
using the selected Technical Charcoal design: dark charcoal, cyan accents and the
original GRABLI mark and sensor-module illustration.

The public page includes the product overview, supported FPV platforms,
physics-aware AI positioning, early validation, pilot testimonial, captioned C2
mission demo, project demo, manufacturing milestones and existing WhatsApp /
Signal contact links.
Financial figures, operating-band specifications, internal NDA relationships and
individual attribution are not included. Original presentations and one-pager
PDFs must not be uploaded alongside the website.

## Preview

Open `index.html` directly in a browser. For a local web-server preview, run:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`. The C2 mission video is included in `assets/`
and plays locally, with English captions, at 2× speed (40.65 seconds). It uses
native playback controls and loads only when played. The separate YouTube
project demo requires internet access and may refuse embedded playback from
local file URLs; its direct YouTube link remains available.

## Publish with the included script

Requirements: Python 3.9+ and the official [GitHub CLI](https://cli.github.com/).
The CLI must be signed into the GitHub account that owns the site.

```sh
gh auth login --hostname github.com
python3 publish.py --repo grabli-website
```

For a new repository, confirm the public publication when prompted. If the
repository already exists under the authenticated account, the script updates
`index.html`, `.nojekyll`, this README and the C2 video and poster in `assets/`.
It enables GitHub Pages from the default branch root when needed, then checks
the deployment and reports
`LIVE and verified` only after a successful HTTP response containing the page.

For a repository it created, a local state file allows the script to resume and
refuses to create a replacement if that repository disappears. The state file
contains only the repository name and numeric ID; it is not uploaded. No token is
requested, printed or stored by this script.

A local-only preflight check is available:

```sh
python3 publish.py --dry-run
```

If account or organization policy prevents configuring Pages, the site files
remain intact and the script reports the error rather than claiming deployment.

## Publish using GitHub's website instead

1. Create a new public repository, for example `grabli-website`.
2. Upload `index.html` and the `assets/` directory into the repository root and
   commit them. Keep the asset filenames and directory structure unchanged.
   The optional `.nojekyll` file disables unnecessary static-site processing.
3. In **Settings → Pages**, select **Deploy from a branch**, choose the default
   branch and **/(root)**, then save. Open the site URL shown by GitHub after the
   deployment completes.

Official documentation:
- [Configure a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [GitHub Pages REST API](https://docs.github.com/en/rest/pages/pages)
- [Repository contents REST API](https://docs.github.com/en/rest/repos/contents)

## Edit

All copy, styles and the small demo-loader script live in `index.html`. The logo
and module illustration are embedded as image data, so there is no build step,
framework, package installation or font download. The C2 video and poster use
relative paths in `assets/`, so the page works at repository subpaths without
modification.

Search for the HTML section IDs `product`, `technology`, `validation`, `demo` and
`contact` to find the corresponding text. The C2 player is `c2-demo-video`; its
video is `assets/grabli-c2-demo-2x.mp4` and its preview image is
`assets/grabli-c2-demo-poster.jpg`. The English captions are part of the video.
The YouTube ID is `Si6ZT7ueMGU`. Its player uses youtube-nocookie.com and is not
loaded until the visitor presses play.
No analytics, signup form or site-owned cookies have been added.

## Validation performed on the supplied files

- Desktop, tablet and mobile layouts checked at widths 1440, 768, 390 and 320 px.
- No horizontal overflow, broken inline images or JavaScript errors detected.
- All in-page anchors resolve; all images have alternative text attributes.
- No third-party network request occurs until the demo is activated or an
  external contact link is followed.
- C2 video playback, seeking, local assets and responsive layout checked locally.
- YouTube demo-button interaction checked with the video response mocked. Actual
  YouTube playback and third-party contact destinations have not been tested.
- Production deployment has **not** been performed in the authoring session.

The project copy is based on the supplied materials; product claims and
third-party relationships were not independently verified. No confidential
technical implementation, measurement dataset or original source document is
included in this package.
