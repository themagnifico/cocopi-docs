Managing Pages
===

## The content folder

Copilot's content is managed with static files contained in your `content` folder. To add content, just add a file to this directory. A page can either be created with a single file, or with a single folder that can contain any number of additional files.

## Manage a page with a single file 

Every file in the content folder represents a page. The file name will determine the URL to access the page. The file extension determines how the page is rendered.

The file `content/about.html` will be available under `example.com/about` and rendered as a HTML page. The file `content/portfolio.md` will be accessible as `example.com/portfolio` and rendered as Markdown. 

## Manage a page with a folder

More complex pages can be located as an index file in their own folder. To create the page `example.com/blog`, you create a file called `content/blog/index.html` or `content/blog/index.md`.

You might prefer this over a single page because the folder allows to keep additional files like images right where you keep the page content itself.

Nested folder structures allow you to have sub-pages that can be rendered in your index file. You can use this for things like a blog. 

```
+-- content/
|   +-- blog/
|   |   +-- articles/
|   |   |   +-- article-1.md
|   |   |   +-- article-2.md
|   |   +-- index.md
```

This results in the following URLs:

| File      | Resulting URL                | 
|-----------|------------------------------|
| `content/blog/index.md` | `example.com/blog`                | 
| `content/blog/articles/article-1.md` | `example.com/blog/articles/article-1`               | 
| `content/blog/articles/article-2.md` | `example.com/blog/articles/article-2`               | 

# Hidden pages

File names starting with an underscore will not be accessible via URL automatically. You can use this to temporarily hide pages or to create content that is only accessible from the code, but not from the browser. 

An special case of a hidden page is the file `_meta.yaml` that you can use to store shared meta data for several pages. More on meta data in the next chapter on [the single page](page.md).
