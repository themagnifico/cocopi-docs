The copi API
===

The `copi` offers a global access to much of Cocopi's functionality. You can call this from your layout files, your content files or your `bootstrap.php`

`copi::home()`: Returns the page object of the home page.

`copi::page($path)`: Returns the page object for a given path to a file.

`copi::pages($folder)`: Returns a PageCollection with all pages in a given folder.

`copi::snippet($snippet, $slots = [])`: Renders a snippet file with optional parameters which are handed to the snippet file.

`copi::menu($menu, $options = [])`: Renders a menu file (point to a `*.yaml` file)

`copi::find($criteria = null, $folder = null)`: Find all pages from your content matching given search criteria, optionally only from a given subfolder.

`copi::resource($path)`: Return a resource object for a given file path. A resource can be an image or any other file.

`copi::view($template, $slots = [])`: Render a view file from a given template file with optional parameters which are handed to the renderer.

`copi::render_page($view, $slots = [])`: Renders a page from a given file path.

`copi::render_page_route($route = null, $slots = [])`: Renders the page from a given route.
