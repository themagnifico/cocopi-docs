Types
===

Create content types with any content fields your project requires. A type tells Cocopi which fields it should display in the browser and which data it will store inside your content items.

## Create a new type

A type is defined by a `*.yaml` file which is located under `site/types/`. An event type could look as follows.

`site/types/event.yaml`

```
label: Event
layout: layouts:events/single.html
ext: md
meta:
    text:
        type: markdown
        label: Event description
    image:
        type: file
        label: Event photo
    date:
        type: date
        label: Event date
        options:
            format: YYYY-MM-DD
    location:
        type: text
        label: Event Location
```

The Cocopi interface will render a content area with a Markdown editor and four meta fields, with input elements according to the field type. When the user saves the item a page is created in the  `content/` folder.

The resulting content file will look something like:

`content/events/some-concert/index.md`

```
uid: pid-563f62cd2cf23
type: event
created: 2015-11-08 14:53:01
modified: 2015-11-14 09:47:14
title: Some Concert
date: 2015-11-12
location: Hamburg
image: >
  content/events/some-concert/demo.jpg
time: 20:00

===

# Some concert

Go to **this concert**. It will be awesome. Promise!
```

## Available parameters

- `label`: The label for this content type in the Cocopi interface
- `layout`: The layout view file to render when viewing a content item of this type
- `ext`: What file extension to save this content item to (available: `md` or `html`). This will also determine if the content part of a content item is rendered as Markdown or HTML.
- `meta`: List of meta fields for this content item. Every field needs at least a `label` and a `type`. You can set `options` which are defined for some field types. All available field types are listed below.
- `content`: Parameters for the content. Currently you can use this to hide the content field. This makes sense if your content type only needs fields and no content area. Example:
```
content:
    visible: false
```
- `subpages`: If subpages are allowed for a content item of this type. (default: `true`)
- TODO subtypes etc...

## Meta field types

- `boolean`
- `code`
- `date`
- `file`
- `gallery`
- `html`
- `image`
- `location`
- `markdown`
- `multipleselect`
- `object`
- `password`
- `repeater`
- `select`
- `set`
- `tags`
- `text`
- `textarea`
- `time`
- `wysiwyg`
