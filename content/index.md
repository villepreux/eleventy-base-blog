---js
const eleventyNavigation = {
	key: "Home",
	order: 1
};

const numberOfLatestPostsToShow = 3;
---

# Hello and welcome!

If you've just set up your new 11ty base blog and would like to find some new themes for it, this will be the right place once we've gathered some more :)

## What is this?

Finding drop-in themes to use with 11ty is proving tricky, as it's so very flexible and every implementation varies.

Seeing as the [eleventy-base-blog](https://github.com/11ty/eleventy-base-blog) is such a good place for people to start, it makes sense to have a bunch of themes ready to use with it.

This website will soon showcase themes made with CSS stylesheets for use with the 11ty base blog, and make them easily downloadable.

The bar along the top of the page shows the available themes and a download link. The files you download from there can be renamed to dropped into your `eleventy-base-blog`'s `\public\css` folder.

## Want to contribute a theme?

YES! Please do! Submit your 11ty base blog stylesheets, let's goooooo 🎈

You can find me in quite a few places, check my [contact details](https://sarajoy.dev/#find) to pick your preferred contact method.

You can drop me your own `index.css` file directly from your 11ty base blog, or whichever other stylesheets you have in your CSS bundle.

If you want to start from scratch, go ahead! I would then advise you to keep the following within your stylesheet:

```css
/* Keep everything below within alternative CSS for sensible
   post numbering in postlist, and visually-hidden elements */

/* https://www.a11yproject.com/posts/how-to-hide-content/ */
.visually-hidden {
	clip: rect(0 0 0 0);
	clip-path: inset(50%);
	height: 1px;
	overflow: hidden;
	position: absolute;
	white-space: nowrap;
	width: 1px;
}
/* Posts list */
.postlist {
	list-style-type: "";
}
.postlist-item {
	counter-increment: start-from -1;
}
.postlist-item:before {
	content: "" counter(start-from, decimal-leading-zero) ". ";
	text-align: right;
	margin-left: -1.5rem;
}
```
Additionally, for themes that use `color-scheme`, I've added a little built in light/dark/auto mode switcher in the top bar. You can enable this for your own theme, by also including the following in your CSS:
```css
/* Enable light/dark/auto mode switcher
   if the theme uses color-scheme */
#mode-switcher {
	display: block !important;
}
```

{% set postsCount = collections.posts | length %}
{% set latestPostsCount = postsCount | min(numberOfLatestPostsToShow) %}
<h1>Latest {{ latestPostsCount }} Post{% if latestPostsCount != 1 %}s{% endif %}</h1>

{% set postslist = collections.posts | head(-1 * numberOfLatestPostsToShow) %}
{% set postslistCounter = postsCount %}
{% include "postslist.njk" %}

{% set morePosts = postsCount - numberOfLatestPostsToShow %}
{% if morePosts > 0 %}
<p>{{ morePosts }} more post{% if morePosts != 1 %}s{% endif %} can be found in <a href="blog.njk">the archive</a>.</p>
{% endif %}

{# List every content page in the project #}
{#
<ul>
	{%- for entry in collections.all %}
	<li><a href="{{ entry.url }}"><code>{{ entry.url }}</code></a></li>
	{%- endfor %}
</ul>
#}
