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

## TODO

`public function siblings($filter = null)`

`public function pages($path = '')`

`public function page($path)`

`public function depth()`

`public function data($store)`

`public function file($path)`

`public function files($path)`

`public function image($path)`

`public function images($path)`

`public function modified($format = null)`

`public function content($part = null)`

## TODO: maybe not document the following so people don't mess with the internals?

`public function setContent($content)`

`public function render($slots = [])`

`public function parts($name = null)`
