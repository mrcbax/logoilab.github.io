---
title: Design Changes and Updates
description: An overview of what has been done and what has changed.
published_date: "2020-04-17 22:40:03 +0000"
layout: default.liquid
is_draft: false
---
I am de-Googling a lot of my own stuff and my projects as a side effect. I though I would also give this site some love while I was at it. The page you are currently reading is composed of HTML & CSS.

**That's it.**

Of course there are fonts and SVGs hanging around and the required pictures for certain posts but there is **no javascript**. Bootstrap is gone, Google Analytics is gone, Selly is gone.

### The current stack

I spent hours playing with minimal CSS frameworks and eventually just chose the one with the most recent updates and most features. For me that was [spectre.css](https://picturepan2.github.io/spectre/). With spectre I am also using [Animate.css](https://daneden.github.io/animate.css/), although it currently isn't in use at this point I'm a big fan of Dan Eden's projects.

All of this is composed by the [Cobalt](https://cobalt-org.github.io/) static site generator which is written in [Rust](https://rust-lang.org) and uses [Liquid](https://shopify.github.io/liquid/) templating. It is hosted on GitHub pages for simplicity but may be moving soon to baremetal with Cloudflare integration.

### What has(n't) changed

- The style (duh).
- DosLab electronics related content is now hosted at [doslabelectronics.com](https://doslabelectronics.com). The changes made on the DosLab side were immense for this and the web server itself is fully custom, no off the shelf anything. This itself warrants a full blog post.
- Legacy pages (ones linked to the most by other sites) remain in place at their original locations. This includes CVE write-ups and other *atomic* links.

### The fun stuff

- [Project Spacebar](https://github.com/LogoiLab/spacebar) is in use on this site and works much better after the recent overhaul.
- The title font is:<h1 class="title">[Sans Forgetica](http://sansforgetica.rmit/)</h1>I did this because it looks cool and is funny (fight me).
- [Wigle.net](https://wigle.net) stats are at the bottom. Race me to the top of the leaderboard.
- [Abuse IPDB](https://abuseipdb.com) stats are also at the bottom. Triggering [Fail2Ban](http://fail2ban.org) on DosLab servers will get you listed here.
- Keybase link is at the top for contacting me any way you see fit.
