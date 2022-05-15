# PHP Streams tasks

## Source issues

- Remove poll when MSG_DONTWAIT available
  - https://github.com/php/php-src/pull/8092 - streams/xp_socket: eliminate poll() when MSG_DONTWAIT is available
- Socket metadata are inherited
  - https://github.com/php/php-src/issues/8472 - The resource returned by stream_socket_accept may have incorrect metadata