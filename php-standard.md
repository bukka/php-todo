# PHP Standard extension related tasks

## Serialization

- **Bug**: Look to wekup issue
  - https://github.com/php/php-src/issues/9936 - PHP unserialize bypass wakeup 8.1.1-fpm version
- **Bug**: Unserialization extran memory usage
  - https://github.com/php/php-src/issues/10126 - Unserialized objects use significantly more memory than ones created with the normal constructor

## Changes

### 2023-01

- **Bug**: Mail() function not working correctly in PHP 8.x
  - https://github.com/php/php-src/issues/8086