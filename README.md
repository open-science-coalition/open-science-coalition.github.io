# Open Science Coalition

Hugo site for the Open Science Coalition. The theme lives in `themes/clean-hugo/`.

## Prerequisites

* [Hugo Extended](https://gohugo.io/installation/) 0.139.4
* [Node.js](https://nodejs.org/) 24 (`nvm use`)

## First-time setup

`npm ci` needs a `package-lock.json`. Create that file once (see below), then:

```bash
nvm use
npm ci
hugo server --disableFastRender
```

Open http://localhost:1313/.

## Production build

```bash
npm ci
hugo --gc --minify
```

Output goes to `public/`. Do not commit `public/`, `resources/`, or `.hugo_build.lock`.

## Refresh the lock file

From the repo root, with Node 24:

```bash
nvm use
npm install
npm audit
npm audit fix
```

Commit the new `package-lock.json`. Use `npm audit fix --force` only if you intend to accept major version bumps.

## Deploy

GitHub Actions builds and publishes the site.

* `.github/workflows/build-site.yml` builds on pull requests and on pushes to `main`, then checks links and images. Pushes to `main` also publish the site to GitHub Pages.

One-time setting in the GitHub repo: Settings, Pages, Build and deployment, Source = GitHub Actions. The site is published at https://open-science-coalition.github.io/.

Netlify: `netlify.toml` builds with Hugo Extended 0.139.4 and Node 24. The footer keeps the Netlify badge. Connect the repo in Netlify when you apply for the nonprofit plan. `npm ci` on Netlify needs the lock file in git.
