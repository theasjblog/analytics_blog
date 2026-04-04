# ASJ Analytics and Software

This repository contains a Quarto website used as a programming-focused blog. The site is built from standalone pages at the repo root plus post folders under `posts/`.

## What Is In This Repo

- `index.qmd`: the home page, configured as a Quarto listing of blog posts.
- `about.qmd`: the about page.
- `posts/`: one folder per post, usually with an `index.qmd` and, when needed, a local `img/` folder.
- `img/`: shared site assets such as the logo.
- `_quarto.yml`: the main site configuration.
- `styles.css`: site-level CSS overrides.
- `drafts/` and `medium_to_blog/`: working areas for draft content and conversions that are not part of the published site.

## How The Site Works

This is a Quarto website project.

- Quarto reads `_quarto.yml` for site configuration.
- The home page uses Quarto listing functionality to show posts from `posts/`, sorted by date descending.
- Each post lives in its own folder under `posts/`.
- Post card thumbnails on the home page are best driven by front matter `image:` metadata.
- Local post images should live next to the post in that post's `img/` folder and be referenced relatively.

The project is explicitly configured to render only:

- `index.qmd`
- `about.qmd`
- `posts/`

That means `README.md` is not rendered as part of the blog.

## Repo Patterns Worth Noting

- Posts are folder-based: `posts/YYYY-MM-DD_slug/index.qmd`.
- Many older posts use local images in `posts/.../img/`.
- Some imported drafts use remote images. Those work for published pages, but front matter `image:` should be set if you want a reliable listing thumbnail.
- Draft conversions may exist outside `posts/`; those are staging files, not published content.
- `.Rprofile` conditionally activates `renv` only when `renv/activate.R` exists, to avoid render failures in environments without the local `renv` bootstrap files.

## Render

Use this clean render command from the repo root:

```sh
rm -rf _site .quarto && quarto render
```

## Updating Content

To add a new published post:

1. Create a new folder under `posts/` using the existing date-based naming pattern.
2. Add an `index.qmd` with front matter including at least `title`, `description`, `date`, and `categories`.
3. Add `image:` in front matter if you want the post card image to appear reliably on the home page.
4. Place any local images in a sibling `img/` folder.
5. Run the render command above and confirm the post appears correctly on the home page and the post page.
