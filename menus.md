# Menus

A menu is defined by:

1. A list of links, located as `*.yaml` files in the `/site/menu` folder
2. A renderer which creates the markup. Cocopi provides a default renderer that you can overwrite.

## Define links and structure of a menu

Every menu is defined by a YAML file in the folder `/site/menu/`. Your main menu could be called `main.yaml` and have the following content.

```
Home  : /
About  : /about
Portfolio: /portfolio
    Photos: /photos
    Videos: /Videos
Cocopi: https://cocopi.co/
```

YAML is a readable format for structured data and internally converted to an array representation. Read more about the [YAML syntax](https://en.wikipedia.org/wiki/YAML#Examples).

## Render a menu in your template

To render the menu defined in `/site/menu/main.yaml`, add the following snippet to the desired position in your theme layout file.

```
@menu('main')
```

The default menu renderer also takes an option array to influence the rendering of the markup. You can add additional classes on the top level container and define the class for the active menu element.

```
@menu('main', ['class'=>'uk-navbar-nav', 'activeClass' => 'uk-active'])
```

## Overwrite default menu renderer

If the default menu renderer does not suit your needs, you can overwrite the existing renderer by putting a snippet file in your site folder. For example copy the existing renderer from `/system/snippets/menu/default.html` to `/site/snippets/menu/default.html` and make any markup changes you want.
