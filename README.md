#

Thoughts, ideas and course notes.

## Contents
- [About](#about)
- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
  - [Gem dependency settings](#gem-dependency-settings)
  - [Site settings](#site-settings)
  - [Site navigation](#site-navigation)
- [Using includes](#using-includes)
- [Page layouts](#page-layouts)
- [Page and Post options](#page-and-post-options)
- [Credits](#credits)

## About

I put my various notes on courses or readings into my blog. I'll add any interesting things I find along the way.

## Features

- Based on Jekyll using the [Alembic theme](https://github.com/daviddarnes/alembic) from David Darnes
- Hosted on Github Pages
- Setup assistance from [Barry Clark](https://www.smashingmagazine.com/author/barryclark/) and his [SmashingMag article] (https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/)
  - Deployment from mac using [github desktop]().
  - all configuration in the `_config.yml` file.
- jekyl file setup from Damon (Bauer)[http://damonbauer.me/] (Organizing Jekyll Pages) [http://damonbauer.me/organizing-jekyll-pages/]

## Installation

1. [Fork from the original repo](https://github.com/daviddarnes/alembic#fork-destination-box)
2. Clone down the repo with `$ git clone git@github.com:username/reponame.git`
3. Delete the `demo/` folder and `screenshot.png` files
4. Change the `CNAME` record to your projects' record
5. Install bundler with `$ gem install bundler`
6. Install gems with `$ bundle install`
7. Run Jekyll with `$ bundle exec jekyll serve --watch`
8. Begin hacking
9. Commit and Sync to github

## Configuration

There's a number of settings you'll need to change before you can start hacking away at files. Here's a run down of what you'll need to change:

### Gem dependency settings
`twitter`, `author` and `social` values will need to be changed to the projects' social information or removed. Look for the `Gem settings` comment within the `/_config.yml` file. These values are for the [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) - follow the link to find out more.

### Site settings
You'll need to change the `description`, `title` and `url` to match with the project. You'll also need to replace the `/assets/placeholder-logo.svg` `/assets/placeholder-social.png` with project logo and default social image. The `email` needs to be changed to the email you want to receive contact form enquires with. The `disqus` value should be changed to your project username on [Disqus](https://disqus.com). Look for the `Site settings` comment within the `/_config.yml` file. The `repo` setting is optional, for now, and can be removed entirely, if you wish.

### Site navigation
There are a total of 4 different navigation types:

- `navigation_header`: The links shown in the header (it is also used on the 404 page)
- `navigation_footer`: The links shown in the footer
- `social_links`: The social icon links that are shown in the sidebar
- `sharing_links`: The social sharing buttons that are shown at the bottom of blog posts

Also this is hosted on github at `\Blog` so added in a number of prepend: site.baseurl into the various navigation links.  This is defined in the `_config.yml` file. Thanks to [Parker](https://byparker.com/blog/2014/clearing-up-confusion-around-baseurl/) for pointing out the right place to look.

All navigations can be edited using the `_config.yml` file. To see example usage either look for the `Site navigation` comment within the `/_config.yml` file or see [the nav-share.html include](#nav-sharehtml).

If there are no items for the `navigation_header` or `navigation_footer`, they will fallback to a list of pages within the site. The `social_navigation` properties should either be one that is already in the list (so `Twitter` or `Facebook`) or simply `link`, this is so an icon can be set for the link.

## Using includes

There are 2 main types of includes: ones designed for the site and ones that are designed as shortcodes. Here are a list of the shortcode includes:

### `button.html`
A button that can link to a page of any kind.

Example usage: `{% include button.html text="I'm a button" link="https://github.com" %}`

Available options:
- `text`: The text of the button _required_
- `link`: The link that the button goes to _required_
- `icon`: The icon that is added to the end of the button text
- `color`: The color of the button

### `figure.html`
An image with optional caption.

Example usage: `{% include figure.html image="/uploads/feature-image.jpg" caption="Check out my photo" %}`

Available options:
- `image`: The image shown _required_
- `caption`: A caption to explain the image
- `position`: The position of the image. `left`, `right` or `full`

### `icon.html`
An icon.

Example usage: `{% include icon.html id="twitter" %}`

Available options:
- `id`: The reference for the icon _required_
- `title`: The accessible label for the icon
- `color`: The desired colour of the icon

### `nav-share.html`
A set of buttons that share the current page to various social networks, which is controlled within the `_config.yml` file under the `sharing_links` keyword.

Example usage: `{% include nav-share.html %}`

Available options:
``` yml
Twitter: "#1DA1F2"
facebook: "#3B5998"
Google+: "#DC4E41"
Pinterest: "#BD081C"
LinkedIn: "#0077B5"
tumblr: "#36465D"
Reddit: "#FF4500"
Hacker News: "#ff6600"
Designer News: "#2D72D9"
Email: ""
```

_The first item is the name of the network (must be one of the ones stated above) and the second is the colour of the button. To remove a button just remove the line of the same name._

### `video.html`
A YouTube video.

Example usage: `{% include video.html id="zrkcGL5H3MU" %}`

Available options:
- `id`: The YouTube ID for the video _required_

### `map.html`
A Google map. _See Google [My Maps](https://www.google.com/mymaps)_

Example usage: `{% include map.html id="1UT-2Z-Vg_MG_TrS5X2p8SthsJhc" %}`

Available options:
- `id`: The map ID for the video _required_

### `site-form.html`
Adds a contact form to the page.

Example usage: `{% include site-form.html %}`

This include has no options. Use the `email` option in the `/_config.yml` to change to the desired email.

### `site-search.html`
Adds a search form to the page.

Example usage: `{% include site-search.html %}`

This include has no options. This include will add a block of javascript to the page and javascript reference in order for the search field to work correctly.

## Page layouts

As well as `page`, `post`, `blog`, there are a few alternative layouts that can be used on pages:

- `page-aside-left`: Places the aside (sidebar) to the left of the content
- `home`: Removes the aside entirely, leaving the full width for the main content (typically used for home page designs)
- `categories`: Shows all posts grouped by category, with an index of categories in a left hand sidebar
- `search`: Adds a search field to the page as well as a simplified version of the sidebar to allow more focus on the search results

## Page and Post options

There are some more specific options you can apply when creating a page or a post:

- `comments: false`: Turns off comments for that post
- `feature_image: "/uploads/feature-image.jpg"`: Adds a full width feature image at the top of the page
- `feature_text: "Example text"`: Adds text to the top of the page as a full width feature with solid colour; supports markdown. This can be used in conjunction with the `feature_image` option to create a feature image with text over it
- `indexing: false`: Adds a `noindex` meta element to the `<head>` to stop crawler bots from indexing the page, used on the 404 page

> **Note:** The Post List Page options are actually in the collection data within the `_config.yml` file.

## Credits

- Thanks to [Simple Icons](https://simpleicons.org/) for providing the brand icons, by [Dan Leech](https://twitter.com/bathtype)
- Thanks to [Sassline](https://sassline.com/) for the typographic basis, by [Jake Giltsoff](https://twitter.com/jakegiltsoff)
- Thanks to [Flexbox mixin](https://github.com/mastastealth/sass-flex-mixin) by [Brian Franco](https://twitter.com/brianfranco)
- Thanks to [Normalize](https://necolas.github.io/normalize.css/) by [Nicolas Gallagher](https://twitter.com/necolas) and [Jonathan Neal](https://twitter.com/jon_neal).
- Thanks to [pygments-css](http://richleland.github.io/pygments-css/) for the autumn syntax highlighting, by [Rich Leland](https://twitter.com/richleland)
- Lots of Thanks to [David Darnes] (https://daviddarnes.com) for the Alembic Theme [Alembic theme](https://github.com/daviddarnes/alembic)
