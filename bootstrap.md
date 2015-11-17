# Add custom code in the bootstrap.php

You can execute any custom code you want in `site/bootstrap.php`.

## What can I use this for?

That's the beauty of this file: You can do whatever you want or need to do. Examples include, but are certainly not limited to:

1. Register [shortcodes](shortcodes.md)
2. Register a custom route
3. Register a route to a generated feed

## Some handy snippets

To access functionality from the `bootstrap.php`, you can make use of the following snippets.

The current page.

`$page = copi::$meta->page;`

The home page.

`$home = copi::home();`

Bind a custom route.

```php
copi::bind('/feed', function() {
    //...

    return "...";
});
```

For more examples check out the [copi API](copi-api.md).
