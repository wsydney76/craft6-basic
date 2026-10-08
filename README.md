# Craft 6 Basic

This is a customized Craft 6 DDEV starter project which installs just the bare minimum to get you started with Craft CMS 6. It includes a basic setup with some things you will need in every project.

For a more extended example with a basic content model and more examples, see [Craft 6 Custom](https://github.com/wsydney76/craft6-custom).

## Disclaimer

Craft 6 is still in alpha, so anything may break anytime.

## Installation

Clone this repository into a new project directory `git clone https://github.com/wsydney76/craft6-basic your-project` and run `setup/install your-project` in it, or execute the included steps manually, adjusted to your needs.

> `setup/install` is not executable by default, so you may need to run `chmod +x setup/install` first, or run `bash setup/install` to execute it.

## Changes

### Composer

* Added `craft:migrate:up` to the `post-update-cmd` so that migrations are run automatically after a `composer update`.
* Clear Laravel and Craft caches after a `composer update` to avoid issues with stale caches.

`composer.json` requires `6.x-dev` versions of `craftcms/cms` and `craftcms/cms-assets` packages. Run `composer update` to get the latest versions.

Or go back to tagged releases of Craft CMS 6 by changing the version constraints in `composer.json` to `^6.0.0` and run `composer update`.

### Config

Added a couple of asset-related settings to `config/craft/general.php` to improve image quality, cache busting and ASCII support.

### Vite Integration

Updated `.ddev/config.yaml`, `vite.config.js` and `resources/js/app.js` according to [DDEV Vite Integration](https://docs.ddev.com/en/stable/users/usage/vite/#vite-integration), so that the Vite development server `ddev npm run dev` will work with automatic reloading.

### Content Model

Added  `Home` single sections with a `Simple Page` entry type (title only).

### Assets

Added an `images` asset volume  with `public/images` root directory.

Added an `Images Transformer` asset transformer with `public/dist/transforms/images` root directory.

> Convention: Set up a dedicated asset transformer for each asset volume to match paths.

### Templates

For simplicity, templates use Flux components. Adjust or replace to match your design.

Added templates:

* `layouts/app.blade.php` layout template with minimal markup and dark mode support.
* `_entries/home/show.blade.php` template for the home page with minimal markup.

Added Blade components:

* `<x-markdown :text="$text" />` blade component.
* `<x-nl2br :text="$text" />` blade component.
* `<x-img :image="..." width="..." height="..." />` blade component.
* `<x-prose>...</x-prose>` blade component for rendering rich text with Tailwind CSS typography styles.
* `<x-layouts.nav />` blade component for rendering a navigation menu.
* `<x-layouts.dark-mode-switcher />` blade component for switching between light and dark mode.

### Livewire/Flux

Added Livewire and Flux (free) to the project.

Published Livewire config filed (setting the `high-voltage` emoji to `false`, sorry...).

### Blaze

Installed Blaze for performance improvements.

### Tailwind CSS

Added the [Typography](https://github.com/tailwindlabs/tailwindcss-typography) plugin to Tailwind CSS for better typography support.

### Fonts

Added custom fonts support, see [Laravel docs](https://laravel.com/framework/docs/13.x/vite#working-with-fonts).

### Theming

The layout follows [Flux theming conventions](https://fluxui.dev/docs/theming), using `zinc` as the default base color. 

You can apply your theming in `resources/css/app.css` by overriding this base color and the accent color used in Flux components.

See the [Flux theme builder](https://fluxui.dev/themes).

This adds `accent`, `accent-foreground` and `accent-content` colors to the Tailwind CSS color palette, including dark mode support.

### Routes

Added a `'tests/{template}' route to test templates in the browser, e.g. `tests/home` will render the `resources/views/tests/home` template.

### IDE 

Added Prettier support for formatting `php,blade.php` files including sorting of Tailwind classes.

In PhpStorm, you can enable Prettier by going to `Settings > Languages & Frameworks > JavaScript > Prettier` and

* enable `Automatic Prettier configuration`
* add `,php,blade.php` to the `Run for files` list
* enable `Run on save`, `Run on paste`, and `Prefer prettier...` options.

Note: Prettier may mess up comments in `@props` directives, so we follow the convention to put comments into a separate `@php` block, e.g.

```blade
@props([
    'entry',
])

@php
    /** @var CraftCms\Cms\Entry\Elements\Article $entry */
@endphp
```

Dropped `laravel-pint`.

Added `FauxCraft` file to enable autocompletion for often used variables in templates, such as `$entry`, `$image`, etc.

## AI Support

Not yet. In local dialect: 

> Mia glangt dass i woas das i kannt wann i woin dad. Aber i duas ned, weil i muas ned.
