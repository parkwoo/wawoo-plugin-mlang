# wawoo-plugin-mlang

Multi-language content support for wawoo-cms: language-prefixed URLs with per-language post/page resolution and language switcher links.

## Install

Requires the wawoo-cms core:

```
cd /path/to/wawoo-cms
php bin/wawoo plugin:link /home/git/wawoo-plugin-mlang
```

Enable via `config.local.php` `ENABLED_PLUGINS` or the admin Plugins page.

## Test

Coverage lives in wawoo-cms tests/Unit/PostsLangTest.php + PagesLangTest.php and the core E2E suite (multilingual URLs).

```
cd /path/to/wawoo-cms
php bin/wawoo plugin:link /home/git/wawoo-plugin-mlang
phpunit tests/Unit/PostsLangTest.php tests/Unit/PagesLangTest.php
```

## CI

GitHub Actions PHP 8.2/8.3: clone core, `plugin:link --copy`, then run core's `phpunit tests/Unit/PostsLangTest.php tests/Unit/PagesLangTest.php`.

## Dependencies

Depends on core language-suffix resolution in Posts/Pages (core >= 1.0.0). Optional companion: wawoo-plugin-i18n for translated UI chrome. Content translations are per-bundle files; no other plugin required.

## Release

Manifest requires `core >=1.0.0`; repo tagged `v1.0.0`; bump manifest + tag together.
