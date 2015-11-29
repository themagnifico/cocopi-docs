Page Collection API
===

Cocopi doesn't use a database. Instead, all of your content is stored in static files. Still, Cocopi allows to query content items in a powerwul manner. This is useful when building sitemaps, dynamic menus or things like an RSS feed.

Example: Fetch the 10 most recent blog posts.

```
$articles = copi::page('content:index.html')
    ->find('$p->type()=="post"')
    ->sort('$p->meta("date")', 'desc')
    ->limit(10);
```


## Get all pages from folder

`$pages->fromFolder($folder, $criteria = null)``

## Get all pages matching a criteria

`$pages->find($criteria = null, $folder = null)` {

## Get pages count

`$pages->count()`

## Get first item

`$first = $pages->first()`

## Get last item

`last = $pages->last()`

## Reverse order

`$pages->reverse()`

## Limit count of items

`$pages->limit($number)`

## Skip items (useful for manual pagination)

`$pages->skip($items_per_page)`

## Negated search critera

`$pages->not($criteria)`

Everything that is not of the type "post"

`$pages->not('$p->type()=="post"')`

## Only keep visible items

`$pages->visible()`

## Only keep hidden items

Hidden content items are files or folders starting with the underscore, i.e. `_hidden.md` or `_hidden/index.md`.

`$pages->hidden()`

## Filter by criteria

`$pages->filter($criteria)`

## Sort by expression

`$pages->sort($expr, $dir = 1)`

`$pages->sort('$p->meta("date")', $dir = 'desc')`

Sort direction:

- ascending (default): `asc` or `1`.
- descending: `desc` or `-1`.

## Sort by value of the "sort" meta key

You can automatically sort items by the value of the "sort" attribute in the meta data. This attribute is set automatically when you manually sort your items in the admin panel.

`$pages->sorted()`

## Iteration

- `$pages->next()`: Advance internal position counter
- `$pages->rewind()`: Reset internal position counter to zero
- `$pages->current()`: Get page at current counter position
- `$pages->key()`: Get current counter position
- `$pages->valid()`: Check if the internal position counter points to an existing item

## Get pages as array

`$arr = $pages->toArray()`

## Get pages as JSON

`$arr = $pages->toJSON()`
