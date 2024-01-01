---
title: "Light Reading"
summary: "Adjust more than colors when supporting dark mode."
tags: ["Typography"]
date: 2023-12-29
show-title: true
---

# Light Reading

Someone in my Mastodon feed (sorry, I looked but couldn’t find it. It was like a couple of days ago maybe?) pointed out something about dark mode web UIs that sat me right up! I think they called it “glow”, but I always think of it as “bloom”.

On a dark screen, the lighter the text the more it blooms -- meaning that the light from them pixels spills out past the edges of the letters. It reminds me of “bleed” from my old print design days. And the more of it, like several lines in a paragraph, the more bloom I see. 

## Basic dark mode is easy for simple sites

In CSS, it’s pretty easy these days to support light and dark modes for a simple site. It gets harder for more complex sites of course, but I think it’s a nice feature if worth the effort. The idea is easy: create a couple of custom properties for color and background-color, and flip them using a media query, like this:

```css
    :root {
        --color-text: #222;
        --color-background: #fff;
    }
    @media (prefers-color-scheme: dark) {
        :root {
            --color-text: #fff;
            --color-background: #111; // Even a little darker
        }
    }
```

This works great, but my point for this post is that <span style="padding: 6px 10px;color:white;background:#111">white text</span> has a lot of bloom. To me it’s like staring at a lot of tiny little light bulbs. The edges of the letters are hard to make out from the glare. Eyes get tired and reading gets difficult.

Here, I’ll emphasize what I see: <span style="padding: 6px 10px;color:white;background:#111;text-shadow: 0 0 4px white;">white text</span>

And although I’ve always had 20/20 vision, I’m getting old (ok, I am old) and I’m noticing _inconsiderate_ web typography a lot more these days. Also, dark mode is more commonly on at night, when people’s eyes are already tired anyway.

When switching from light mode to dark, it’s not enough to just flip the colors. I’m experimenting with a lot of it and am realizing that setting type for legibility is as different for light vs. dark mode as it is about which font you're using. I just did a quick check of the excellent [webtypography.net](http://webtypography.net/toc/) and didn’t see anything about it, but I’m sure someone out there has done some work on this.

Here's where I'm at as of this writing (using it for this very site), and it's really only scratching the surface:

```css
    :root {
        --color-text: #222;
        --color-background: #fff;

        --base-font-size: 18px;

        /*
         *  I usually use 1.4 or 1.5 for line height,
         *  and dark mode definitely needed 1.8.
         *  Now I just like 1.8 all the time!
         */
        --base-line-height: 1.8; 

        --reading-width: 48rem;

        --color-code: #ccc;
        --color-code-background: #111;
    }

    @media (prefers-color-scheme: dark) {
        :root {
            --color-text: #d6cdc1;
            --color-background: #111;

            /* even shorter line widths */
            --reading-width: 42rem;

            /* 
             *  Code blocks don't really look great just being inverted.
             *  So I'm tweaking the colors a bit.
            */
            --color-code: #aaa;
            --color-code-background: #1a1a1a;
        }
    }
```

The world of code editing includes hundreds of color themes that you can install to change how your app displays code on the screen. There are _so many themes_, and they cover the full color spectrum, light or dark, high or low contrast, dull or intense colors, etc. And many come in both light and dark mode (Solarized and Solarized Dark, for example -- a very popular pair). But the differences between the two modes are only in the colors. 

I think there are opportunities to improve legibility in dark mode that I haven't seen explored yet. And they go beyond just tweaking colors. Font-size, line-height, hue, brightness, and even letter-spacing, should all be re-considered for legibility when switching modes. 