---
layout: post
title:  "Building a personal website using Jekyll and GitHub Pages"
title-short: Building a Jekyll blog
tags: [websites, jekyll, github pages, personal website, ruby]
date:   2020-07-24 0000
categories: how-to
---



GitHub has a feature called [Pages](pages) which essentially lets you turn a repository full of [markdown](markdown) files into a website (like [the one you're on now](repo)). Seeing as I have very little web dev experience but feel relatively comfortable writing markdown, Pages seemed like a great way to get the feel of a custom personal website with GitHub handling most of the nitty-gritty backend details. It's also free, which fit my budget.

A personal website can be like a digital business card. I use mine as a blog and portfolio of both writing samples and the work I've done on the site. It's a powerful professional tool and an outlet for creativity.

If you have some coding experience and don't mind using command line tools, GitHub Pages and Jekyll might be worth considering if you want to build your own website..

Here's what worked for me:

1. [Prerequisites](#prereqs)
2. [Follow GitHub's getting started](#getting-started)
3. Modify the design
4. Set up a custom domain

<h2 id="prereqs">Prerequisites</h2>

* [Git](git)
* [Ruby](ruby)
* [Bundler](bundler)
* [Jekyll](jekyll)

After Git and Ruby, install [Bundler](bundler). Bundler is a utility that manages some backend tasks (like keeping the Ruby gemfiles up to date and making sure Jekyll builds execute properly) to reduce build errors or environment issues. GitHub recommends using Bundler to install Jekyll:

```
$ bundle install jekyll
```

Software installed, we're one step closer to a website.

IMAGE

<h2 id="getting-started">Follow GitHub's getting started</h2>

Follow [the setup guide](guide) on the Pages website:

1. Create your repository. For individual and organization pages, the repository must be named username.github.io, where username = your username. These websites will publish from the ```master``` branch of the repository. Project pages can publish from a ```gh-pages``` branch or a `docs` folder, but I'm only covering individual/organization pages in this guide.

2. Using your Git tool of choice, navigate to the root folder containing your soon to be website. Initialize it as a Git repository with the following, replacing REPOSITORY-NAME with your repository name:

```
$ git init REPOSITORY-NAME
> Initialized empty Git repository in /Users/octocat/my-site/.git/
# Creates a new folder on your computer, initialized as a Git repository
```


3.










[pages]: https://pages.github.com/
[markdown]: https://daringfireball.net/projects/markdown/
[repo]: https://github.com/Mandelliant/mandelliant.github.io
[jekyll]: https://jekyllrb.com/docs/installation/
[git]: https://git-scm.com/downloads
[ruby]: https://www.ruby-lang.org/en/documentation/installation/
[bundler]: https://bundler.io
[create-repo]: https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll
