
# Snippets

Snippets are small files to use for markup you use several times, i.e. a featured box that appears on several places of your site. You can also pass an option array as the second parameter.

```
@render( 'snippets:teaser.html' , ['text' => 'Hello, handsome.'])
```

An example for the `site/snippets/teaser.html`:

```
<div class="uk-panel uk-panel-box">
    <h2 class="uk-panel-title">{{ $text }}</h2>
</div>
```

By default, COCOPi looks for `.html` snippets in the `site/snippets/` directory, so in the example above we could also just write `@render('teaser', ...)`

## Snippets File cascade

COCOPi looks for snippets in several folders and take the last file it finds. That way you can overwrite system snippets (i.e. the default menu renderer, which is just a snippet internally).

`@render(snippet:example.html)` will look for:

1. 'system/snippets/example.html'
2. 'site/snippets/example.html'
3. 'site/theme/snippets/example.html'
