# PHP main TODO

## Source issues

### SAPI

- **Bug**: Look to explicitly enabling chroot only for some SAPI's
  - https://github.com/php/php-src/issues/11984 - The chroot() doesn't get properly enabled/disabled when building SAPIs
- **Bug**: Fix incorrect counting of max_input_vars
  - https://bugs.php.net/bug.php?id=60707 - max_input_vars allows one extra var
- **Feat**: Do not set charset for some mime type that do not support it
  - https://github.com/php/php-src/issues/11146 - SAPI should not add charset to each text subtype
- **Feat**: Look to API for populating post data for other methods (will require RFC)
  - https://github.com/php/php-src/pull/11472 - Add populate_post_data() function


## Docs

- **Doc**: better $_SERVER docs
  - https://bugs.php.net/bug.php?id=74424 - $_SERVER documentation page needs improvement

