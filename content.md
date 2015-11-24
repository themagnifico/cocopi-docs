Content
===

## The content folder

Cocopi's content is managed with static files contained in your `content` folder. To add content, just add a file to this directory. A page can either be created with a single file, or with a single folder that can contain any number of additional files.

## Use the admin panel for easy content editing

If you use the admin panel, the files with your page content will be created automatically, including any meta data you enter in the web interface.

The admin panel just offers a differnet view on the content files. If you make a manual change in a content file, this will also appear when you open the page in the admin panel.

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

## Hidden pages

File names starting with an underscore will not be accessible via URL automatically. You can use this to temporarily hide pages or to create content that is only accessible from the code, but not from the browser.

An special case of a hidden page is the file `_meta.yaml` that you can use to store shared meta data for several pages. More on meta data in the next section below.

## A single content file

A file in the `content` folder contains both meta data and content. These parts are separated by a line with three equal signs.

```yaml
title   : Hello World
author  : Cocopi
created : 2015-03-11

===

**This is the first Blog entry.**

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse fermentum lobortis porta. Mauris faucibus hendrerit pulvinar.
```

### Content

The content of your page can be HTML or Markdown, depending on the file extension.

You can also use PHP here. If you do, it's recommended to keep the code simple and concise. When you start complex tasks, think about moving this to your Page layout, your theme or a snippet.  

### Meta data

The meta data is in `YAML` syntax, meaning that it is a simple representation of keys and values. By default, a page can set a `title` attribute to be used as a title for that page. Other parameters can be set as desired. These are used by the page layout or other pages, depending how you implement your site.

If you want all files inside a folder to share some meta data, create a file `_meta.yaml` in that folder. Whatever you put in that file will be added to each page's meta data just like you had specified that parameter inside every single file.

Use the `layout` key to set a different [page layout](page-layout.md) that is used to render this page. If you want to render the page with the layout `site/layouts/blog/article.html` set the key like this:

```yaml
layout : blog/article
```
