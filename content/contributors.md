---js
const eleventyNavigation = {
	key: "Contributors",
	order: 2
};
---
{%- css %}{% include "node_modules/prismjs/themes/prism-okaidia.css" %}{% endcss %}

# Contributors

So far we have three contributors. Four contributors including the original!

## Current contributors

- **[11ty](https://www.11ty.dev/)**
  - [Original](?theme=original)
- **[Sara Joy](https://sarajoy.dev/)**
  - [Classic](?theme=classic)
  - [Simple Purple](?theme=simple-purple)
- **[Antoine Villepreux](https://villapirorum.netlify.app/web/)**
	- [VillaPirorum](?theme=villapirorum)
- **[Den McHenry](https://denmchenry.com/)**
	- [Enhanced Contrast Grid](?theme=enhanced-contrast-grid)

## How to contribute

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