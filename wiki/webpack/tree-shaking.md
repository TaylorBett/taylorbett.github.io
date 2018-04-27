---
layout: page
title: Tree shaking
permalink: /wiki/webpack/tree-shaking/
parent:
    text: Webpack
    link: /wiki/webpack
---

#### TLDR:

Pruning 'dead code' from JS bundles for load size purposes.

#### Usage

- Uses import/export syntax
- Requires 'side effects' set to false
- Requires Webpack production mode to enable pruning and minification, otherwise in non-prod mode the dead code will just have comments above it denoting it as prunable. 