# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the Traditional Chinese (繁體中文) translation of "Mastering the Lightning Network" by Andreas M. Antonopoulos, Olaoluwa Osuntokun, and René Pickhardt. The book is written in AsciiDoc format and deployed as HTML to GitHub Pages.

## Build Commands

### Build HTML locally
```bash
gem install asciidoctor asciidoctor-diagram rouge
asciidoctor -D docs -a toc=left -a toclevels=3 -a sectnums -a icons=font -a source-highlighter=rouge -a imagesdir=images -a stem=latexmath -o index.html zh-TW/book.adoc
```

### Docker environment (for Lightning Network examples)
```bash
cd code/docker
make pull          # Pull all containers
make build         # Build all containers (bitcoind, lnd, c-lightning, eclair)
docker-compose up  # Run the demo network
```

## Repository Structure

- **Root `.asciidoc` files**: Original English source chapters (01-17) and appendices
- **`zh-TW/`**: Traditional Chinese translation in `.adoc` format
  - `book.adoc`: Main entry point that includes all chapters
- **`code/docker/`**: Docker containers for running Lightning Network demos with bitcoind, LND, c-lightning, and Eclair
- **`images/`**: All book diagrams and figures
- **`docs/`**: Generated HTML output for GitHub Pages deployment

## AsciiDoc Style Guidelines

- One sentence per line (for easier diff review)
- Unix line endings (LF, not CRLF)
- No trailing whitespace or tabs
- Use spaces for indentation
- Headings: Level 2 (`==`) for chapters, level 3+ for sections
- Include unique anchors: `[[anchor_name]]` above headings
- Spell out acronyms on first use with acronym in parentheses: "Hash Time-Locked Contract (HTLC)"

## Deployment

Pushing to `develop` branch triggers GitHub Actions workflow that:
1. Builds HTML using Asciidoctor with Rouge syntax highlighting
2. Deploys to GitHub Pages at https://lnbook-zh.doge.tg/

## CI Checks (.travis.yml)

Travis CI validates:
- No Windows-style line endings
- No trailing whitespace
- No tabs in content
- No duplicate consecutive words
- Files end with newline
- No multiple consecutive blank lines
- Spelling (codespell, misspell)
