---
"title": "Thoughts on Javascript Frameworks"
"summary": "Any way to build web sites and apps should include web standards at its core."
"tags": ["JavaScript"]
"date": 2016-07-06
"show-title": true
---

# Thoughts on Current Javascript Frameworks

<p class="datetime">July 6, 2016</p>

In the dark days (90s), websites were created using a murky mix of css and js inside the html via attributes (bgColor="#888888" onClick="javascript..."). Any web developer nowadays, upon seeing one of those html files should shake their head at least as much as when seeing the page itself in a browser.

The web standards movement pushed web design forward by promoting the use of CSS and organizing site code by following the concept of “separation of concerns,” moving css and javascript out of html so the three elements make for more stable code. But there were many other benefits, including accessibility and wider browser support, performance gains from browser caching, code simplicity, and my favorite one, future-proofing.

Fast-forward to July, 2016 and javascript is now in the forefront of web development, with javascript frameworks the _de facto_ way to build a web app.

These frameworks offer some performance advantages that are hard to dispute. And as large web sites get even larger and more complex, separating functional components into modules makes sense, and frameworks encourage that. It’s no surprise that the two most popular frameworks at the moment, Angular and React were developed by Google and Facebook, respectively, companies with unbelievably large and complex codebases and the business need to squeeze every nanosecond of performance out of <del>the site</del> their development teams.

But by taking the module idea and expanding it to propose we should combine a module’s html and css in with the javascript is a step way too far and sounds to me like js devs making everyone play in their world. I like the idea of somehow organizing code with modules in mind, and even the idea of keeping all of a module’s pieces somehow more tightly coupled, but I can’t go for mixing html and css in js anymore than I could when it was js and css mixed in with the html.

I've heard arguments from the React side that separating html, css, and javascript was only a superficial separation anyway because all those things are needed by each module. A date-picker module needs all three things, and keeping them in the same file is actually _better_ for organizing your code. This argument sounds compelling, until you get past just code organization and remember  progressive enhancement.

Combining everything into a module’s React javascript file may be convenient and make your site load a bit faster, but that’s not good enough to ignore the cost. There are people in the React and Angular communities that do a lot of work to encourage progressive enhancement and [accessibility](https://github.com/dequelabs/Deque-University-for-Android), but React and Angular aren’t leading that charge unfortunately.

I hold on to the position that javascript should not be required. Javascript can vastly enhance the user’s experience but if done right, the site works without it. Same with CSS — makes things look way better, won’t make the site useless if it’s missing.

[Brad Frost said it](http://bradfrost.com/blog/post/i-have-no-idea-what-the-hell-i-am-doing/) very well:
>	At the end of the day this idea of progressive enhancement, this idea of Web standards, of starting with HTML and layering on CSS and layering on behavior on top of that is foundational work.

There are many more frameworks than React and Angular, and many more on the way. I’m sitting back and waiting for one of them to promote itself with a web-standards-first and accessible-by-default approach. I’m pretty optimistic that it will show up, too, because the reasons why web standards were important before are still true. There’s always a strong case for making your site future-proof.
