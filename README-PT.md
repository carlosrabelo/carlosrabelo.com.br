# carlosrabelo.com.br

Site pessoal e blog de Carlos Rabelo — tecnologia, programação, open source e TI no serviço público.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Hugo](https://img.shields.io/badge/Hugo-0.164.0-blue.svg)](https://gohugo.io/)

## Destaques

- Site estático com Hugo Extended e tema mínimo customizado
- Conteúdo em português com feeds Atom e JSON
- Open Graph, JSON-LD e sitemap para SEO
- Deploy no GitHub Pages a cada push em `master`

## Pré-requisitos

- [Hugo Extended](https://gohugo.io/installation/) **0.164.0** (ou compatível)
- Dart Sass (necessário para os pipelines SCSS do Hugo)

## Instalação

```bash
git clone https://github.com/carlosrabelo/carlosrabelo.com.br.git
cd carlosrabelo.com.br
```

Instale o Hugo Extended na versão indicada em `.github/workflows/hugo.yml`.

## Uso

Pré-visualização local:

```bash
hugo server -D
```

Build de produção:

```bash
hugo --minify --baseURL "https://carlosrabelo.com.br/"
```

A saída fica em `public/`.

### Opcional: comentários Utterances

1. Instale o app [Utterances](https://utteranc.es/) neste repositório.
2. Em `config.toml`, descomente `params.comments.githubRepo`.

### Opcional: headers de segurança

O GitHub Pages não permite headers customizados. Se o site estiver atrás do Cloudflare, veja [docs/security-headers.md](docs/security-headers.md).

## Estrutura do Projeto

```
content/           Conteúdo do site (posts, codes, about)
themes/mytheme/    Tema Hugo customizado (layouts, SCSS, assets)
static/            Arquivos estáticos do site (CNAME)
archetypes/        Arquétipos de conteúdo
docs/              Documentação extra
.github/workflows/ Deploy no GitHub Pages
```

## Desenvolvimento

- `hugo server -D` — live reload com rascunhos
- `hugo --minify` — build de produção
- `hugo --printPathWarnings` — alerta de caminhos (usado no deploy)

O deploy roda no push para `master`.

Nomes de arquivos markdown de conteúdo ficam em inglês, mesmo com o corpo em português.

## Licença

Conteúdo do site e repositório: [MIT](LICENSE).

Tema (`themes/mytheme`): MIT — baseado no trabalho de Calvin Tran, com modificações de Carlos Rabelo. Veja [themes/mytheme/LICENSE](themes/mytheme/LICENSE).
