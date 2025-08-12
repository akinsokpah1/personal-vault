# BUILD.md — Reproducible build & vendoring

This project is intentionally static and minimal. Follow these steps to produce a reproducible site bundle.

## Recommended versions
- Node.js: 18.x (pin exact minor if you prefer)
- npm / yarn: match Node version
- libsodium: use `libsodium-wrappers` build v0.7.9 (or pin the exact version you test with)

## Vendoring libs
1. Download the `libsodium-wrappers.min.js` browser bundle and place it at the repository root next to `personal-vault-index.html`.
   - Example source: the official libsodium releases (`libsodium-wrappers.js`).
   - Pin the file version and keep a copy inside the repo (do NOT rely on external CDNs).

## Minimal build (no bundler)
This site is static — you can host it directly on GitHub Pages. Steps:
1. Create a new GitHub repo (private if you prefer). `git init` and add files.
2. Add `personal-vault-index.html`, `libsodium-wrappers.min.js`, `RECOVERY.md`, `BUILD.md`.
3. Commit with pinned file contents. Tag the commit with a semantic version and include a changelog entry when you update.
4. Enable GitHub Pages from the repo `main` branch or `gh-pages` branch.

## Using a simple bundler (optional)
If you prefer to produce a smaller single-file artifact that inlines `libsodium`, use a bundler like `esbuild`.

Example `esbuild` command (pin esbuild version in package.json):

```bash
npx esbuild personal-vault-index.html --bundle --minify --outfile=dist/index.html
