---
layout: post-layout.njk
title: Enfin un nouveau billet
date: 2021-12-08
tags: ['post']
---
<!-- Excerpt Start -->

C'est le premier billet depuis 2 and et demi !

<!-- Excerpt End -->
 
Mais au moins, le blogue est maintenant hébergé sur GitHub Pages :)

Grace à l'action suivante :

```yaml
name: Build Eleventy

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-20.04

    strategy:
      matrix:
        node-version: [12.x]

    steps:
      - uses: actions/checkout@v2

      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}

      - name: Install dependencies & build
        run: |
          npm ci
          npm run build          

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          publish_dir: ./_site
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

Et surtout grâce à [Sophia Brandt](https://www.rockyourcode.com/how-to-deploy-eleventy-to-github-pages-with-github-actions/).
