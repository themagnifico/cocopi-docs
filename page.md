A single Page
===


## Page structure

A file in the `content` folder contains both meta data and content. These parts are separated by a line with three equal signs. 

```yaml
title   : Hello World
author  : Copilot
created : 2015-03-11

===

**This is the first Blog entry.**

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse fermentum lobortis porta. Mauris faucibus hendrerit pulvinar.
```

## Content

The content of your page can be HTML or Markdown, depending on the file extension. 

You can also use PHP here. If you do, it's recommended to keep the code simple and concise. When you start complex tasks, think about moving this to your Page layout, your theme or a snippet.  

## Meta data

The meta data is in `YAML` syntax, meaning that it is a simple representation of keys and values. By default, a page can set a `title` attribute to be used as a title for that page. Other parameters can be set as desired. These are used by the page layout or other pages, depending how you implement your site.

If you want all files inside a folder to share some meta data, create a file `_meta.yaml` in that folder. Whatever you put in that file will be added to each page's meta data just like you had specified that parameter inside every single file.

Use the `layout` key to set a different [page layout](page-layout.md) that is used to render this page. If you want to render the page with the layout `site/layouts/blog/article.html` set the key like this:

```yaml
layout : blog/article
```



