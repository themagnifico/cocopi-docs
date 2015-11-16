# Folder Structure

The folders you should check out first are `site/` and `content/`. These are the places where you manage your site appearance and where your content is located.

When you want to add custom PHP code, either just put in in `site/bootstrap.php` or add a folder with your own module in `modules/`

| Folder    | Purpose                |
|-----------|------------------------|
| `cockpit` | Copilot is the admin panel that you can use to manage your content |
| `content` | Contains **your content**. Every file or subfolder corresponds to one page. |
| `site`    | Defines what your site looks like. Theme, page layouts, content types, snippets, menus and assets such as CSS and JavaScript |

And that's it basically.

# Version control

A best practice is to place the two folders `content` and `site` under version control and add `cockpit/` to your `.gitignore`.

In cases where your `content` folder becomes large or you do not want to sync your production content with the repository, maybe you just want to version control the `site` folder.

At the end, it's your call. Cocopi is all about giving control back into your hands.
