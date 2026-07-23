# carlosrabelo.com.br

Portuguese personal site and blog of Carlos Rabelo — technology, programming, open source, and public-sector IT.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Hugo](https://img.shields.io/badge/Hugo-0.164.0-blue.svg)](https://gohugo.io/)

## Highlights

- Hugo Extended static site with a custom minimal theme
- Portuguese content with Atom and JSON feeds
- Open Graph, JSON-LD, and sitemap for SEO
- Deploy to GitHub Pages on every push to `master`

## Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) **0.164.0** (or compatible)
- Dart Sass (required by Hugo SCSS pipelines)

## Installation

```bash
git clone https://github.com/carlosrabelo/carlosrabelo.com.br.git
cd carlosrabelo.com.br
```

Install Hugo Extended matching the version in `.github/workflows/hugo.yml`.

## Usage

Local preview:

```bash
hugo server -D
```

Production build:

```bash
hugo --minify --baseURL "https://carlosrabelo.com.br/"
```

Output lands in `public/`.

### Optional: Utterances comments

1. Install the [Utterances](https://utteranc.es/) GitHub App on this repository.
2. In `config.toml`, uncomment `params.comments.githubRepo`.

## Project Layout

```
content/           Site content (posts, codes, about)
themes/mytheme/    Custom Hugo theme (layouts, SCSS, static assets)
static/            Site-wide static files (CNAME)
archetypes/        Content archetypes
.github/workflows/ GitHub Pages deploy
```

## Development

- `hugo server -D` — live reload with drafts
- `hugo --minify` — production build
- `hugo --printPathWarnings` — surface path issues (used in deploy)

Deploy runs on push to `master`.

Content markdown filenames stay in English.

English version: [carlosrabelo.com](https://carlosrabelo.com/).

## License

Site content and repository: [MIT](LICENSE).

Theme (`themes/mytheme`): MIT — based on work by Calvin Tran, with modifications by Carlos Rabelo. See [themes/mytheme/LICENSE](themes/mytheme/LICENSE).
