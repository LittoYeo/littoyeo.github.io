# Site deployment

## What the workflow does

The GitHub Actions workflow at [.github/workflows/deploy-jekyll.yml](.github/workflows/deploy-jekyll.yml#L1) builds this Jekyll site using Bundler and `jekyll build`, then publishes the generated `_site` contents to the `main` branch. This means the workflow will overwrite files on `main` with the generated site output.

## Important notes

- This repository uses the free GitHub Actions tier for public repositories; the workflow will run without extra billing for a public repo.
- The workflow pushes the built site to `main`. If you want a non-destructive deploy target, change `publish_branch` to `gh-pages` in the workflow and set GitHub Pages to serve from `gh-pages`.
- A backup of the original root `index.html` and `index.css` is saved in `root-backup/`.

## Local build & test

To build and preview the site locally:

```bash
gem install bundler
bundle install
bundle exec jekyll serve
```

Visit `http://127.0.0.1:4000` to preview the site locally.

## Reverting or changing behavior

- To stop the workflow overwriting `main`, edit [.github/workflows/deploy-jekyll.yml](.github/workflows/deploy-jekyll.yml#L1) and set `publish_branch: gh-pages`.
- To remove the workflow entirely, delete the file above and push the change.

If you'd like, I can switch the workflow to publish to `gh-pages` instead, or add a protective step to avoid overwriting specific files.
This is a READEME.md file for littoyeo.github.io

This site has 2 main portions:
1) The index page which hosts a Tarot reading section and my links
2) The blog powered by Jekyll