Page API
===

Every page file in the `content/` directory will be parsed by Cocopi and made available as a `$page` object. This document explains what you can do with that object.

The example return values are for the following file `content/about.md`

```
title: About Us
author: Bruce

===

Nothing to see, move along.
```

## Access meta data of the page.

| `$page->meta()` | Returns all meta data as a PHP array |
| `$page->meta('title')` | Returns `About Us` |
| `$page->meta('title', 'Unknown')` | Returns the value of the `title` parameter or `Unknown` if not set.|

## Get filename

`public function filename()` returns `about.md`

## Get filepath

`public function path()` returns `content/about.md`

## Get extension

`public function ext()` returns `md`

## Get page url

`$page->url()` returns `/about`

## Get page permalink

`$page->permalink()` returns `http://example.com/about`

## Is this page an index file

`$page->isIndex()` returns `false`

## Is this page the root index file

`$page->isIndex()` returns `false`

## Is visible or hidden

A page is hidden if the filename starts with an underscore `_`.

`$page->isVisible()` returns `true`

`$page->isHidden()` returns `false`

## Get parent page

`$page->parent()` returns `null` TODO: really? or returns index?

## Get child pages

`$page->children()`

## Get sibling pages

`$page->siblings($filter = null)`

## Find subpages

All subpages:

`$page->find()`

Matching a criterion (can be a string or a callback function).

## Get files attached to page

Any files in the folder of a content item can be seen as file attachements. You can query these and get an array of `Resource` objects. Check out [examples and explanation](files-and-images.md) of what to do with these.

`$page->files()`

## Get images attached to page

Same as `$page->files()`, but only returns images and leaves out other file types.

`$page->images()`

## Get page content

`$page->content($part = null)`

## Advanced methods

For even more details and methods, check out the [Lib\Page](https://github.com/COCOPi/cocopi-kickstart/blob/master/cockpit/modules/addons/Copilot/Lib/Page.php) class.
