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

The bar along the top of the page shows the available themes and a download link. The files you download from there can be renamed to dropped into your `eleventy-base-blog`'s `/public/css/` folder.

## Want to contribute a theme?

YES! Please do! Submit your 11ty base blog stylesheets, let's gooo! [Contribution information](/contributors/#how-to-contribute) 🎈

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
