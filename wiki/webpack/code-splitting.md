---
layout: page
title: Code Splitting
permalink: /wiki/webpack/code-splitting/
parent:
    text: Webpack
    link: /wiki/webpack
---

#### TLDR:

Bundling code either manually or automatically to reduce file size and produce different bundles for different pages.

#### Usage

##### Entry Points
- Manual config
- CON: Duplicate code will show in all entries, ie. dependencies
- CON: Inflexible and manual work required

##### Avoiding Duplication
- Use `CommonsChunkPlugin`
- Extracts common dependencies into separate entries

##### Dynamic imports

