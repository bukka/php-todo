# PHP Streams tasks

## Source issues

- **Bug**: fread blocking unpredictible
  - https://bugs.php.net/bug.php?id=51056 - fread() on blocking stream will block even if data is available
  - https://bugs.php.net/bug.php?id=52602 - fread is blocking even with the use of stream_select
- **Bug**: Possible issue with pipes and select in fread and similar
  - https://bugs.php.net/bug.php?id=66232 - proc_open: Inconsistent handling of EOFs on pipes
- **Bug**: Issue with stream_select ignoring proc_open streams
  - https://bugs.php.net/bug.php?id=75584 - Docs?: stream_select() ignores proc_open() streams for buffered fopen() streams
- **Bug**: Investigate stream_select after fork issue
  - https://bugs.php.net/bug.php?id=75749 - pcntl_fork does not duplicate stream_sockets
- **Bug**: stream_select on freebsd possibly incorrect
  - https://bugs.php.net/bug.php?id=60186 - stream_select ignores the timeout on freebsd
- **Bug**: Polling should stop on EINTR
  - https://bugs.php.net/bug.php?id=79564 - poll() cannot be interrupted
  - https://github.com/php/php-src/pull/5521 - Don't continue polling on EINTR
- **Bug**: Not able to identify error for stream_socket_client with STREAM_CLIENT_ASYNC_CONNECT
  - https://bugs.php.net/bug.php?id=64803 - async stream_socket_client return
- **Bug**: Look to potentially incorrect seeking of stream wrappers
  - https://bugs.php.net/bug.php?id=72561 - https://bugs.php.net/bug.php?id=72561
- **Bug**: Seeking past the end on memory stream does not work
  - https://bugs.php.net/bug.php?id=52335  - fseek() on memory stream behavior different then file
  - https://github.com/php/php-src/issues/9441 - fseek does not work with php://input even though the stream is advertised as seekable
**Feat**: Check correctness of updating position on the stream if it works for all streams
  - https://github.com/php/php-src/pull/7354 - Fix #81302: Stream position after stream filter removed 
  - https://github.com/php/php-src/pull/7356 - Fix #81346: Non-seekable streams don't update position after write
**Feat**: Look to refactoring fd seeking related to new changes
  - https://github.com/php/php-src/pull/8540 - main/streams/plain_wrapper: skip lseek(SEEK_CUR) for newly opened files
- **Bug**: Detection IO error in php_fopen_wrapper_for_zend
  - https://bugs.php.net/bug.php?id=71385 - require* and include* do not detect input/output error
- **Bug**: Issue with reading image info in getimagesize with StreamWrappers
  - https://bugs.php.net/bug.php?id=75708 - getimagesize with "&$imageinfo" fails on StreamWrappers
- **Bug**: fopencookie issue visible in imagecreatefrompng
  - https://bugs.php.net/bug.php?id=79945 - using php wrappers in imagecreatefrompng causes segmentation fault
- **Bug**: File existence check should be false for unsupported protocol
  - https://bugs.php.net/bug.php?id=76857 - Can read “non-existant” files
- **Bug**: Possibly incorrect return value from fclose and similar
  - https://bugs.php.net/bug.php?id=60110 - fclose(), file_put_contents(), copy() do not return false properly
- **Bug**: Look to the clearing stat cache after touch()
  - https://bugs.php.net/bug.php?id=72666 - touch(): stat cache clearing inconsistent between file:// paths and plain paths
- **Feat**: Option to disable stat cache
  - https://bugs.php.net/bug.php?id=28790 - Add php.ini option to disable stat cache
  - https://github.com/php/php-src/pull/5894 - Feature Request #28790 Add php.ini option to disable stat cache
- **Bug**: Look to altering default context when https request goes through http proxy
  - https://bugs.php.net/bug.php?id=74796 - Requests through https:// with http proxy set altering default context
- **Feat**: Look to support for select on filtered streams
  - https://github.com/php/php-src/pull/6926 - Allow to cast filtered streams to PHP_STREAM_AS_FD_FOR_SELECT
- **Bug**: HTTP 1/1 steram hangs due to server not closing - unresolve issue with stream_select
  - https://bugs.php.net/bug.php?id=80931 - file_get_contents() hangs with HTTP/1.1 if server doesn't close connection
  - https://github.com/php/php-src/pull/6874 - Fix #80931: HTTP stream hangs if server doesn't close connection
- **Bug**: Handling HTTP 304 in copy and others
  - https://bugs.php.net/bug.php?id=67351 - copy() should handle HTTP 304 response
  - https://github.com/php/php-src/pull/6177 - Fix #67351: copy() should handle HTTP 304 response
- **Feat**: Set IP(6)_RECVERR on connected datagram
  - https://github.com/php/php-src/pull/8635 -  set IP(6)_RECVERR on connected datagram sockets
- **Bug**: Issue with user stream filter after destruction
  - https://bugs.php.net/bug.php?id=75931 - User stream filter is used after destruction
- **Bug**: Socket metadata are inherited
  - https://github.com/php/php-src/issues/8472 - The resource returned by stream_socket_accept may have incorrect metadata
- **Bug**: Look to a proper fix for socket name
  - https://bugs.php.net/bug.php?id=74556 - stream_socket_get_name returns \0 string instead of false
- **Feat**: Make STREAM_NOTIFY_COMPLETED work
  - https://github.com/php/php-src/issues/8641 - STREAM_NOTIFY_COMPLETED over HTTP never emitted
- **Feat**: Glob stream wrapper support
  - https://github.com/php/php-src/issues/9224 - StreamWrapper support for glob()

## Docs

- **Doc**: Better document stream_select behaviour for passed array streams
  - https://bugs.php.net/bug.php?id=70099 - stream_select() reverts to previous behavior of not preserving keys after read
- **Doc**: Improve and clarify stream_set_option docs
  - https://bugs.php.net/bug.php?id=78375 - stream_set_option method of stream wrapper is now called inside require()
- **Doc**: Document stream_bucket_new
  - https://bugs.php.net/bug.php?id=78258 - stream_bucket_new does not have documentation
- **Doc**: Note that ftell on character device fails
  - https://bugs.php.net/bug.php?id=79389 - ftell retruns false on linux for STDIN
- **Doc**: Document fseek quirks
  - https://bugs.php.net/bug.php?id=76995 - fseek() breaks reading in read/append (a+) mode
- **Doc**: Properly document compression filters
  - https://bugs.php.net/bug.php?id=68556 - Fix for zlib.deflate and zlib.inflate filters; fix for example #1
- **Doc**: Document opendir behavior on Windows related required access
  - https://bugs.php.net/bug.php?id=43817 - opendir() fails on Windows directories with parent directory unaccessible
- **Doc**: Document failed opening COMn on Windowns
  - https://bugs.php.net/bug.php?id=66943 - Can't open COM10 or higher serial ports
- 



## Changes

### 2022-07
- **Bug**: Fix open_basedir check in GlobIterator and glob:// stream
  - https://github.com/php/php-src/commit/1a9e6895f1d203f38655b52d5b6b823be7d14cbd
- **Feat**: Allow not close stream on rscr dtor in php cli sapi
  - https://github.com/php/php-src/pull/8833