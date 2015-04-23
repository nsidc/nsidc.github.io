---
layout: post
title: How To Post
published: false
catagories: [posting, blogging, tutorials]
---

# How To Post To This Blog

This post will teach you how to write a post for the NSIDC blog. Here is the quick version:

1. Create a new branch (your-post-tile)
1. Create a new file in _posts/ called [yyyy-mm-dd-your-post-title.md]
2. Add the YAML front-matter (the stuff at the top of this .md file) to your file.
3. Write your post in YAML, run `jekyll serve` to preview.
4. Create a pull-request so people can review your post and give feedback.
5. When you merge to master your post will be live!

# Some tips

## Code Highlighting

{% highlight python linenos %}

# see the source for code highlighting
# you'll probably want to paste in code from another file
foo = 'this is one way you can highlight code'
for word in foo.split():
  print(foo)

{% endhighlight %}
