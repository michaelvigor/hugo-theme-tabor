# Hugo Tabor Theme

This is a port of the Wordpress [Tabor theme](https://github.com/themebeans/tabor) into a Hugo theme. Only a subset of the templates from the original theme has been migrated over, as there are a number of templates and styles for specific Wordpress plugins.

The Hugo theme [Terminal](https://github.com/panr/hugo-theme-terminal/) was used as a starting off point, and then the templates and styles were imported from Tabor for it to match as closely as possible the original.

A live demo of this can be seen at [https://michaelvigor.dev](https://michaelvigor.dev).

#### Built-in shortcodes

- **`image`** (prop required: **`src`**; props optional: **`alt`**, **`position`** (**left** is default | center | right), **`style`**)
  - eg: `{{< image src="/img/hello.png" alt="Hello Friend" position="center" style="border-radius: 8px;" >}}`
- **`figure`** (same as `image`, plus few optional props: **`caption`**, **`captionPosition`** (left | **center** is default | right), **`captionStyle`**)
  - eg: `{{< figure src="/img/hello.png" alt="Hello Friend" position="center" style="border-radius: 8px;" caption="Hello Friend!" captionPosition="right" captionStyle="color: red;" >}}`
- **`code`** (prop required: **`language`**; props optional: **`title`**, **`id`**, **`expand`** (default "△"), **`collapse`** (default "▽"), **`isCollapsed`**)
  - eg:
  ```go
  {{< code language="css" title="Really cool snippet" id="1" expand="Show" collapse="Hide" isCollapsed="true" >}}
  pre {
    background: #1a1a1d;
    padding: 20px;
    border-radius: 8px;
    font-size: 1rem;
    overflow: auto;

    @media (--phone) {
      white-space: pre-wrap;
      word-wrap: break-word;
    }

    code {
      background: none !important;
      color: #ccc;
      padding: 0;
      font-size: inherit;
    }
  }
  {{< /code >}}
  ```

## How to start

You can download the theme manually by going to [https://github.com/michaelvigor/hugo-theme-tabor.git](https://github.com/michaelvigor/hugo-theme-tabor.git) and pasting it to `themes/tabor` in your root directory.

You can also clone it directly to your Hugo folder:

```
$ git clone https://github.com/michaelvigor/hugo-theme-tabor.git themes/tabor
```

If you don't want to make any radical changes, it's the best option, because you can get new updates when they are available. You can also include it as a git submodule:

```
$ git submodule add https://github.com/michaelvigor/hugo-theme-tabor.git themes/tabor
```

⚠️ **The theme needs at least Hugo version 0.74.x**.

## How to run your site

If you installed all needed `npm` dependencies, then you can run:

```
$ hugo server -t tabor
```

and go to `localhost:1313` in your browser. From now on all the changes you make will go live, so you don't need to refresh your browser every single time.

## How to configure

The theme doesn't require any advanced configuration. Just copy:

```toml
baseurl = "/"
languageCode = "en-us"
theme = "tabor"
paginate = 5
pygmentsUseClasses = true

[params]
  contentTypeName = "post"
  showSubscribeWidget = false

  # Control which icons are loaded on the page
  icons = [
    "icon-email",
    "icon-github",
    "icon-twitter"
#   "icon-themebeans",
#   "icon-play",
#   "icon-settings",
#   "icon-settings-2",
#   "icon-settings-3",
#   "icon-arrow-down",
#   "icon-chain",
#   "icon-down",
#   "icon-right",
#   "icon-left",
#   "icon-search",
#   "icon-facebook-share",
#   "icon-thumb-tack",
#   "icon-lock",
#   "icon-500px",
#   "icon-bandsintown",
#   "icon-behance",
#   "icon-chownow",
#   "icon-codepen",
#   "icon-dribbble",
#   "icon-dropbox",
#   "icon-facebook",
#   "icon-facebook-mask",
#   "icon-flickr",
#   "icon-foursquare",
#   "icon-googleplay",
#   "icon-google",
#   "icon-google-mask",
#   "icon-instagram",
#   "icon-itunes",
#   "icon-linkedin",
#   "icon-medium",
#   "icon-meetup",
#   "icon-pinterest",
#   "icon-pinterest-mask",
#   "icon-reddit",
#   "icon-smugmug",
#   "icon-snapchat-ghost",
#   "icon-soundcloud",
#   "icon-spotify",
#   "icon-stumbleupon",
#   "icon-tumblr",
#   "icon-twitch",
#   "icon-twitter-mask",
#   "icon-vevo",
#   "icon-vimeo",
#   "icon-vine",
#   "icon-vsco",
#   "icon-wordpress",
#   "icon-yelp",
#   "icon-youtube",
#   "icon-houzz",
#   "icon-docker-hub",
#   "icon-rss",
#   "icon-quora",
#   "quora",
#   "icon-amazon",
#   "amazon"
  ]

  [params.author]
    name = "Michael Vigor"
    email = "m@michaelvigor.dev"

  [params.social]
    twitter = "michaelvigor"
    github = "michaelvigor"

  [params.header_nav]
    [params.header_nav.about]
      title = "About"
      link = "/about"

  [params.footer_nav]
    [params.footer_nav.about]
      title = "About"
      link = "/about"

    [params.footer_nav.twitter]
      title = "Twitter"
      link = "https://www.twitter.com/michaelvigor"
```

to `config.toml` file in your Hugo root directory and change params fields.

## Post archetype

See the basic `post` file params supported by the theme — https://github.com/michaelvigor/hugo-theme-tabor/blob/master/archetypes/posts.md

## Add-ons

- **Comments** — for adding comments to your blog posts please take a look at `layouts/partials/comments.html` https://github.com/michaelvigor/hugo-theme-tabor/blob/master/layouts/partials/comments.html.
- **Extended Head** — please take a look at `layouts/partials/extended_head.html` https://github.com/michaelvigor/hugo-theme-tabor/blob/master/layouts/partials/extended_head.html
- **Extended Footer** — please take a look at `layouts/partials/extended_footer.html` https://github.com/michaelvigor/hugo-theme-tabor/blob/master/layouts/partials/extended_footer.html

## How to (safely) edit the theme <a id="how-to-edit" />

First, you need to install Node dependencies. To do so, go to the theme directory (from your Hugo root directory):

```bash
 $ cd themes/tabor
```

 then run:

 ```bash
 $ npm install
 $ npm i yarn
 $ yarn
 ```

After you modified the files you can run webpack in watch mode:

```bash
$ yarn dev
```

or rebuild theme

```bash
$ yarn build
```

To see the changes (remember to restart `hugo server`).

## License

Copyright © 2020 Michael Vigor ([@michaelvigor](https://twitter.com/michaelvigor))

The Terminal theme is released under a MIT License. The original Tabor theme has been released under a GPL-V2 License.  As this theme is a derivative, it is also released under the GPL-V2 License.  Check the [license](https://github.com/michaelvigor/hugo-theme-tabor/blob/master/LICENSE.md) for additional licensing information.
