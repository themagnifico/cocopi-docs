# Folder Structure

The folders you should check out first are `site/` and `content/`. These are the places where you manage your site appearance and where your content is located.

When you want to add custom PHP code, either just put in in `site/bootstrap.php` or add a folder with your own module in `modules/`

| Folder  | Purpose                |
|---------|------------------------|

| `cockpit` | Copilot is the admin panel that you can use to manage your content |
| `content` | Contains all **your content**. Every file or subfolder corresponds to one page. |
| `modules` | Additional modules you can install or create yourself. |
| `site`    | Defines what your site looks like. Theme, page layouts, content types, snippets, menus and assets such as CSS and JavaScript  |
| `system`  | COCOPi's own system code.  |
| `vendor`  | Third party libraries  |
