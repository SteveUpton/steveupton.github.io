---
title: Blog Update
date: 2025-04-21
slug: blog-update
Tags:
  - tech
---

So I finally updated my blog.

<!--more-->

## Moving to Hugo

The previous version of this site used Octopress. Overall, I had some decent experiences with it, but a few things prompted me to make the move to Hugo:

* Hugo appears to have a pretty active community and some pretty nice flexibility and features I'd like to take advantage of in the future.
* Octopress is written in Ruby, which I'm generally fond of, but the Rake setup for building and publishing the site always annoyed me a bit. It railroads you into a particular way of deploying the site to GitHub pages (my chosen static site host) and it's portability is lacking, with some pretty tedious steps required when moving to a new computer (which I just did).
* I felt like a change!

## Rewriting history

I mostly ported all the content directly to the new blog, but I did make a few changes.

I removed two old mapping related posts ("Mapping Your Visited Countries" and "YB3 vs Google location history") because they both made heavy use of platforms (YB3, Google Location History and [Carto](https://carto.com/)), which have undergone some pretty significant changes since then, both to how they work and in removing free tiers, which makes almost all of the guidance in the posts invalid. As it happens, I did recently update [where.was.steveupton.io](https://where.was.steveupton.io/) to account for that and I intend to post an updated version of that post soon™.

I moved all the travel blog images to Flickr. Over the lifetime of the previous blog, I switched from hosting the images in the site itself to hosting the images on Flickr to allow higher resolution images without ballooning the filesize of the repo, so I took this as an opportunity to complete the transition for a few older posts. Technically, this means the site is not completely portable/self contained, but for now, I'm happy with the service Flickr provides. 

On top of that, I made a few very minor updates to old posts, updating dead links, fixing some spelling mistakes and improving link accessibility. Nothing major, just some house cleaning.

The biggest bit of rewriting history I did was adding a few travel blogs that I never got around to posting and backdated them to around the time of the actual trip. Yeah, it's a lie, but it makes the blog archive a bit easier to skim, y'know?

I [archived the original Octopress blog](https://github.com/SteveUpton/blog-archive) and started fresh. The archive remains as a snapshot of how the blog looked before the refresh, but the [new repo](https://github.com/SteveUpton/steveupton.github.io) is clean.

## What's next?

There's still a few things I need to port over from the previous version of the blog, like the embedded maps I had on a few travel blogs.

I'd like to expand the site in general, potentially adding a projects/portfolio page, expanding the About page etc.

Most of all, I'm planning to actually start writing more!
