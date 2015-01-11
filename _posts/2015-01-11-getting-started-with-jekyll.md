---
layout: post
title: Getting Started with Jekyll
---

##Introduction
As I mentioned previously, I recently decided to restart my blog (not that I ever wrote particularly much anyway) and initially I thought I'd just restart it on Tumblr where it was previously. However, this is meant to be a technical blog and I expect to be posting code or configuration snippets fairly regularly and I've never found Tumblr (or most other blogging tools) to handle this particularly well so I decided to see what other options were available. 

After a short amount of searching, I found a number of recommendations to use [Jekyll](http://jekyllrb.com) and host the blog on [GitHub Pages](http://pages.github.com). This seems like a great solution - GitHub Pages allows me host the entire site for free, while Jekyll allows me to maintain the entire site offline in a local Git repository, with the ability to work on it offline (such as on a plane, like I am now) and just push to GitHub whenever I want to publish. Despite how simple Jekyll is, I further came across [Poole](http://getpoole.com), which makes things even easier by bundling up some sample content and a couple of pre-built themes ([Hyde](http://hyde.getpoole.com) and [Lanyon](http://lanyon.getpoole.com)). 

##Getting Started
The first thing you need to do is create a GitHub account if you don't already have one, so head on over there and do that at [GitHub](http://github.com). 

Next, you need to fork your chosen starter project ([Hyde](https://github.com/poole/hyde), [Lanyon](https://github.com/poole/lanyon) or [Poole](https://github.com/poole/poole)) into your account. Just browse to the repository of your choice on GitHub, and click the "Fork" button near the top.

Once you've cloned the repository, you need to go into its settings (look on the right hand side of the repository's page) and rename it to \<username\>.github.io (replace "username" with your own).

Now you can clone the repository onto your local machine (replace "username" with your own):
{% highlight bash %}
git clone http://github.com/username/username.github.io
{% endhighlight %}

Make some initial changes to the sample project - I recommend starting with _config.yml and updating the title, description and author information.

After you've made your initial changes, commit them to your repository:
{% highlight bash %}
git commit -a -m 'Initial commit'
{% endhighlight %}

And finally, push your repository to github so that it is live:
{% highlight bash %}
git push
{% endhighlight %}

Now browse to http://username.github.io/ and see your new blog live.

##Posting
The process of creating a new post is relatively simple. In this instance I will also go through the workflow of using a draft post.

To create drafts, first create a _drafts folder in your project, then create a file for your draft post. For example, create the following in _drafts/getting-started.md:
{% highlight text %}
---
layout: post
title: Getting Started with Jekyll
---
#Heading
Content ....
{% endhighlight %}

To preview this locally, simply start the jekyll server from your project directory:
{% highlight bash %}
jekyll serve --drafts
{% endhighlight %}

Then open http://127.0.0.1:4000/ in your browser.

Once you're happy with your new post, simply move the .md file into the _posts folder, and rename to \<year\>-\<month\>-\<day\>-post-title.md, e.g. _posts/2014-11-30-getting-started-with-jekyll.md and then commit and push your git repository to github.


##Using a custom domain name
If you're like me, you won't want to use "username.github.io" for your blog, you'll want to use a custom domain so that you can move it somewhere else when something new and shiny comes along.

To use your own custom domain, simply add a CNAME record to your domain pointing to "username.github.io". For example in my esquilax.org domain, I have the following record:
{% highlight bash %}
blog	CNAME	cgascoig.github.io
{% endhighlight %}

Then, in your _config.yml update the "url" line with the full url of your custom domain, e.g.:
{% highlight yaml %}
url:              http://blog.esquilax.org
{% endhighlight %}

Commit your changes and push to github:
{% highlight bash %}
git commit -a -m 'Setup custom domain'
git push
{% endhighlight %}


##Summary
Hopefully this post will help you understand Jekyll and GitHub Pages, and allow you to get started with this new approach to publishing. 

As always, please send me any feedback or questions on twitter, where I am [@chrisgascoigne](http://twitter.com/chrisgascoigne)

