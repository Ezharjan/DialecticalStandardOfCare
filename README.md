# From Reviewable to Reviewed: A Dialectical Standard of Care for Nurse- and Physician-Facing Clinical AI

Project page for the paper by **Aizierjiang Aiersilan** (The George Washington University),
prepared for the **AAAI 2026 Fall Symposium Series**, symposium on *Agentic and Trustworthy AI
for Health and the Global AI-Ready Nursing Workforce* (AT-AI4H-NW 2026).

The paper argues that clinical AI oversight should be specified as a performed and recorded act
rather than an available capability. It proposes *dialectical review*, with four conditions
(independent prior, basis at decision-relevant granularity, recorded disposition, consequence
rule) and a rule for allocating responsibility among vendor, institution, and clinician.

## Links

| Button | Target | Note |
|---|---|---|
| arXiv | https://arxiv.org/abs/2606.00044 | The arXiv record is titled “Algorithmic Authority and the Clinical Standard of Care”. |
| Confab | https://cal.com/ezhar/30min | Scheduling link. |
| Slides | `A_Dialectical_Standard_of_Care_AizierjiangAiersilan_silides4AAAI2026FSS.pdf` | The talk slides (PDF), also embedded above the BibTeX. |
| Paper | https://aaai.org/conference/fall-symposia/2026-fall-symposium-series-2/ | Temporary: the AAAI 2026 Fall Symposium Series page. Replace with the paper URL after publication. |

Buttons render in the order of `links` in `config.json`.

## Slides

The talk slides are embedded above the BibTeX as a scrollable deck, with a link to the PDF
(`A_Dialectical_Standard_of_Care_AizierjiangAiersilan_silides4AAAI2026FSS.pdf`).
Each slide is a pre-rendered image in `static/images/slides/` (`slide-01.jpg` … `slide-40.jpg`,
1600 × 900). If the deck changes, regenerate the images and update `slides.count` in `config.json`:

```bash
pdftoppm -r 300 -scale-to-x 1600 -scale-to-y 900 -jpeg -jpegopt quality=88 \
  A_Dialectical_Standard_of_Care_AizierjiangAiersilan_silides4AAAI2026FSS.pdf static/images/slides/slide
```

`pdftoppm` names its output `slide-01.jpg`, `slide-02.jpg`, …, which matches
`"imagePattern": "static/images/slides/slide-{n}.jpg"` with `"pad": 2`. If you rename the PDF,
update `slides.file` as well.

## Editing the page

All page content (title, venue, authors, links, abstract, sections, tables, figure, slides,
BibTeX, footer) lives in `config.json` and is rendered at runtime by `static/js/render.js`.
`config.schema.json` provides autocomplete and validation in editors such as VS Code.
`site.title` is the plain-text title used for the browser tab and citation metadata;
`site.displayTitle` controls the two-line heading on the page.
Set `"enabled": false` on any section, link, block, or the slides to hide it without deleting it.

No poster is included. To add one, place an unencrypted `paper_poster.pdf` in the root, add
`"poster": { "enabled": true, "title": "Poster", "file": "paper_poster.pdf" }` to `config.json`,
and, if desired, a Poster button to `links`:

```json
{ "type": "poster", "label": "Poster", "icon": "fas fa-file-image", "url": "paper_poster.pdf", "enabled": true }
```

## Previewing locally

The page loads `config.json` with `fetch()`, which browsers block on `file://`. Serve the folder instead:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying (GitHub Pages)

1. Push this folder to a GitHub repository.
2. In **Settings → Pages**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The page goes live at `https://<user>.github.io/<repo>/`.

`__reference_materials/` (private paper and code sources used to build the page) is listed in
`.gitignore` and must never be published.

## Folder structure

```
index.html            Generic shell (loads render.js)
config.json           All page content
config.schema.json    Schema for config.json
favicon.ico           Tab icon
A_Dialectical_Standard_of_Care_AizierjiangAiersilan_silides4AAAI2026FSS.pdf   Talk slides (PDF)
static/
  css/index.css       Theme
  js/render.js        Renderer
  images/             Figure 1 (dialectical_review.png) and slides/ (slide-01.jpg … slide-40.jpg)
  webfonts/           Font Awesome fonts
```

## Credits

Layout adapted from the [Nerfies](https://github.com/nerfies/nerfies.github.io) academic
project page template (Bulma CSS, Font Awesome).
