# ray of sunshine

A static site: one Python script, one stylesheet, and a folder of markdown.

```bash
pip install markdown pyyaml
python build.py && python -m http.server -d dist 8000
```

Then open http://localhost:8000.

```
rayofsunshine/
├── build.py          # generator and HTML templates
├── content/
│   ├── img/          # images embedded in posts
│   ├── macro/        # essays
│   ├── micro/        # snapshots
│   ├── art/          # objects
│   └── burgundy/     # photos
├── static/
│   ├── style.css
│   └── *.png         # one landing icon per section
└── dist/             # generated output (gitignored)
```

## Sections

Each `content/<key>/` folder is a section. `SECTIONS` at the top of `build.py` sets its `kind`:

- `list` — date-sorted links (`macro`)
- `feed` — title, date, and body inline (`micro`)
- `gallery` — cards that link to a page (`art`)
- `images` — image files only, no titles or pages (`burgundy`)

The home page links to each section using the icon named in `SECTION_ICONS`. The intro line lives in `render_landing()`.

## Posts

Drop a `.md` file in `content/macro/`, `content/micro/`, or `content/art/`. Front matter is optional:

```markdown
---
title: My Post Title
date: 2026-06-01
slug: custom-url-slug   # defaults to the filename
cover: img/my-photo.jpg # art thumbnail; also shown at the bottom of the post
---

Body in **markdown**.
```

- No `title` → taken from the filename.
- No `date` → the file's modification time.
- Pages are written to `dist/<section>/<slug>/`.
- `#` headings in the body become the table of contents.
- `^[note]` is a sidenote.
- A hex color in prose (`#c70000`) becomes a swatch.
- `![[img/photo.jpg]]` or `![[img/photo.jpg|600]]` embeds a file from `content/img/`.

For `art`, the card image is `cover` if set, otherwise the first image in the post.

For `burgundy`, drop image files (`.jpg`, `.png`, `.gif`, `.webp`, `.avif`) in `content/burgundy/`.

## Deploy

`dist/` is plain static files. Set `CUSTOM_DOMAIN` in `build.py` to write `dist/CNAME` for a GitHub Pages custom domain.

To change the site, edit `SITE_TITLE`, `SECTIONS`, `SECTION_ICONS`, and `MD_EXTENSIONS` at the top of `build.py`. The HTML is in the template strings just below.
