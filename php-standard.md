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

### Math

- **Feat**: Check casting of object for is_numeric
  - https://bugs.php.net/bug.php?id=46524 - is_numeric doesn't take objects as parameter

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

- **Doc**: Better document is_callable
  - https://bugs.php.net/bug.php?id=70088 - is_callable() doesn't check if a class/method syntax is valid

## Changes

### 2023-01

- **Bug**: Mail() function not working correctly in PHP 8.x
  - https://github.com/php/php-src/issues/8086