---
layout: post
title: Blogging with Jekyll and Github
categories: 
- jekyll
- github
- blogging
description: quick beginner's guide to blogging with jekyll
keywords: jekyll,github,blogging,howto,guide,backups,dropbox
---

Jekyll is a flat file website (blog) generator and it's pretty good. It's especially useful if you have a [github.com](http://github.com "Github code hosting") account (although it's rumoured to play nice with [heroku.com](http://heroku.com "Heroku ruby hosting") as well).

It feels a bit odd if you're used to the idea of a database-powered CMS, but it's quick and simple and if you use [git](http://git-scm.com "Git source control") you get version control and edit history thrown in for free (including [blame](http://book.git-scm.com/5_finding_issues_-_git_blame.html "Git blame manual") which is useful if you have multiple contributors). Backups become as simple as pulling the repository onto a machine (or two) or if - like me - you're really paranoid about losing things, you can dump your git repository into your [dropbox](https://www.dropbox.com/referrals/NTExMzE3MDg5 "Dropbox online storage") folder.

(Excuse the dropbox referral link, but it's for your own good - you _do want_ 250MB of extra free space don't you?)

So how to go about installing it? Simply run the following commands:

```
sudo gem install RedCloth
sudo gem install liquid
sudo gem install classifier
sudo gem install maruku
sudo gem install directory_watcher
sudo gem install open4
sudo gem install mojombo-jekyll -s http://gems.github.com
```

You can also optionally install pygments for code syntax highlighting (warning - the instructions given here are for a Mac running Snow Leopard, you can [find out how to install pygments for other OS choices here](http://wiki.github.com/mojombo/jekyll/install "jekyll + pygments install guide"))

```
sudo easy_install Pygments
```

All good? Still here? Yay! The next step is to look through [the official documentation](http://wiki.github.com/mojombo/jekyll/usage" Jekyll documentation on Github") which explains the basic folder structure and how to run a local server or for a quick tour of the basics [I recommend this tutorial](http://articles.sitepoint.com/article/jekyll-sites-made-simple "Jekyll: Sites Made Simple on sitepoint.com")
