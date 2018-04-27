---
layout: page
title: Hot Module Replacement
permalink: /wiki/webpack/hot-module-replacement/
parent:
    text: Webpack
    link: /wiki/webpack
---

#### TLDR:

Enables hot-loading for changed modules on local dev server.

#### Usage

- Enable in config
- Watch out for bound event handlers pointing to outdated events after hot-swap. Need to write a function which re-binds the newer version which runs when the hot-swap happens, using a function hook provided by Webpack.