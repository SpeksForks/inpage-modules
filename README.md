# In Page Content Modules

Alternative method to define content in the CMS, either replacing or amending
SilverStripe's core "page type" system. Allows authors to insert "content modules"
into a page as separate items, which enables more flexible content structures
both for sidebar-style content and flexible main content areas.

## Features

 * Define your own content modules by subclassing `ContentModule`
 * Sort modules via drag'n'drop
 * Save module drafts and publish independently of the parent page
 * List all used modules in a separate admin interface, and view their history
 * Reuse content modules on multiple pages by saving them to a library
 * Built-in modules: Text, Image (incl. cropping), related pages

## Screenshots

![Overview](docs/images/overview.png)

![Admin](docs/images/admin.png)

## Installation

Install the module into a `inpage-modules\` folder inside the webroot.
Then add the `ContentModule_PageExtension` class to either your base `Page` class or select subclasses.

```yml
# File: mysite/_config/config.yml
Page:
  extensions:
    - ContentModule_PageExtension
```

In your template (e.g. `themes/<yourtheme>/templates/Layout/Page.ss`) you can loop through
modules, and have them render with their own templates:

```html
<% loop $SortedContentModules %>
	$forTemplate
<% end_loop %>
```