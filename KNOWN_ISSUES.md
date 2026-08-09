# Known Issues — laravel-package-skeleton

_Last checked: 2026-08-02_

## Failing tests

Could not run. `composer install --no-interaction` fails before any dependencies are resolved:

```
In Factory.php line 317:
  "./composer.json" does not match the expected JSON schema:
   - name : Does not match the regex pattern ^[a-z0-9]([_.-]?[a-z0-9]+)*/[a-z0-9](([_.]|-{1,2})?[a-z0-9]+)*$
```

This is because `composer.json`'s `name` field is still the literal placeholder
`":vendor_slug/:package_slug"` (as intended for a template meant to be renamed via a
scaffolding script before use), which isn't a syntactically valid Composer package name.
With no `vendor/` directory, the test/lint/analyse suite (`composer test`, pint, phpstan,
pest) could not be executed at all for this checkout.

## Style / static-analysis debt

Not evaluated — blocked by the `composer install` failure above (no `vendor/bin/*`
binaries available). A `phpstan-baseline.neon` exists but is empty (0 bytes), so no
baselined debt is pre-recorded either way.

## TODO / FIXME markers

None found (checked `src/`, `config/`, `database/`).

## Open GitHub issues

Not checked — the `gh` CLI is not installed in this environment.
