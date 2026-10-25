# The Hedge – band website

Live 80s pop & rock from the Wirral. A simple one-page static site for gig-goers
(`index.html` + `style.css` + `assets/`), hosted free on GitHub Pages.

Booking enquiries: thehedgeband@proton.me

## Going live (one-time)

Settings → Pages → Source: **Deploy from a branch** → Branch: **main**, folder **/ (root)** → Save.
The site will then be at https://johncomish-byte.github.io/the-hedge-site/

## Adding or removing a gig

In `index.html`, find the `GIG CARD: copy from here` comment inside the
"Next gigs" section. Copy everything down to `GIG CARD: end`, paste it below,
and change the date, venue, town and details. The poster block
(`<a class="gig-poster"> ... </a>`) is optional – delete it if there is no poster.
Remove a card once the gig has happened.

## Placeholders still to fill in (search index.html for `TODO`)

- **Gig details** – start time / entry price, and an optional ticket or Facebook event link.
- **Video** – replace the `video-placeholder` block with a YouTube embed (instructions in the comment).
- **Socials** – replace each `href="#"` with the band's real pages; delete unused ones.
- **Sharing preview** – once the site has its final web address, add `og:url` and make the
  `og:image` URL absolute.

## How images are stored

The booking bot's GitHub connector can only commit text, so images are committed as
base64 text in `assets-b64/<name>.b64`. The workflow `.github/workflows/decode-assets.yml`
runs on every push that touches `assets-b64/`, decodes them into `assets/<name>`
and commits the real image files back. To add an image this way:

```bash
base64 -w 76 my-photo.jpg > assets-b64/my-photo.jpg.b64
```

You can also just upload images straight into `assets/` with GitHub's web
"Add file → Upload files" button – that works too.

## Local preview

```bash
python3 -m http.server
# then open http://localhost:8000
```
