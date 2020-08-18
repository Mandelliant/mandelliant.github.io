---
layout: post
title:  "Configuring Handshake Top-level Domains for GitHub Pages"
title-short: Set up a Handshake domain for a GitHub Pages blog
tags: [websites, Handshake, github pages, personal website, domains, DNS, top level domain, HNS, DWeb, hosting]
date:   2020-08-18 0000
categories: how-to
---

### A Quick Start Guide for DWeb Hosting

*Originally posted on [BlockChannel](blockchannel)*

![Handshake and GitHub](/assets/img/blog/2020/configuring-handshake-domains-for-github/HNS-GH.png)

## What is [Handshake](handshake)?
Handshake is a decentralized DNS and certificate authority — think [Internet Corporation for Assigned Names and Numbers](icann) but with smart contracts instead of people.

If you’re not familiar with ICANN, it’s a United States nonprofit organization that maintains databases of namespaces and numerical designations on the web; a phone book for the entire internet.

>Handshake aims to experiment with new ways the internet can be more secure, resilient, and socially useful with a peer-to-peer system validated by the network’s participants. — [Handshake.org](handshake)

Handshake’s purpose is to remove the need for authorities like ICANN and the registrars that charge rental fees for domain name “ownership.” Instead, Handshake’s permissionless blockchain serves as the source of truth, providing immutable DNS records. This is the coolest part: this means when you buy a domain with Handshake, you actually *own* it.

Once you own a top level domain, naturally you want to do something with it. Here’s how to initially set up a personal website using GitHub Pages and then point your Handshake domain to it.

If you don’t own a Handshake domain yet, the [Namebase docs](nb-docs) walk you through the process.

## Setting up a GitHub Pages site

GitHub Pages lets users turn repositories into websites. There are two kinds of Pages sites: personal and project. Project sites let you turn a specific folder or branch of your repository into a website whereas personal sites require the entire repo and publish from the main branch. This guide is based on a personal GitHub Pages site.

*[GitHub’s official docs](pages-docs) are very helpful; I wrote a [step-by-step guide for building a Pages](pages-guide) site as well.*

Broadly speaking:
1. Create a new repository on GitHub called `USERNAME.github.io` where USERNAME is your GitHub username.
2. Go to the repository settings ...

![repo-settings](/assets/img/blog/2020/configuring-handshake-domains-for-github/settings-tab.png)

3. ... then scroll down to enable GitHub Pages by choosing a publishing source (for personal websites, select the *Master* branch) and choosing a theme.

![enable-pages](\assets\img\blog\2020\configuring-handshake-domains-for-github\pages-setting.png)

4. Add an `index.md` file to your repository's root directory and commit it to your publishing source (which should be the main branch).

## Updating your GitHub Pages URL settings

Once your repository has GitHub Pages enabled, in the Settings tab you’ll now have the option to set a custom domain for your site. As far as GitHub is concerned, it really is as easy as just typing in your Handshake domain and hitting ‘Save.’

![custom-domain](\assets\img\blog\2020\configuring-handshake-domains-for-github\github-pages-custom-domain-HNS.png)

I chose to set my URL as `writtenby.mandelliant` but it could have just as easily been `mandelliant`.

## Configuring your Handshake top level domain

Using Namebase, from your dashboard you can manage any domains you own.

Select the domain you want to use and click the 'Manage' button.

If you have the ability to host your own nameservers, Namebase recommends doing so, otherwise they give you the information you need to use theirs.

<br>

**Create your NS record:**

![ns record](\assets\img\blog\2020\configuring-handshake-domains-for-github\NS-record.png)

<br>
<br>

**Add your nameserver DNS records:**

![dns records](\assets\img\blog\2020\configuring-handshake-domains-for-github\HNS-DNS.png)

<br>

The Name field is the subdomain for your website, and the Value/Data field is where the URL should point. I left the default TTL value.

Your GitHub Pages site should now be accessible from `subdomain.yourdomain/`!

## Visiting Handshake domains

There are two ways to see your new domain in action: changing the DNS settings on your browser/device, or using the Handshake search engine [HNS.to](hns-to).


Give HNS.to a try by searching for `welcome.nb` or (shameless plug) `writtenby.mandelliant`.

![hns to](/assets\img\blog\2020\configuring-handshake-domains-for-github\HNS.to.gif)
*gif courtesy of the [Namebase docs](gif-link)*

If you want to try [modifying your DNS settings](dns-settings), Namebase covers a variety of methods on different platforms / operating systems.

Happy building! Thank BlockChannel for posting this piece originally by learning more about [what’s to come for the DWeb](dweb).





[blockchannel]: https://medium.com/blockchannel/configuring-handshake-top-level-domains-for-github-pages-f84f4a310c94
[handshake]: https://handshake.org
[icann]: https://www.icann.org/
[nb-docs]: https://learn.namebase.io/starting-from-zero/how-to-get-a-name
[pages-docs]: https://docs.github.com/en/github/working-with-github-pages/getting-started-with-github-pages
[pages-guide]: https://mandelliant.netlify.app/how-to/2020/07/27/building-websites-with-jekyll-and-github-pages.html


[hns-to]: http://hns.to/
[gif-link]: https://learn.namebase.io/starting-from-zero/how-to-access-handshake-sites#hns-to
[dns-settings]: https://learn.namebase.io/starting-from-zero/how-to-access-handshake-sites#more
[dweb]: https://medium.com/blockchannel/the-decentralized-web-a87b2b9d100
