# Proposal for a new CSS design layer

<p class="datestamp">Published 2013-01-08. Edited 2013-12-14</p>

​Here’s an idea that’s been banging around in my head for a couple of years now.

<p class="alert alert--info">
	<b>UPDATE (2013-01-10):</b> some good feedback below about the CSS content property.
</p>

Background-image is the fundamental way to get non-content images into your web design. Our CSS files are riddled with it. Textures and patterns, a handful of image-replacement techniques, fancy borders, etc. Heck, we even very often add some empty divs and other elements to our markup just to add yet more background images. 

The theory is that the html represents the meaningful content and all visual design should be “in the background”—and there’s certainly sound thinking there—but in reality designers can, and do, find ways to use those visual elements to convey meaning as well. Sometimes for me there’s a cognitive conflict between using visual design to communicate and keeping those designs in a background layer.

Designers are always looking for ways to create compelling sites that do both those things. In fact, for many of us and for a long time, that *is* what web design is all about.

An example born in this communication-vs-background conflict is the group of techniques known as image-replacement, a solution to the problem of using CSS background-image properties to add a logo to the page while still including the company name in the markup. You want the company name in the markup for screen readers and SEO but branding wants a logo. So you set the logo using CSS background properties and then hide the html text itself somehow so that the logo can be seen in it’s full, customer-engaging glory. Genius solution really, but those are hoops we’re jumping through. I mean, text-indent: -9999em?

Then something occurred to me one day, probably while trying to figure out Cufon…

## Presenting “foreground”

<div class="hero float--right">
	<div style="transform: rotate(0deg) skew(-52deg);-webkit-transform: rotate(0deg) skew(-52deg);-moz-transform: rotate(0deg) skew(-52deg);-o-transform: rotate(0deg) skew(-52deg);-ms-transform: rotate(0deg) skew(-52deg); text-align:center;background: rgba(100,100,100,0.3);padding: 40px 0;border-radius:10px;">
		foreground-image layer
	</div>
	<div style="margin-top: -20px;transform: rotate(0deg) skew(-52deg);-webkit-transform: rotate(0deg) skew(-52deg);-moz-transform: rotate(0deg) skew(-52deg);-o-transform: rotate(0deg) skew(-52deg);-ms-transform: rotate(0deg) skew(-52deg); text-align:center;background: rgba(200,200,200,0.3);padding: 40px 0;border-radius:10px;">
		semantic content
	</div>
	<div style="margin-top: -20px;transform: rotate(0deg) skew(-52deg);-webkit-transform: rotate(0deg) skew(-52deg);-moz-transform: rotate(0deg) skew(-52deg);-o-transform: rotate(0deg) skew(-52deg);-ms-transform: rotate(0deg) skew(-52deg); text-align:center;background: rgba(100,100,100,0.3);padding: 40px 0;border-radius:10px;">
		background-image layer
	</div>
</div>

What if there was a layer equivalent in every way to the background layer, but that displayed *above* the html? Think of “foreground-image”.

_Right!?_

Background properties are so basic to any web designer that a foreground layer that maps exactly to a background layer would be an instant hit. Suddenly, image-replacement techniques are unnecessary. It’s like progressively enhanced branding. It’s image-replacement without the need for the “replacement” part, because the logo would simply overlay the perfectly semantic text below it _without any changes to your html_.

<pre><code>
	Acme Corporation
	.branding {
		foreground-image: url(logo.png);
	}
</code></pre>

That’s it. And of course all the other related properties should be available too, including the shortcut:

<pre><code>
	.branding {
		foreground: transparent url(logo.png) no-repeat;
	}
</code></pre>

There are very cool embellishments that can be really simple right off the bat. How about a fade-to-white on the bottom?:

<pre><code>
	.faded {
		foreground: transparent url(fade-bottom.png) repeat-x left bottom;
	}
</code></pre>

Instead of javascript show/hide techniques which are often not accessible ([although there are ways](http://coding.smashingmagazine.com/2012/11/19/building-relationship-between-css-javascript/)), this gives us another method by dynamically adding a foreground mask to hide an item visually. Parallax on foreground and background images?

As for event binding and DOM manipulation, I assume this would be trivial since we’re still talking about a single element. There may be a challenge with foreground images somehow preventing clicks on the element itself, for example. Not sure. That’s where my mind starts wandering and I go get a snack. I’ll leave it to those super bright people in California or Oslo to figure out how to make that work.

I think this set of properties would be an instant hit with CSS coders. With all the background-image tricks in our bag, there should be a lot of good ideas that foreground-image should inspire.

### Update

Lea Verou ([@leaverou](https://twitter.com/leaverou)) suggested that the [conent property in CSS3](http://www.w3.org/TR/css3-content/#content) is meant to do what I'm proposing for foreground-image. After reading up a little on it I still think foreground-image is useful mainly because content: url() doesn't allow for either image-repeat or sprites, but also because I'm specifically *not* talking about content. I'm sure that once browser support catches up, the content property is going to be a popular solution for most simple image-replacement techniques, but at least it's current documentation doesn't imply several of the features foreground-image would support.

[@marcoos](https://twitter.com/marcoos) coded up a [demo](http://dabblet.com/gist/4505682) of content: url() which is supported at the moment on Webkit and Opera.

It’s also important to note that the content property was only for :before and :after pseudo-classes in CSS 2.1. The CSS 3 spec adds support for all elements.
	
	
	
	
	
	