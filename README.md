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

Each post is a folder (a Hugo "page bundle") with its screenshots next to it:

```
content/blog/my-new-post/
  index.md
  screenshot-1.png
```

Front matter:

```yaml
---
title: "Game #2 Devlog #1: The Idea"
date: 2026-11-01T10:00:00Z
slug: "game-2-devlog-1"
summary: "One or two sentences for cards and link previews."
tags: ["devlog", "game 2"]
game: "game-2"          # optional: links the post to a game page (its folder name)
cover: "screenshot-1.png" # optional: card / social image from this folder
---
Post body in Markdown. Images: ![Alt text](screenshot-1.png)
```

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

## Layout

| Path | What it is |
|---|---|
| `hugo.toml` | Site title, tagline, menu, URLs |
| `content/` | Home, About, games and blog posts |
| `layouts/` | Templates (home, lists, posts, game pages) |
| `assets/css/main.css` | All styling |
| `static/` | Files copied as-is: favicon and playable game builds |
