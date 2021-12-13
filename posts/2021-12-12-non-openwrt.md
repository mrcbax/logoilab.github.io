---
title: Everything to do with Non-OpenWrt
description: Sinkholing an accidental href for fun and profit.
published_date: "2021-12-12 04:58:00 +0000"
layout: default.liquid
is_draft: false

---

## Introduction

While I never intended to write an post about domain squatting, the perfect opporitunity made an appearance and so I decided to cover it in detail. This is the story of how a terms of service, fancy forum software, and an example.com came together to give me free SEO on a prominent, but unregistered, domain.

## How It Started

The wireless access in my house was lacking in one room. I decided to take one of my "project devices" (a networking device that is currently dead or useless) and try to install OpenWrt on it. The device I chose was a [Netgear WN370](https://www.netgear.com/business/wifi/access-points/wn370/) that I picked up off of ebay for $2. After hours of trying I could get it to boot, but it would not load the root filesystem.

After hours spent on a device worth only $2 I decided it was time to waste other people's time on it as well. My friend wrote up a very nice forum post on the [OpenWrt forum](https://forum.openwrt.org) for me. We sat and waited.

... And waited...

And waited

No one seemed to care about the WN370.

I had this great idea, lets bump the thread back to the top of the front page. If people think it looks active maybe they'll join our quest to get OpenWrt running on the device. I created my bump post, submitted it, aaaand *REMOVED for not following community guidelines*. So let's read the guidelines then.

That's when I found it. That wonderful domain. A wonderfully evil unregistered domain. On a [terms of service page](https://forum.openwrt.org/tos) no less.

![tos](/assets/img/non-owrt/tos.png)

Lo and behold:

![hmm](/assets/img/non-owrt/hmm.png)

It can't be, but it is. So like any logical person I rushed to register the domain as fast as I could.

Yours truly is now the official owner of [non-openwrt.org](https://non-openwrt.org)

## How It's Going

Well. It's popular. Oddly popular.

Cloudflare is reporting over 250 requests a day to the domain. Currently most of them are bots. This is expected as I doubt many people are actually reading the ToS for a forum from an open source project.

![cf-hits](/assets/img/non-owrt/cf-hits.png)

This is about as accurate as I get without adding analytics which I feel is not apropriate for this type of site.

As a huge sigh of relief for the OpenWrt project, the content I have (and intend to keep) hosted there is a simple message warning about the dangers of linking to unregistered domains.

## How This Happened

The creators of OpenWrt write an embbeded operating system, not forum software. To make their life easier they are hosting a copy of [Discourse](https://www.discourse.org/) which is an open source forum project focused on modernity and ease of use. Discourse has built in link parsing for posts. This parser takes anything that looks like a link in any post and attempts to create an href out of it when a user browses the page.

Unbeknownst to the OpenWrt forum maintainers; this parser was utilized on the Terms of Service page as well. In fact this is a bug on all installs of Discourse. See it present on the Rust community forum as well:

![rust](/assets/img/non-owrt/rust.png)

For the Rust community it is not as dangerous as they utilized a subdomain and the ToS seems to have parsed it properly.

## How to Fix It

Check the *Content Posted on Other Websites* section of your ToS page on your Discourse instance, remove any links that look like they shouldn't be there.

I will be issuing a bug report to the Discourse developers describing the problem and linking them to this article.

## TL;DR:

Don't link to domains that do not exist, someone could register them and give you a hell of a time.
