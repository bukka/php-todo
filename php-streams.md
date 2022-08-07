# PHP Streams tasks

## Source issues

- **Bug**: fread blocking unpredictible
  - https://bugs.php.net/bug.php?id=51056 - fread() on blocking stream will block even if data is available
- **Bug**: possible issue with pipes and select in fread and similar
  - https://bugs.php.net/bug.php?id=66232 - proc_open: Inconsistent handling of EOFs on pipes
- **Bug**: stream_select on freebsd possibly incorrect
  - https://bugs.php.net/bug.php?id=60186 - stream_select ignores the timeout on freebsd
- **Bug**: Possibly incorrect return value from fclose and similar
  - https://bugs.php.net/bug.php?id=60110 - fclose(), file_put_contents(), copy() do not return false properly
- **Bug**: Not able to identify error for stream_socket_client with STREAM_CLIENT_ASYNC_CONNECT
  - https://bugs.php.net/bug.php?id=64803 - async stream_socket_client return
- **Bug**: Seeking past the end on memory stream does not work
  - https://bugs.php.net/bug.php?id=52335  - fseek() on memory stream behavior different then file
- **Bug**: HTTP 1/1 steram hangs due to server not closing - unresolve issue with stream_select
  - https://bugs.php.net/bug.php?id=80931 - file_get_contents() hangs with HTTP/1.1 if server doesn't close connection
  - https://github.com/php/php-src/pull/6874 - Fix #80931: HTTP stream hangs if server doesn't close connection
- **Feat**: Set IP(6)_RECVERR on connected datagram
  - https://github.com/php/php-src/pull/8635 -  set IP(6)_RECVERR on connected datagram sockets
- **Bug**: Socket metadata are inherited
  - https://github.com/php/php-src/issues/8472 - The resource returned by stream_socket_accept may have incorrect metadata
- **Feat**: Make STREAM_NOTIFY_COMPLETED work
  - https://github.com/php/php-src/issues/8641 - STREAM_NOTIFY_COMPLETED over HTTP never emitted



## Changes

### 2022-06
- **Feat**: Allow not close stream on rscr dtor in php cli sapi
  - https://github.com/php/php-src/pull/8833