# Launchpad Entrepreneurial Society website

Website for Launchpad Entrepreneurial Society, a youth-run nonprofit in Vancouver running free case competitions, hackathons, school clubs and volunteer programs for high school students.

The design, animations and pixel-dither image effect come from a static mirror of a Next.js site; all copy has been rewritten for Launchpad. There is no build step: the repo is served as plain files.

## Pages

| URL | File | Content |
| --- | --- | --- |
| `/` | `index.html` | Home: mission, initiatives, stats, featured speakers, FAQ |
| `/who` | `who.html` | Who it’s for |
| `/where` | `where.html` | Where we are (Vancouver) |
| `/agenda` | `agenda.html` | Initiatives: Summit, Tyche Cup, Clubs, Volunteer |
| `/stan` | `stan.html` | Who we are |

`vercel.json` turns on `cleanUrls` (so `/who` serves `who.html`) and redirects the old `/apply` and `/legal/*` URLs to the home page.

## Editing the text

Each page stores its text twice: in the HTML and in the React data embedded in the page (`self.__next_f.push(...)`), which React uses when the page loads. Both copies have to change together, or React puts the old text back.

All copy changes live in `tools/les_content.py`. To change wording, edit that file and rebuild from the original mirror:

```sh
git checkout 3e4e675 -- index.html who.html where.html agenda.html stan.html _next
python3 tools/les_content.py
```

The script stops without saving anything if a phrase it expects isn't found. Page-wide CSS overrides (hidden Apply buttons, footer links, extra FAQs) are in `tools/les.css` and get appended by the script.

## Images

- `img/` — photos (dithered at runtime by the site's own script), including `gabriel-morgan.jpg` and the two “To be announced” speaker placeholders
- `brand/launchpad-lockup.png` — header logo; `icon.svg`, `favicon.ico`, `apple-icon.png` — site icons

## Run locally

```sh
npx serve .
```
