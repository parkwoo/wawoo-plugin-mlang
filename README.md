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

## Versioning, update & rollback
- **Compatible core**: wawoo-cms `>= 1.0.0` (`plugin.json` → `requires.core`).
- **Pin a deployment**: record the exact combination (e.g. core @ v1.0.0 +
  this plugin @ v1.0.0). Install from a tag/path:
      git -C /path/to/wawoo-plugin-mlang checkout v1.0.0
      php bin/wawoo plugin:link /path/to/wawoo-plugin-mlang
  For Docker images use `--copy`:
      php bin/wawoo plugin:link /path/to/wawoo-plugin-mlang --copy
- **Configuration & persistent data**: No own persistent data (translations are content files
  `posts/<slug>/index.<lang>.md` inside the posts volume). Configure
  `$GLOBALS['WAWOO_MLANG']` (default_lang, supported). Requires core
  language-suffix resolution (core >= 1.0.0). Tests = core
  `tests/Unit/PostsLangTest.php` + `PagesLangTest.php`.
- **Before updating**: back up the cache state volume + test:
      docker run --rm -v <cache-volume>:/data -v $PWD:/backup alpine tar czf /backup/cache.tgz -C /data .
      cd /path/to/wawoo-cms
      php bin/wawoo plugin:link /path/to/wawoo-plugin-mlang
      phpunit tests/Unit/PostsLangTest.php tests/Unit/PagesLangTest.php
- **Rollback**: checkout previous tag, re-link (--copy for Docker), restore cache volume backup, restart.

## License

Released under the [MIT License](LICENSE).

## Contributing & security

This is a standalone plugin/theme for [wawoo-cms](https://github.com/parkwoo/wawoo-cms).
Bugs, features and security reports follow the core project's policies:

- [CONTRIBUTING.md](https://github.com/parkwoo/wawoo-cms/blob/main/CONTRIBUTING.md)
- [SECURITY.md](https://github.com/parkwoo/wawoo-cms/blob/main/SECURITY.md)
- Versioning and rollback for this repository is described in the
  "Versioning, update & rollback" section above; releases are published as
  GitHub Releases on this repository's tags.
