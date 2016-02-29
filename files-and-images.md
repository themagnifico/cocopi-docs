Working with images and files
===

Internally, Cocopi represents files and images as instances of the `Resource` class. You don't need to think about that in most cases, but it's useful background knowledge.

The resource class includes helpful methods to work with file and image operations, fetch meta data and render thumbnails.

There are two common use cases to receive a `Resource` object that you can work with.

1. Fetch a resource object for a known file path: `$file = copi::resource($path)`
2. When you query for files attached to a content item, you automatically receive an array of `Resource` objects: `$files = $page->files()` and `$images = $page->images`.

## Fetch images from content item

Any images located in the folder of a content item can be queried directly from your content layout (or the content file itself).

Lexy example:

```
{% $images = $page->images() %}
@foreach($images as $img)
    <a href="{{ $img->url() }}"><img src="{{ $img->thumb_url(300); }}"></a>
@endforeach
```

PHP example:

```
<?php $images = $page->images() ?>
<?php foreach($images as $img): ?>
    <a href="<?= $img->url() ?>"><img src="<?= $img->thumb_url(300); ?>"></a>
<?php endforeach; ?>
```

## Fetch files attached to your content item

You can query and list more than just images for the current content item.

```
<h2>Attachments</h2>
<?php foreach($page->files() as $file): ?>
    <li>
    Name: {{ $file->filename() }}
    Type: {{ $file->ext() }}
    Size: {{ (int)($file->size() / 1024) }} KB
    <a href="<?= $file->url() ?>">Download</a>
    </li>
<?php endforeach; ?>
</ul>
```

## Add meta data to files

For any file `demo.jpg`, you can create a `demo.jpg.yaml` file in the same folder. Include any kind of meta data in the YAML syntax. You can query this data using the `meta()` method on a file resource object.

Example  `demo.jpg.yaml`:

```
title: Panorama
comment: This photo was taken during my travels to New Zealand.
```

`site/layouts/files.html`:

```
@foreach($page->files() as $file)
    <h2>{{ $file->meta('title')}}</h2>
    <p>{{ $file->meta('comment') }}</p>
@endforeach
```

## Generate thumbnails

To fetch a thumbnail URL for a given image, use the global function `thumb_url()` or the `$image->thumb_url()` method call (see example above).

You can specify dimensions and a resize behaviour. The thumbnail files are generated once and then saved in `/storage/thumbs/`. The only required parameter is `$path`, the other ones are optional.

```
thumb_url($path, $width, $height, $options=array())
```

Example:

```
{{ thumb_url('site:assets/logo.png', 300, 200, ["mode" => "resize"]) }}
```

Available options for the `$options` array:

<table class="uk-table">
<thead>
    <tr>
        <td>Key</td>
        <td>Default value</td>
        <td>Description</td>
    </tr>
</thead>
<tbody>
    <tr>
        <td>rebuild</td>
        <td>false</td>
        <td>Force rebuilding the thumbnail instead of using a previously generated file</td>
    </tr>
    <tr>
        <td>cachefolder</td>
        <td>site:storage/thumbs</td>
        <td>path to folder to save the generated thumbnail</td>
    </tr>
    <tr>
        <td>quality</td>
        <td>100</td>
        <td>Jpeg image quality</td>
    </tr>
    <tr>
        <td>base64</td>
        <td>false</td>
        <td>Return the base64 encoded image instead of the file path</td>
    </tr>
    <tr>
        <td>mode</td>
        <td>crop</td>
        <td>Image resizing mode. Available: 'crop', 'best_fit', 'resize','fit_to_width'</td>
    </tr>
    <tr>
        <td>domain</td>
        <td>false</td>
        <td>If set to true, the returned path will start with the domain of the site. Useful for feeds etc, where an absolute path is needed.</td>
    </tr>
    <tr>
        <td>overlay</td>
        <td>false</td>
        <td>Provide a path to an image which will be overlayed over the thumbnail. Useful for watermarks.</td>
    </tr>
    <tr>
        <td>overlay_pos</td>
        <td>center</td>
        <td>Position of the overlay. Available: center, top, left, bottom, right, top left, top right, bottom left, bottom right.</td>
    </tr>
    <tr>
        <td>overlay_alpha</td>
        <td>1</td>
        <td>Alpha value of the overlay, determines how visible the overlay is. Value between 0.0 (invisible) and 1.0 (completely visible).</td>
    </tr>
</tbody>
</table>


## Generate url to a specific file path

The global function `url_to()` returns a URL to a given path. It only returns the path if the file exists.


Example:

```
<img src="{{ url_to('assets:logo.jpg') }}" alt="">
```

As you see you can use a handy shorthand notation for specific folders.
This works for the following folders.

- `site:` Your `/site` folder
- `docroot:` Document root of your server
- `tmp:` Folder for temporary files (`/storage/tmp`)
- `content:` Content folder `/content`
- `theme:` Folder of your theme. `/site/theme`
- `menu:` Folder of your menus. `/site/menu`
- `assets:` Asset folder cascade. First looks for a file in `/site/assets` and then in the default `/cockpit/modules/addons/Copilot/site/assets/`.
- `modules:` `/site/modules`
- `snippets:` Snippets folder cascade. First looks in `/site/theme/snippets`, then in `/site/snippets` and then in the default `/cockpit/modules/addons/Copilot/site/snippets`.
- `types:` Types folder cascade in the order `/site/theme/types`, `/site/types`, `/cockpit/modules/addons/Copilot/site/types`
- `layouts:` Layout folder cascade in the order `/site/theme/layouts`, `/site/layouts`, `/cockpit/modules/addons/Copilot/site/layouts`
- `cockpit:` Cockpit installation folder `/cockpit`
- `current:` Path to file of current page, i.e. `/content/blog/hello-world`
