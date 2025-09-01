# Opcache issue

- **Bug**: Investigate and fix opcache_reset parallel issue
  - https://github.com/php/php-src/issues/14471 - Crash with opcache_reset() under high load in fpm
- **Bug**: Investigate bypass of user error handler
  - https://github.com/php/php-src/issues/17422 - OPcache bypasses the user-defined error handler for deprecations