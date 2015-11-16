# Theme

Your site's theme is located in `site/theme/`. This folder includes your main layout file as well as images, CSS and JS files needed or the site.

## Main layout file

The main layout is located in `site/theme/layout.html`. This file includes the markup your content will be rendered in by default.

## Templating syntax

Cocopi renders templates using the lightweight Lexy template engine. View files are compiled to plain PHP files which are cached. This makes rendering really fast. You can also use plain PHP in your view files.

Lexy has its own documentation available at FIXME. Here are some basic examples:

```php
// Print any valid PHP expression (not escaped).
{{ $variable }}

// Escape and print any expression
{{{ $escape_this }}}
{{{ "<strong>Will be escaped</strong>" }}}

@if( $expression )
    Simple conditionals. Wow.
@else
    Just look at this.
@endif

@foreach($something as $key => $value)
    You can iterate as well
@endforeach
```

## Main content

Where to render the main content inside your layout file.

```
{{ $content_for_layout }}
```

The `$meta` object contains the meta data from the current page. The `$site` array contains properties from your site configuration (`site/config/config.yaml`). You can use this to render the title of your page and default to the default site title if the page does not define its own title.

## Things to put in your `<head>` section

```
<title>{{ $meta->get('title', $site['site.title']) }}</title>
```

You can also use this for your metatags.

```
<meta name="description" content="{{ $meta->get('description', '') }}">
<meta name="keywords" content="{{ $meta->get('keywords', '') }}">
<meta name="author" content="{{ $meta->get('author', '') }}">
```

Include assets you need all the time and assets that have been added to the `$meta` object (i.e. from the current page layout).

```
@assets(['theme:css/site.css', 'cockpit:assets/lib/jquery.js', 'cockpit:assets/lib/uikit/js/uikit.min.js', 'theme:js/site.js'])
```

Note how some paths are registered with a shorthand. Cocopi will resolve these to the the full file paths. For a full list of available paths, have a look at the `system/bootstrap.php` and look for all lines starting with `$copilot->path(...)`.

To make sure your page layouts can also load asset files, include the following expression as well. In your page layout (or other view files) you can then use `@load('theme:js/custom.js')` to have additional asset files loaded.

```
@assets($meta->assets)
```

Before the closing `</head>` tag, you should include the following snippets. This will render any additional things, for example if one of the sub-layouts needs to include additional things aside from assets.

```
@trigger('site.header')
```

## Render a menu

Render menu `site/config/menu/main.yaml` and pass additional parameters to the menu renderer. You can
```
@menu('main', ['class'=>'uk-navbar-nav', 'activeClass' => 'uk-active'])
```

## Helpers and such

Extend another template file. I.e. you can always have the same wrapping markup in your master layout and have different page layouts that extend the master layout.

```
@extend('theme:layout.html')
```

Calculate and print the full link based on the base url of the site.

```
@base('/favicon.png')
```

Generate and print the URL to a route.

```
Read more <a href="@route('/about')">about us</a>.
```

Render Markdown to HTML and print the result.

```
@markdown('Just because **we can**.')
```

TODO

```
@start()
@end()
@block
```

TODO

```
@render()
```

TODO

```
@url()
```


Render a snippet. Read [more about snippets](snippets.md).

```
@render( 'snippets:teaser.html' , ['text' => 'Hello, handsome.'])
```

## Cockpit enabled

As Cocopi is built with Cockpit, you can also use all Cockpit helpers. For more information on Cockpit in general, head over to the [Cockpit documentation](http://getcockpit.com/docs).

Render a region.

```
@region('myregion')
```

Render a form.

```
@form('myform')
    ...
</form>
```
