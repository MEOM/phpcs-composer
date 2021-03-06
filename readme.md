# MEOM PHPCS ruleset

This is a standalone composer package for Custom [WPCS](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards) and [PHPCompatibilityWP](https://github.com/PHPCompatibility/PHPCompatibilityWP)  rulesets.

## Requirements

* PHP 7+.
* [Composer](https://getcomposer.org/) for managing PHP dependencies.

## Installation

Use Composer to install the package.

```bash
composer require --dev meom/phpcs-composer:dev-main
```

## Usage

Lint your PHP files with the following command:

```bash
./vendor/bin/phpcs .
```

Or give path to lint theme folder, for example:

```bash
./vendor/bin/phpcs htdocs/wp-content/themes/theme-name
```

Note that by default warning are not displayed. You can change that with `--severity` flag like this:

```bash
./vendor/bin/phpcs --severity=1 htdocs/wp-content/themes/theme-name
```

## Fixing issues using PHPCBF command

Some of the issue can be fixed using `phpcbf` command:

```bash
./vendor/bin/phpcbf .
```

Or give path to fix theme folder, for example:

```bash
./vendor/bin/phpcbf htdocs/wp-content/themes/theme-name
```

Note that by default warnings are not fixed. You can fix warnings also  with `--severity` flag like this:

```bash
./vendor/bin/phpcbf --severity=1 htdocs/wp-content/themes/theme-name
```

More info about [fixing PHPCS errors automatically](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Fixing-Errors-Automatically).

## IDE Integration

Some IDE integrations of PHPCS fail to register the MEOM-default ruleset. In order to rectify this, place `.phpcs.xml.dist` at your project root:

```xml
<?xml version="1.0"?>
<ruleset name="Project Rules">
    <rule ref="MEOM-default" />
</ruleset>
```

Note this is already added in Kala Stack.

### VS Code

If you don't have PHP codesniffer installed globally, you might need to

1. Create folder `.vscode` (in the root of the project).
1. Add file `settings.json` in the folder.
1. Add the following content in the file.

```json
{
    "phpcs.executablePath": "./vendor/bin/phpcs"
}
```

P.S. Windows is looking for file `./vendor/bin/phpcs.bat`. If that's not generated automatically in `./vendor/bin/` for some reason, test path `./vendor/squizlabs/php_codesniffer/bin/phpcs`.

`.bat` files should be in that folder.
