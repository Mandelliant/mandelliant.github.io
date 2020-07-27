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

If you have some coding experience and don't mind using command line tools, GitHub Pages and Jekyll might be worth considering if you want to build your own website.

Here's what worked for me:

1. [Prerequisites](#prereqs)
2. [Follow GitHub's getting started](#getting-started)
3. [Modify the design](#modify)
4. [Set up a custom domain](#domain)

<h2 id="prereqs">1. Prerequisites</h2>

* [Git](git)
* [Ruby](ruby)
* [Bundler](bundler)
* [Jekyll](jekyll)

After installing Git and Ruby, download [Bundler](bundler). Bundler is a utility that manages some backend tasks (like keeping the Ruby gemfiles up to date and making sure Jekyll builds execute properly) to reduce build errors or environment issues.

GitHub recommends using Bundler to install Jekyll. From the root folder of your site project, run the following command:

```
$ bundle install jekyll
```

<h2 id="getting-started">2. Follow GitHub's getting started</h2>

Follow [the setup guide](guide) on the Pages website:

1. Create your repository.
For individual and organization pages, the repository must be named <username>.github.io. These websites will publish from the `master` branch of the repository. Project pages can publish from a `gh-pages` branch or a `docs` folder, but I'm only covering individual/organization pages in this guide.

**Note: when initially setting up the repository for Pages on GitHub, the instructions walk you through configuration but don't explicitly say whether or not to create the repo. When you get to that point, initialize with a README (unless you're importing a repository) and click 'Create'.**


![create-repo](/assets/img/blog/2020/building-personal-website-jekyll/create-repo.png)


2. Using your Git tool of choice, navigate to the root folder containing your soon to be website. Initialize it as a Git repository with the following command, replacing REPOSITORY-NAME with your repository name:

    ```
    $ git init REPOSITORY-NAME
    > Initialized empty Git repository in /Users/anthony/mandelliant.github.io/.git/
    ```


3. Because this is a personal/organizational Pages site, the `master` branch is your live website. Check you're on the right branch with `git branch`.

    ```
    $ git branch
    > * master
    ```

    Once you're in the right folder and on the right branch, use the following Jekyll command to create the website: `$ bundle exec jekyll VERSION new .`. Replace VERSION with the [current dependency version GitHub Pages requires](dependency).

4. Open the Gemfile and follow the instructions in the code comments to configure it for GitHub Pages. The GitHub guide then says to update the `gem` line to: `gem "github-pages", "~> VERSION", group: :jekyll_plugins`, again replacing VERSION with the [current dependency version](dependency). I couldn't get that to work, so I left off the VERSION entirely and that seemed to do the trick. I'm not necessarily endorsing that as the correct course of action, but I haven't run into any issues.

    This is what the relevant lines of my Gemfile looks like after updating:


    ```ruby
    # If you want to use GitHub Pages, remove the "gem "jekyll"" above and
    # uncomment the line below. To upgrade, run `bundle update github-pages`.
    gem "github-pages", group: :jekyll_plugins
    # If you have any plugins, put them here!
    group :jekyll_plugins do
      gem "jekyll-feed", "~> 0.12"
    end
    ```

    Save and close the Gemfile.

5. At this point, GitHub suggests [testing your site locally](testing):

    ```
    $ bundle exec jekyll serve
    >  Configuration file: /Users/octocat/my-site/_config.yml
    >            Source: /Users/octocat/my-site
    >       Destination: /Users/octocat/my-site/_site
    > Incremental build: disabled. Enable with --incremental
    >      Generating...
    >                    done in 0.309 seconds.
    > Auto-regeneration: enabled for '/Users/octocat/my-site'
    > Configuration file: /Users/octocat/my-site/_config.yml
    >    Server address: http://127.0.0.1:4000/
    >  Server running... press ctrl-c to stop.
    ```

    In a new browser tab, navigate to `localhost:4000` to see your website for the first time.

6. Connect your local directory with your repository on GitHub.

    First, run `$ git remote add origin https://github.com/USER/REPOSITORY.git`, replacing USER with the user account that owns the repository, and REPOSITORY with the name of your GitHub Pages repo.

    Then push the repository to GitHub with `$ git push -u origin BRANCH`, replacing BRANCH with the name of the branch you're working on, which should be `master`.

And that's it! Your website should now be live at YOURNAME.github.io. You can check by navigating to your repo and opening the settings - if you scroll down, there will be a GitHub Pages section with a link to your site.

![pages-url](/assets/img/blog/2020/building-personal-website-jekyll/click-pages-url-to-preview.png)
*[image source](source)*

From there, the GitHub guide offers instructions on [adding new posts and pages](new-content) or [customizing your theme](custom-theme).


<h2 id="modify">Modify the design</h2>

If you're like me and unfamiliar with Ruby, different elements called gems control a lot of the configurations and settings; Jekyll layout themes, like the default theme Minima, are gems.

This means much of the HTML laying out your pages is hidden away in the directory where you initially installed Ruby. The path should be something like `Ruby26x-64 > lib > ruby > gems > 2.6.0 > gems > minima-2.5.1`, and from there you can access the `_layouts` and `_includes`.

If you only change the local version of the file, the changes won't be pushed to GitHub, so the live version of your website will look different than when you [test it locally](testing). To override any of these files, all you have to do is create a new version in a `_layouts` or `_includes` folder in your website's primary directory (similar to the instructions in the guide on [customizing your theme](custom-theme) - you can also look at my website's [repository](repo) as an example).

I added a callout box above the main content on my homepage so I could feature my most recent blog post above the list of my writing samples.

The homepage layout is controlled by the `index.markdown` file Jekyll placed in the root directory. If you open that file, you'll notice the layout is `home`.

![homepage](/assets/img/blog/2020/building-personal-website-jekyll/homepage-markdown.png)


So I added a `_layouts` folder to my root directory, then create a `home.html` file inside.

![layouts](/assets/img/blog/2020/building-personal-website-jekyll/layouts.png)

In the `home.html` file, I added the floating box:

![floating-box](/assets/img/blog/2020/building-personal-website-jekyll/floating-box.png)

*The endif tags in this code snippet were causing a Jekyll Liquid syntax error. You can find the code [here](floating-box-code).*

It required some CSS, so I created an `Assets` folder in the root directory and a `main.scss` file to supercede the default CSS that comes with the Minima theme.

```css
@import "minima";

.floating-content { padding: 30px 0; flex: 1; border: 1px solid;
  padding: 10px;
  margin-right: 50;
  box-shadow: 5px 10px #778899;
  background-color: #ffffff;
}
```

<h2 id="domain">Set up a custom domain</h2>

GitHub makes it really easy to add your own domain for your Pages site. From your repository on GitHub, go to the settings and scroll down to the GitHub Pages section. There will be a field to input a custom domain:

![domain](/assets/img/blog/2020/building-personal-website-jekyll/custom-domain.png)

This is my actual domain - thanks to a sweet project called [Handshake](hns), I own the top level domain `mandelliant/`. If you're [resolving HNS domains](hns-sites), check out [writtenby.mandelliant/](my-site). I plan to write more about Handshake and setting up the domain soon.

There are `baseurl` and `url` fields in the `_config.yml` file in your site's root directory, and I'm sure there's a very good reason for them, but it seems like I'm not having any issues leaving them empty for now.

---


[pages]: https://pages.github.com/
[markdown]: https://daringfireball.net/projects/markdown/
[repo]: https://github.com/Mandelliant/mandelliant.github.io
[jekyll]: https://jekyllrb.com/docs/installation/
[git]: https://git-scm.com/downloads
[ruby]: https://www.ruby-lang.org/en/documentation/installation/
[bundler]: https://bundler.io
[create-repo]: https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll
[dependency]: https://pages.github.com/versions/
[testing]: https://docs.github.com/en/github/working-with-github-pages/testing-your-github-pages-site-locally-with-jekyll
[source]: https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll#creating-a-repository-for-your-site
[new-content]:https://docs.github.com/en/github/working-with-github-pages/adding-content-to-your-github-pages-site-using-jekyll
[custom-theme]: https://docs.github.com/en/github/working-with-github-pages/adding-a-theme-to-your-github-pages-site-using-jekyll
[hns]: https://handshake.org/
[hns-sites]: https://learn.namebase.io/starting-from-zero/how-to-access-handshake-sites
[my-site]: writtenby.mandelliant/
[floating-box-code]: https://github.com/Mandelliant/mandelliant.github.io/blob/master/assets/main.scss
