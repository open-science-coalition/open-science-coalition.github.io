# Open Science Coalition

[![Netlify Status](https://api.netlify.com/api/v1/badges/6e15368c-55d1-4ed1-a6e2-47a6eee69164/deploy-status)](https://app.netlify.com/projects/open-science-coalition/deploys)

Hugo site for the Open Science Coalition. The theme lives in `themes/clean-hugo/`. These theme is copied from the pyopensci website repository:

https://github.com/pyopensci/pyopensci.github.io

use at own risk :) 

## Prerequisites

* [Hugo Extended](https://gohugo.io/installation/) 0.139.4
* [Node.js](https://nodejs.org/) 24 (`nvm use`)

## Check out the site locally 

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

The output of the above commands will be dumpted into  `public/`. Do not commit `public/`, `resources/`, or `.hugo_build.lock` to git history!! 

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

This site is deployed using GitHub Actions builds and is published using GitHub Pages. We use Netlify for live previews of pull requests. 

The site is published at https://open-science-coalition.github.io/. 
