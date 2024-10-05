---js
const eleventyNavigation = {
	key: "Home",
	order: 1
};

const numberOfLatestPostsToShow = 3;
---

# Hello and welcome!

If you've just set up your new 11ty base blog and would like to find some new themes for it, you've actually come to the right place this time ;)

## What is this?

We've now seen several people wanting to use 11ty but finding the path complicated, and frustratingly lacking in applicable themes.

Seeing as the [eleventy-base-blog](https://github.com/11ty/eleventy-base-blog) is such a good place to start, it makes sense to have a bunch of themes ready to drop into it.

This website will soon showcase some themes made with CSS stylesheets for use with the 11ty base blog, and make them easily downloadable.

## Want to contribute a theme?

YESSSSS please do! Please submit your 11ty base blog stylesheets, let's goooooo

You can find me in quite a few places, check my [contact details](https:sarajoy.dev/#find) to pick your preferred route.

You can drop me your own `index.css` file from your 11ty base blog, or whichever other stylesheets you have in your CSS bundle.

If you want to start from scratch, go ahead! I would then advise you to keep the following within your stylesheet:

```css
/* Turn on the light/dark/auto mode switcher if the theme uses color-scheme */
#mode-switcher {
	display: block !important;
}

/* Keep everything below within alternative CSS for sensible post numbering in postlist, and visually-hidden elements */

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
