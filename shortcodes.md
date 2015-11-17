Shortcodes
===

Copilot supports shortcodes in your content items. To understand how they work we will implement a simple `[gallery]` short code that you can use in your page content. This short code will render a list of all images in the page's directory.

## Register a shortcode

Add the following code to `site/bootstrap.php`. Not how short codes can have arguments, even though we are not using them here.

```php
$site['shortcodes']->add('gallery', function($args) {

    return copi::view('snippets:gallery.html');

});
```

## Create a snippet file

Create a file `site/snippets/gallery.html`.

```
{% $page = copi::$meta->page; %}
@foreach ($page->images() as $key => $file)
    <p>
        <img src="{{ $file->url() }}" alt="" />
    </p>
@endforeach
```

## Use the short code

Add the short code `[gallery]` to any content item. Make sure to add at least one image file to the folder of the content item.

## Shortcode API

The shortcode API is implemented in `cockpit/modules/addons/Copilot/Lib/ShortCodes.php`. All methods are available from the `site['shortcodes']` object.

- `$site['shortcodes']->add($tag, $fn)`: Add a shortcode with a callback function (example see above)
- `$site['shortcodes']->remove($tag)`: Remove a shortcode
- `$site['shortcodes']->removeAll()`: Remove all shortcodes
- `$site['shortcodes']->exists($tag)`: See if a shortcode exists
