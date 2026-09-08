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

## Requirements

`wawoo-cms >= 1.0.0`, PHP 8.3, no runtime deps.

Content multi-language also needs the core language-suffix support in Posts/Pages (already in core >=1.0.0); the i18n UI plugin is optional for translated chrome.
