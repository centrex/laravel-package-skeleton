# CLAUDE.md

## Package Overview

`laravel-package-skeleton` — Template/scaffold for creating new Laravel packages in this monorepo.

Namespace: `VendorName\Skeleton\` (replace with actual vendor/package name)

This is the reference template. When creating a new package, copy this directory and do a find-and-replace on `VendorName`, `Skeleton`, `skeleton`, and `package-description`.

## Commands

Run from inside the new package directory:

```sh
composer install          # install dependencies
composer test             # full suite: rector dry-run, pint check, phpstan, pest
composer test:unit        # pest tests only
composer test:lint        # pint style check (read-only)
composer test:types       # phpstan static analysis
composer test:refacto     # rector refactor check (read-only)
composer lint             # apply pint formatting
composer refacto          # apply rector refactors
composer analyse          # phpstan (alias)
composer build            # prepare testbench workbench
composer start            # build + serve testbench dev server
```

## Standard Structure

```
src/
  <Name>.php                    # Main class (logic entry point)
  <Name>ServiceProvider.php     # Registers config, routes, migrations, views, commands
  Facades/<Name>.php            # Laravel facade
  Commands/
config/config.php
database/
  migrations/
  factories/
  seeders/
tests/
  Pest.php
  TestCase.php                  # Extends Orchestra\Testbench\TestCase
  ArchTest.php
workbench/                      # Testbench dev app
```

## Checklist when creating a new package

1. Replace all `VendorName\Skeleton` namespace references
2. Update `composer.json` name, description, and autoload namespace
3. Rename `Skeleton.php` and `SkeletonServiceProvider.php`
4. Update `config/config.php` key to match package slug
5. Register service provider in `TestCase.php`

## Conventions

- PHP 8.2+, `declare(strict_types=1)` in all files
- Pest for tests, snake_case test names
- Pint with `laravel` preset
- Rector targeting PHP 8.3 with `CODE_QUALITY`, `DEAD_CODE`, `EARLY_RETURN`, `TYPE_DECLARATION`, `PRIVATIZATION` sets
- PHPStan at level `max` with Larastan
