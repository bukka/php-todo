# PHP Standard extension related tasks

## Source issues

### Arrays

- **Bug**: Check current return value
  - https://bugs.php.net/bug.php?id=74724 - current returns false but each returns value

### File

- **Feat**: Refactore php_fgetcsv - horrible and flaky code (it can be optimized)
- **Feat**: Introduce new parameter for file lock in various functions
  - https://github.com/php/php-src/pull/11254 - make FILE_ constants not collide with LOCK_
- **Feat**: Look how to make optional suffix work on Win and be more acceptable
 - https://github.com/php/php-src/pull/11685 - Standard: Support optional suffix arg in tempnam

### Image

- **Feat**: SVG support in getimagesize()
  - https://bugs.php.net/bug.php?id=71517 - Implement SVG support for getimagesize() and friends _(31 votes)_
- **Feat**: Respecting orientation flag in getimagesize()
  - https://bugs.php.net/bug.php?id=66516 - getimagesize() should cater to orientation flag _(3 votes)_
- **Feat**: Support strem resources in getimagesize()
  - https://bugs.php.net/bug.php?id=68499 - getimagesize could support stream resources _(1 vote)_

### Mail

- **Bug**: mail() should not return true if fails (Windows related)
  - https://bugs.php.net/bug.php?id=43327 - wrong return value from mail(), if sendmail_path is wrong _(8 votes)_
- **Bug**: possible issue with preventing mail.force_extra_parameters to be set in PHP_INI_PERDIR
  - https://bugs.php.net/bug.php?id=71901 - mail.force_extra_parameters is not PHP_INI_PERDIR _(5 votes)_
- **Bug**: Look to `$message` filtering options - possibly some new INI
  - https://github.com/php/php-src/issues/12632 - mail() truncates message on full stop between two newlines
- **Feat**: Allow $to being NULL to skip `To:` header
  - https://bugs.php.net/bug.php?id=44170 - mail() function arguments ambiguity _(1 vote)_
- **Feat**: Allow internatiaonlized names on Windows mail()
  - https://bugs.php.net/bug.php?id=81615 - Windows mail should support internationalized email _(3 votes)_

### Math

- **Feat**: Check casting of object for is_numeric
  - https://bugs.php.net/bug.php?id=46524 - is_numeric doesn't take objects as parameter

### Network

- **Feat**: Add new function to display response text (something like http_response_code but for text)
  - https://bugs.php.net/bug.php?id=68219 - Make http_response_code() also returns the text of response _(1 vote)_

### Proc

- **Feat**: Add function num_cpus that returns number of cpu (interface discussion)
  - https://github.com/php/php-src/pull/11137 - feat: add function num_cpus (formerly nproc)

### Serialization and export

- **Bug**: Proper handling of serialization locking
  - https://github.com/php/php-src/pull/5039 - Properly handle serialization locking
- **Bug**: Look to wekup issue
  - https://github.com/php/php-src/issues/9618 - unserialize __wakeup bypass
  - https://github.com/php/php-src/issues/9936 - PHP unserialize bypass wakeup 8.1.1-fpm version
- **Bug**: Serialization duplication of circular references
  - https://github.com/php/php-src/issues/11743 - Seralize incorrectly duplicates element in case of circular reference in array
- **Bug**: Unserialization extra memory usage
  - https://github.com/php/php-src/issues/10126 - Unserialized objects use significantly more memory than ones created with the normal constructor
- **Feat**: Reduce memory for packed arrays
  - https://github.com/php/php-src/pull/7691 - Reduce memory usage when unserializing packed arrays of size 1
- **Feat**: Look to handling of promoted properties during serialization
  - https://github.com/php/php-src/issues/11354 - promoted property in serialized object behaves unexpected
  - https://github.com/php/php-src/issues/11489 - Allow optional promoted class properties to come before required
- **Feat**: var export formatting option to use brackets
  - https://bugs.php.net/bug.php?id=76811 - Add option to var_export so arrays use brackets []

### String
 
- **Bug**: Fix implode() function signature (BC breaking)
  - https://github.com/php/php-src/pull/11991 - Fix implode() function signature

### Type

- **Feat**: Introduce keyval function for key casting
  - https://bugs.php.net/bug.php?id=70378 - keyval (=effective value as array key) to complement strval/intval


## Docs

- **Doc**: Types - Better document is_callable
  - https://bugs.php.net/bug.php?id=70088 - is_callable() doesn't check if a class/method syntax is valid
  - https://bugs.php.net/bug.php?id=60984 - Document output buffering mechanism
- **Doc**: Mail - Document introduction of mail.mixed_lf_and_crlf INI and previous CRLF changes
 - https://bugs.php.net/bug.php?id=81158 - Mails sent by mail function broken since PHP 8.0
- **Doc**: Mail - Fix mail function example
  - https://bugs.php.net/bug.php?id=70082 - mail() function description should provide right example of multi-part mail

## Changes

### 2023-01

- **Bug**: Mail() function not working correctly in PHP 8.x
  - https://github.com/php/php-src/issues/8086