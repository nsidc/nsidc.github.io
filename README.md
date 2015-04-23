# NSIDC Technology Blog

This is the source for the NSIDC Technology Blog at [nsidc.github.io](nsidc.github.io).

## Quick-Start

* Create a new branch titled `my-post-title`
* Create a new file in `_posts/` titled `YYYY-MM-DD-my-post-title.md`
* Add the following "front-matter" to your new file:

```
---
layout: post
title: my-post-title
author: Your Name
---
```

* Preview with `jekyll serve` (see Blogging Preview Tips below)
* Create a pull request

## Blogging Preview Tips

While jekyll serve is fine there is a better way!

1. Install [live-server](https://www.npmjs.com/package/live-server)
2. Run `jekyll build --watch`
3. In another terminal window cd to `_site` and run `live-server`

As you edit your content the site will automatically be build and live-server will automatically update your changes in the browser.

## Blogging Basics

More information to come here, for now [read the docs](http://jekyllrb.com/docs/posts/)
