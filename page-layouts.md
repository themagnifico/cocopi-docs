Page layouts
===

When your page is rendered, COCOPi takes the content and places it inside a so called page layout. By default, this is the main layout as defined by your site's theme: `site/theme/layout.html`. A page layout will also take the meta data of the current page and use parts of it, i.e. the page title to place in the broser window title.

## Render a page with a another page layout

If you want your page to be rendered with a different layout, you can specify that in the meta data of your page file.

```yaml
layout : blog/article
```

This file will now be rendered using `site/layouts/blog/article.html`.

## Create custom page layouts

Locate all your custom page layouts in your site's layout directory `site/layouts/`. To create your own layout, create a new file inside that folder, i.e. `site/layouts/blog/article.html`.

You can use any HTML markup inside the layout and have access to a simple but powerful templating engine.

Output the page content:

```
{{ $content_for_layout }}
```

You have access to the current page object `$page` and can access any parameter of its meta data.

```
<h1>{{ $page->meta('title') }}</h1>
<em>Written by {{ $page->meta('author') }}</em>
<p>{{ $page->content() }}</p>
```

For more on the `$page` object, check out the [Page API](page-api.md) documentation.

## Extend page layouts

Page layouts can extend other page layouts so you don't have to rebuild every layout from scratch.

```
@extend('theme:layout.html')
```

The child layout will render in its parent's content location, so exactly where the following line is placed in the parent layout.

```
{{ $content_for_layout }}
```
