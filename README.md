# NSIDC Technology Blog

This is the source for the NSIDC Technology Blog at [nsidc.github.io](nsidc.github.io).

## Quick-Start

* `bundle install`
* Create a new branch titled `my-post-title`
* `bundle exec rake new_post['my-post-tile','My Name']`
* Preview with `bundle exec jekyll serve` OR (see Blogging Preview Tips below)
* Create a pull request

## Blogging Preview Tips

While jekyll serve is fine there is a better way!

1. Install [live-server](https://www.npmjs.com/package/live-server)
2. Run `bundle exec rake build`
3. In another terminal window cd to `_site` and run `live-server`

As you edit your content the site will automatically be build and live-server will automatically update your changes in the browser.

## Blogging Basics

More information to come here, for now [read the docs](http://jekyllrb.com/docs/posts/)
