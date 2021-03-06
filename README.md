<h1 align="center">ramsey/php-library-coding-standard</h1>

<p align="center">
    <strong>A common coding standard for Ramsey's PHP libraries.</strong>
</p>

<p align="center">
    <a href="https://github.com/ramsey/php-library-coding-standard"><img src="http://img.shields.io/badge/source-ramsey/php--library--coding--standard-blue.svg?style=flat-square" alt="Source Code"></a>
    <a href="https://packagist.org/packages/ramsey/php-library-coding-standard"><img src="https://img.shields.io/packagist/v/ramsey/php-library-coding-standard.svg?style=flat-square&label=release" alt="Download Package"></a>
    <a href="https://php.net"><img src="https://img.shields.io/packagist/php-v/ramsey/php-library-coding-standard.svg?style=flat-square&colorB=%238892BF" alt="PHP Programming Language"></a>
    <br>
    <a href="https://github.com/ramsey/php-library-coding-standard/blob/master/LICENSE"><img src="https://img.shields.io/packagist/l/ramsey/php-library-coding-standard.svg?style=flat-square&colorB=darkcyan" alt="Read License"></a>
    <a href="https://github.com/ramsey/php-library-coding-standard/actions?query=workflow%3Amain"><img src="https://img.shields.io/github/workflow/status/ramsey/php-library-coding-standard/main?logo=github&style=flat-square" alt="Build Status"></a>
    <a href="https://packagist.org/packages/ramsey/php-library-coding-standard/stats"><img src="https://img.shields.io/packagist/dt/ramsey/php-library-coding-standard.svg?style=flat-square&colorB=darkmagenta" alt="Package downloads on Packagist"></a>
    <a href="https://phpc.chat/channel/ramsey"><img src="https://img.shields.io/badge/phpc.chat-%23ramsey-darkslateblue?style=flat-square" alt="Chat with the maintainers"></a>
</p>

## About

This is a custom coding standard for [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer).
It borrows many sniffs from [Slevomat Coding Standard](https://github.com/slevomat/coding-standard)
and combines them into a single unified, common standard for Ramsey's PHP
libraries.

This project adheres to a [code of conduct](CODE_OF_CONDUCT.md).
By participating in this project and its community, you are expected to
uphold this code.

## Installation

Install this package as a dependency using [Composer](https://getcomposer.org).

``` bash
composer require --dev ramsey/php-library-coding-standard
```

## Usage

To use this coding standard, add `<rule ref="Ramsey"/>` to your `phpcs.xml`
configuration.

Here are the contents of an example `phpcs.xml.dist` file that you may place in
the root of your repository:

``` xml
<?xml version="1.0"?>
<ruleset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="vendor/squizlabs/php_codesniffer/phpcs.xsd">

    <arg name="extensions" value="php"/>
    <arg name="colors"/>
    <arg value="sp"/>

    <file>./src</file>
    <file>./tests</file>

    <rule ref="Ramsey"/>

</ruleset>
```

Then, run PHP_CodeSniffer:

```bash
./vendor/bin/phpcs
```

## Contributing

Contributions are welcome! Before contributing to this project, familiarize
yourself with [CONTRIBUTING.md](CONTRIBUTING.md).

To develop this project, you will need [PHP](https://www.php.net) 7.4 or greater
and [Composer](https://getcomposer.org).

After cloning this repository locally, execute the following commands:

``` bash
cd /path/to/repository
composer install
```

Now, you are ready to develop!

### Tooling

This project uses [CaptainHook](https://github.com/CaptainHookPhp/captainhook)
to validate all staged changes prior to commit.

#### Composer Commands

To see all the commands available in the project `br` namespace for
Composer, type:

``` bash
composer list br
```

##### Composer Command Autocompletion

If you'd like to have Composer command auto-completion, you may use
[bamarni/symfony-console-autocomplete](https://github.com/bamarni/symfony-console-autocomplete).
Install it globally with Composer:

``` bash
composer global require bamarni/symfony-console-autocomplete
```

Then, in your shell configuration file — usually `~/.bash_profile` or `~/.zshrc`,
but it could be different depending on your settings — ensure that your global
Composer `bin` directory is in your `PATH`, and evaluate the
`symfony-autocomplete` command. This will look like this:

``` bash
export PATH="$(composer config home)/vendor/bin:$PATH"
eval "$(symfony-autocomplete)"
```

Now, you can use the `tab` key to auto-complete Composer commands:

``` bash
composer br:[TAB][TAB]
```

#### Coding Standards

This project follows a superset of [PSR-12](https://www.php-fig.org/psr/psr-12/)
coding standards, enforced by [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer).
The project PHP_CodeSniffer configuration may be found in `phpcs.xml.dist`.

CaptainHook will run PHP_CodeSniffer before committing. It will attempt to fix
any errors it can, and it will reject the commit if there are any un-fixable
issues. Many issues can be fixed automatically and will be done so pre-commit.

You may lint the entire codebase using PHP_CodeSniffer with the following
commands:

``` bash
# Lint
composer br:lint

# Lint and autofix
composer br:lint:fix
```

#### Static Analysis

This project uses a combination of [PHPStan](https://github.com/phpstan/phpstan)
and [Psalm](https://github.com/vimeo/psalm) to provide static analysis of PHP
code. Configurations for these are in `phpstan.neon.dist` and `psalm.xml`,
respectively.

CaptainHook will run PHPStan and Psalm before committing. The pre-commit hook
does not attempt to fix any static analysis errors. Instead, the commit will
fail, and you must fix the errors manually.

You may run static analysis manually across the whole codebase with the
following command:

``` bash
# Static analysis
composer br:analyze
```

### Project Structure

This project uses [pds/skeleton](https://github.com/php-pds/skeleton) as its
base folder structure and layout.

| Name              | Description                                    |
| ------------------| ---------------------------------------------- |
| **bin/**          | Commands and scripts for this project          |
| **build/**        | Cache, logs, reports, etc. for project builds  |
| **src/**          | Project library and application source code    |
| **tests/**        | Tests for this project                         |

## Copyright and License

The ramsey/php-library-coding-standard library is copyright © [Ben Ramsey](https://benramsey.com)
and licensed for use under the terms of the
MIT License (MIT). Please see [LICENSE](LICENSE) for more information.
