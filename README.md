# dsa-explain

Visual, interactive explainers for data structures and algorithms —
built with [Quarto](https://quarto.org).

This repository is currently a **scaffold**: the site shell (navigation,
design system, module grid) is complete, and each module is a
placeholder page waiting to be written.

## Structure

```
dsa-explain/
├── _quarto.yml          # site config: nav, footer, theme
├── theme.scss           # design system (colors, type, layout rules)
├── styles.css           # font loading + a11y rules
├── favicon.svg
├── index.qmd            # homepage: hero + module grid
├── about.qmd            # project background, license, attribution
└── modules/
    ├── 00-arrays-strings/index.qmd
    ├── 01-linked-lists/index.qmd
    ├── ...
    └── 09-dynamic-programming/index.qmd
```

Each module lives in its own numbered folder so a module can grow into
multiple pages (e.g. `modules/06-graphs/bfs.qmd`,
`modules/06-graphs/dijkstra.qmd`) without reshuffling the site.

## Local preview

1. Install Quarto: <https://quarto.org/docs/get-started/>
2. From the repo root, run:

   ```bash
   quarto preview
   ```

   This opens a live-reloading local preview.

3. To produce the static site without previewing:

   ```bash
   quarto render
   ```

   Output goes to `_site/` (git-ignored).

## Writing a module

Replace the placeholder content in a module's `index.qmd`, keeping the
YAML front matter (`title`, `description`) so the homepage card and
page `<title>` stay accurate. Interactive visuals can be built as:

- [Observable JS](https://quarto.org/docs/interactive/ojs/) blocks
  (` ```{ojs} `) for D3-style data-driven visuals rendered at build time, or
- a plain HTML/CSS/JS `<div>` + `<script>` embedded directly in the
  `.qmd` for hand-built animations.

Add a new module by creating `modules/NN-slug/index.qmd` and adding a
matching `.module-card` link in `index.qmd`.

## Deploying to GitHub Pages

This repo includes `.github/workflows/publish.yml`, which renders the
site with Quarto and publishes it to the `gh-pages` branch on every
push to `main`.

To enable it:

1. Push this repository to GitHub as `dsa-explain`.
2. In **Settings → Pages**, set the source to the `gh-pages` branch
   (the workflow creates this branch on its first successful run).
3. Update `site-url` in `_quarto.yml` and the GitHub links in
   `_quarto.yml` / `about.qmd` from `your-username` to your actual
   GitHub username or org.

The site will be published at `https://<your-username>.github.io/dsa-explain/`.

## License and attribution

- **Code** (Quarto config, SCSS/CSS, page scaffolding) in this
  repository: see [`LICENSE`](LICENSE) (MIT).
- **Written content**, once modules are filled in, is intended to be
  shared under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
  unless noted otherwise on a given page — update this if you choose
  differently.

The idea for this project — short, visual, self-contained explainers
— was inspired by [MLU-Explain](https://mlu-explain.github.io/)
([source](https://github.com/aws-samples/aws-mlu-explain)). No code,
styling, illustrations, or copy from that project were copied into
this one; the design system here (palette, type, grid, and the
"graph paper" motif) was built independently for this project. See
[`about.qmd`](about.qmd) for the fuller attribution note that ships
on the live site.
