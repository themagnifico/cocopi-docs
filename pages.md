Managing Pages
===

## The content folder

Copilot's content is managed with static files contained in your `content` folder. To add content, just add a file to this directory.

## One file per page

Every file in the content folder represents a single page. The file name will determine the URL to access the page. The file extension determines how the page is rendered.

The file `content/about.html` will be available under `example.com/about` and rendered as a HTML page. The file `content/portfolio.md` will be accessable as `example.com/portfolio` and rendered as Markdown. 

# Hidden pages

File names starting with an underscore will not be accessable via url automatically. You can use this to temporarily hide pages or to create content that is only accessable from the code, but not from the browser. 

An example for this is a file `_meta.yaml` that you can use to store meta data for your content.

# Complex pages

More complex pages can be located as an index file in their own folder. To create the page `example.com/blog`, you create a `content/blog` directory and locate the pages content in a file called `content/blog/index.html` or `content/blog/index.md`.

This allows you to have sub-pages that can be rendered in your index file. You would typically use this for something like a simple blog page. 

```
+-- content/
|   +-- blog/
|   |   +-- articles/
|   |   |   +-- article-1.md
|   |   |   +-- article-2.md
|   |   +-- index.md
```

This results in the URLs `example.com/blog`

| File      | Resulting URL                | 
|-----------|------------------------------|
| `content/blog/index.md` | `example.com/blog`                | 
| `content/blog/articles/article-1.md` | `example.com/blog/articles/article-1`               | 
| `content/blog/articles/article-2.md` | `example.com/blog/articles/article-2`               | 
