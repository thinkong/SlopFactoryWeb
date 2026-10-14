# Slop Factory website

The Slop Factory studio site: **Our Games** and the **Blog** (devlogs). Built with [Hugo](https://gohugo.io/) and deployed to GitHub Pages by GitHub Actions. No theme dependency, no Node, no WordPress.

## Run it locally

Install Hugo (extended, v0.146 or newer), then:

```sh
hugo server
```

Open http://localhost:1313. Edits reload live.

## Publish to GitHub Pages (one-time setup)

1. Create a GitHub repo and push this folder to its `main` branch.
   - Name it `<your-username>.github.io` for a site at `https://<your-username>.github.io/`, or use any name for `https://<your-username>.github.io/<repo>/`. Both work; links are relative to the base URL.
2. In the repo, go to **Settings → Pages → Build and deployment** and set **Source** to **GitHub Actions**.
3. Push to `main`. The workflow in `.github/workflows/hugo.yml` builds and deploys the site. The URL appears in the **Actions** run and under **Settings → Pages**.

Custom domain: add it under **Settings → Pages → Custom domain**, and add a `static/CNAME` file containing the domain.

## Write a blog post

Each game gets **one** devlog post covering how it was made. Each post is a folder (a Hugo "page bundle") with its screenshots next to it:

```
content/blog/my-new-post/
  index.md
  screenshot-1.png
```

Front matter:

```yaml
---
title: "Game Name Devlog: What We Built and Why"
date: 2026-11-01T10:00:00Z
slug: "game-name-devlog"
summary: "One or two sentences for cards and link previews."
tags: ["devlog", "game name"]
game: "game-name"       # optional: links the post to a game page (its folder name)
cover: "screenshot-1.png" # optional: card / social image from this folder
---
Post body in Markdown. Images: ![Alt text](screenshot-1.png)
```

If a post replaces older ones, list their old URLs under `aliases:` in the front matter (e.g. `- /blog/old-post-slug/`) so the old links redirect to the new post.

Or scaffold one with `hugo new content blog/my-new-post/index.md`.

## Add a game

1. Put the game's built files (its `index.html`, JS, assets) in `static/games/<game>/play/`.
2. Create `content/games/<game>/index.md` with a cover image next to it:

```yaml
---
title: "Game Name"
slug: "game-name"
date: 2026-11-15T10:00:00Z
summary: "Short pitch for cards."
cover: "cover.png"
version: "1.0.0"
status: "Released"        # shows as a sticker on the card
platforms: ["Desktop browser", "Phone browser"]
controls: "How to play in one line."
play: "play/"             # relative path to the build; embedded on the page
---
Longer description, screenshots, credits.
```

Blog posts with `game: "<game slug>"` are listed on that game's page automatically.

## Korean (한국어) pages

English is the default and lives at `/`. Korean lives at `/ko/`. Every page's header has an **EN / 한국어** switcher that goes to the same page in the other language, or to that language's home page if there is no translation yet. You can add Korean without touching any template.

**Translate a page:** put a `.ko.md` file next to the English one, with the same folder and base name. Keep the same `slug` so the two versions link to each other.

| English | Korean | Korean URL |
|---|---|---|
| `content/_index.md` | `content/_index.ko.md` | `/ko/` |
| `content/about.md` | `content/about.ko.md` | `/ko/about/` |
| `content/games/_index.md` | `content/games/_index.ko.md` | `/ko/games/` |
| `content/blog/_index.md` | `content/blog/_index.ko.md` | `/ko/blog/` |
| `content/games/<game>/index.md` | `content/games/<game>/index.ko.md` | `/ko/games/<slug>/` |
| `content/blog/<post>/index.md` | `content/blog/<post>/index.ko.md` | `/ko/blog/<slug>/` |

In a page bundle, `index.ko.md` uses the same images as `index.md`, so you don't need to copy screenshots. To show a Korean screenshot, add it with `.ko` before the extension (`screenshot-1.ko.png`) and Hugo uses it on the Korean page. Copy the English front matter, then translate `title`, `summary`, `description`, `controls`, `status`, `platforms` and `tags`. Leave `slug`, `date`, `game`, `cover`, `version` and `play` unchanged. Keep `play: "play/"` as it is: the game build is shared, and the Korean page loads it from `/games/<game>/play/`.

**Translate the UI text** (menu, buttons, footer, ticker, dates): edit `i18n/ko.toml`. Each placeholder is the English text with a `# TODO ko` line above it. Replace the text inside the quotes and delete the `TODO` line. Keep the key names, HTML tags and `{{ .Something }}` placeholders unchanged. `i18n/en.toml` holds the English text. Add a new key to both files.

Korean pages use a Hangul font stack (Pretendard if installed, then Apple SD Gothic Neo, Malgun Gothic, Noto Sans KR), and long headings wrap between words, not in the middle of a word.

## Layout

| Path | What it is |
|---|---|
| `hugo.toml` | Site title, languages, menu, URLs |
| `i18n/` | UI text per language (`en.toml`, `ko.toml`), including tagline and description |
| `content/` | Home, About, games and blog posts (`*.ko.md` = Korean) |
| `layouts/` | Templates (home, lists, posts, game pages) |
| `assets/css/main.css` | All styling |
| `static/` | Files copied as-is: favicon and playable game builds |
