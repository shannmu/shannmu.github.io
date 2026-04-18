# Repository Guidelines

## Project Structure & Module Organization

This repository is a Zola static site for `https://shannmu.github.io`.
Site configuration lives in `config.toml`. Markdown content lives under
`content/`: top-level pages such as `content/about.md` and `content/journal.md`
render as standalone pages, while writing series live in top-level section
directories such as `content/computer-tech/` and `content/daily-life/`.
Chinese is the default language; English translations use `.en.md` suffixes.
The active theme is `anemone`, stored as a Git submodule under
`themes/anemone`; avoid editing theme files directly unless the change is
intended to be theme-specific. GitHub Pages deployment is configured in
`.github/workflows/deploy.yaml`.

## Build, Test, and Development Commands

- `zola serve`: run a local development server with live reload.
- `zola build`: generate the production site into `public/`.
- `zola check`: validate the site, links, front matter, and templates without
  writing the full output.

There is no `package.json` or language package manager setup in this repository.
Use the Zola CLI directly. CI deploys on pushes to `main` and publishes the
built site to the `gh-pages` branch.

## Coding Style & Naming Conventions

Use TOML front matter delimited with `+++` in Markdown files. Prefer concise,
descriptive page titles, for example:

```toml
+++
title = "About"
+++
```

Name series entries with a date prefix and slug, for example
`content/computer-tech/YYYY-MM-DD-topic-slug.md`. Use the matching
`YYYY-MM-DD-topic-slug.en.md` file for English translations. Keep Markdown
readable with short sections, relative internal links where practical, and
fenced code blocks with language tags when showing code.

## Testing Guidelines

There is no dedicated automated test suite. Before opening a pull request, run
`zola check` and `zola build`. For content or layout changes, also run
`zola serve` and review the affected pages in a browser. Check that new posts
have valid front matter and that internal links resolve.

## Commit & Pull Request Guidelines

Recent commits use short, lower-case summaries such as `nightly update` and
simple imperative descriptions such as `modify config.toml to set theme`. Keep
commit messages brief and focused on one change.

Pull requests should include a short description, list affected pages or config
files, and mention the validation performed (`zola check`, `zola build`, or
manual preview). Include screenshots when a change affects visible layout or
theme behavior.

## Agent-Specific Instructions

Keep generated files out of version control unless they are intentionally part
of the site source. Do not commit `public/` output. Preserve the `themes/anemone`
submodule unless explicitly updating the theme.
