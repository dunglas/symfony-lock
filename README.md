Locking a Symfony Project to a Specific Major Version of the Framework
======================================================================

Using `symfony/symfony` makes Composer install all Symfony Components, all in
the same version. But when using the standalone packages (the Symfony Flex way),
Composer might install dependencies in a different major version (`symfony/http-kernel`
v2.8 and `symfony/event-dispatcher` v3.4 for instance, usually because another
dependency of the project is not compatible with Symfony 3.0).

This Composer package allows you to enforce a consistent major version on all
Symfony Components, whether they are explicitly listed as a project's
dependency or installed transitively.

For instance when using `dunglas/symfony-lock:^4`, if a package cannot be installed
in v4.0, but only in v3.4 (usually because of another library not supporting Symfony
4), a conflict will be generated.

Note that this package is meant to be used by library authors in their continuous
integration systems. It should NOT be added directly to the project's
`composer.json`.


Difference with `symfony/lts`
-----------------------------

`symfony/lts` enforces that your project doesn't use a version not released
as a LTS, but does not enforce that all your Symfony packages are in the same
major version. For instance, when using `symfony/lts` v3, some packages
can be installed in version 3.4, and some others in version 2.8.

Usage
-----

Use the Composer command line:

```bash
composer require dunglas/symfony-lock v4
```
