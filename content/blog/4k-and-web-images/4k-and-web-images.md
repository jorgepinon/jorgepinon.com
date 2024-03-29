---
title: 4K monitors and images for the web
description: When medium is too big
tags: ["Mobile", "Design"]
date: 2014-01-18
show-title: true
---

# 4K monitors and images for the web

<p class="datetime">January 18, 2014</p>

Dave Rupert has a [good post](http://daverupert.com/2014/01/4K-RWD/) about what 4K monitors mean for responsive web design. One point he makes in particular stuck out for me.

> 4K displays really reaffirm the need for a responsive images solution. If you choose to support 3840×2160 or 1920×1080@2× with full bleed imagery, it would require a 10 megapixel image. As it happens, you can’t even send a 10 megapixel image to all devices because iOS will simply will not accept them.

It’s a good point about iOS but the bigger problem is simply bandwidth. I’m sure Dave knows this but it’s worth saying. It doesn’t matter how many pixels your monitor has, we simply can’t send that many <del>mega</del> kilobytes of data for each image. Even if server-side responsive images were already here.

This image at 3200x2400px (unoptimized) is over 22MB. Bringing it down to 600x450px, optimizing with Photoshop, and saving at 50% jpg quality brings it down to 114K.

![Image of Iguana at Seaquarium in Miami, FL](iguana-600.jpg "What?")

On today’s desktop monitors, that’s still considered a large image—it takes up about half a page. Here’s what that same image looks like on a 4K monitor (@1x):

![Illustration of a 600 pixel image on a 4k monitor](600img-on-4k.png "I'm not a thumbnail!")

Marco Arment [predicts](http://www.marco.org/2014/01/08/retina-imac-mac-pro-prediction) that Apple will have a 4K monitor in 2014.

##Tightening our belts

We’ve been kind of spoiled for a couple of years here with most desktop monitors in the 1366–1920px width range and handheld browsers on 4G. Heavy javascript payloads and big images have become popular, but 4k monitors are going to make us carefully watch our bitmap image sizes.

Designers are going to have to add a 4K version to their wireframes and layouts, and big-image sites are going to need alternate designs for 4K screens. The good news is that designers and developers will probably be the first to adopt the larger screens, so image size/bandwidth will jump out at us right away.