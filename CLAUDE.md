# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

`rk-blog` is a content/data store, not an application. It holds blog post
content for **RK Security System** (a home security equipment/installation
business in Kosi Kalan, Mathura, India). There is no build system, package
manager, source code, tests, or CI in this repo — it is consumed by an
external system (a website, CMS, or automation pipeline) that reads
`blog.json` and the `images/` directory.

Because there is no code, there are no build/lint/test commands to run here.

## Structure

- `blog.json` — a JSON array of blog post entries. This is the entire
  content database; new posts are appended to the array.
- `images/` — intended to hold images associated with blog posts (currently
  empty aside from `.gitkeep`). Existing entries reference placeholder
  images hosted on `placehold.co` rather than files in this directory.
- `README.md` — just the repo title, no additional content.

## `blog.json` entry schema

Each element of the array is an object with these fields:

- `title` — post title (Hinglish/Hindi-English mix, matches the business's
  marketing voice).
- `slug` — URL-safe slug derived from the title.
- `tag` — a single category tag (e.g. `"Smart Lock"`).
- `blog_html` — the full post body as an HTML string (headings, lists,
  bold text, etc.) written in Hinglish, ending with a call-to-action
  mentioning "RK Security System" and its location.
- `gmb_caption` — a shorter, emoji-heavy caption formatted for a Google My
  Business / social post, including a hashtag block at the end.
- `image_prompt` — an English text-to-image prompt describing the
  illustrative image for the post (realistic photography style, no text
  overlay, no explicit brand names in the image itself).
- `date` — human-readable date string, e.g. `"08 July 2026"`.
- `image` — URL to the post's image. Currently a `placehold.co` placeholder;
  a real generated/uploaded image (matching `image_prompt`) would replace
  this and presumably live under `images/`.

## Conventions to follow when adding a post

- Append new post objects to the end of the `blog.json` array — don't
  reorder or rewrite existing entries.
- Match the existing tone: Hinglish marketing copy, business name "RK
  Security System", location "Kosi Kalan, Mathura", product lines like
  CP Plus, Hikvision, Dahua.
- Keep `blog_html` and `gmb_caption` consistent with each other (same
  topic/CTA) but distinct in format — `blog_html` is structured HTML,
  `gmb_caption` is a flat, emoji/hashtag-heavy social caption.
- Git history shows posts are committed with messages of the form
  `Auto blog: <title>`, suggesting entries are added by an automated
  process — follow that commit message convention when adding a post here.
