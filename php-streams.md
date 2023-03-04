# PHP Streams tasks

## Source issues

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
- **Feat**: Check correctness of updating position on the stream if it works for all streams
  - https://github.com/php/php-src/pull/7354 - Fix #81302: Stream position after stream filter removed 
  - https://github.com/php/php-src/pull/7356 - Fix #81346: Non-seekable streams don't update position after write
- **Feat**: Look to refactoring fd seeking related to new changes
  - https://github.com/php/php-src/pull/8540 - main/streams/plain_wrapper: skip lseek(SEEK_CUR) for newly opened files
- **Bug**: Detection IO error in php_fopen_wrapper_for_zend
  - https://bugs.php.net/bug.php?id=71385 - require* and include* do not detect input/output error
- **Bug**: Issue with reading image info in getimagesize with StreamWrappers
  - https://bugs.php.net/bug.php?id=75708 - getimagesize with "&$imageinfo" fails on StreamWrappers
- **Bug**: fopencookie issue visible in imagecreatefrompng
  - https://bugs.php.net/bug.php?id=79945 - using php wrappers in imagecreatefrompng causes segmentation fault
- **Bug**: Investigate custom stream wrappers issue with dynamic properties and FFI
  - https://github.com/php/php-src/issues/9698 - stream_wrapper_register crashes with FFI\CData provided as class
- **Bug**: File existence check should be false for unsupported protocol
  - https://bugs.php.net/bug.php?id=76857 - Can read “non-existant” files
- **Bug**: Investigate data loss warning correctnes for supported stream wrappers
  - https://github.com/php/php-src/pull/10093 - Fix GH-10092 (Internal stream casting should not emit lost bytes warning twice)
- **Bug**: Possibly incorrect return value from fclose and similar
  - https://bugs.php.net/bug.php?id=60110 - fclose(), file_put_contents(), copy() do not return false properly
- **Bug**: Look to the clearing stat cache after touch()
  - https://bugs.php.net/bug.php?id=72666 - touch(): stat cache clearing inconsistent between file:// paths and plain paths
- **Feat**: Option to disable stat cache
  - https://bugs.php.net/bug.php?id=28790 - Add php.ini option to disable stat cache
  - https://github.com/php/php-src/pull/5894 - Feature Request #28790 Add php.ini option to disable stat cache
- **Bug**: Look to altering default context when https request goes through http proxy
  - https://bugs.php.net/bug.php?id=74796 - Requests through https:// with http proxy set altering default context
- **Bug**: HTTP 1/1 steram hangs due to server not closing - unresolve issue with stream_select
  - https://bugs.php.net/bug.php?id=80931 - file_get_contents() hangs with HTTP/1.1 if server doesn't close connection
  - https://github.com/php/php-src/pull/6874 - Fix #80931: HTTP stream hangs if server doesn't close connection
- **Bug**: Handling HTTP 304 in copy and others
  - https://bugs.php.net/bug.php?id=67351 - copy() should handle HTTP 304 response
  - https://github.com/php/php-src/pull/6177 - Fix #67351: copy() should handle HTTP 304 response
- **Bug**: Issue with user stream filter after destruction
  - https://bugs.php.net/bug.php?id=75931 - User stream filter is used after destruction
- **Bug**: Socket metadata are inherited
  - https://github.com/php/php-src/issues/8472 - The resource returned by stream_socket_accept may have incorrect metadata
- **Bug**: Look to a proper fix for socket name
  - https://bugs.php.net/bug.php?id=74556 - stream_socket_get_name returns \0 string instead of false
- **Feat**: Look to addition solution for preserving socket errors and error notifications in general
  - https://bugs.php.net/bug.php?id=42387 - Streams layer has no error notification facility _(2 votes)_
  - https://bugs.php.net/bug.php?id=34380 - need stream equivalent to socket_last_error _(12 votes)_
  - https://github.com/php/php-src/pull/838 - preserve errno for stream_select and stream_socket_pair
  - https://github.com/php/php-src/issues/10109 - Change error code of fsockopen from E_WARNING to EXCEPTION
- **Feat**: Consider some additional socket functions
  - https://bugs.php.net/bug.php?id=49416 - Add stream_socket_listen() and stream_socket_set_option() functions
- **Feat**: Changing pipes streams logic to match logic for sockets
  - https://github.com/php/php-src/issues/10171 - Streams blocking read and EOF handling for pipes
  - https://bugs.php.net/bug.php?id=33781 - add "stream_set_timeout" support for pipes
  - https://bugs.php.net/bug.php?id=54717 - stream_set_timeout doesn't work for STDIO streams
  - https://bugs.php.net/bug.php?id=66232 - proc_open: Inconsistent handling of EOFs on pipes
- **Feat**: Look to improving support for descriptors
  - https://github.com/php/php-src/issues/9551 - File descriptors / some procfs entries not openable by php
- **Feat**: Look to the fopen wrapper better support for FTP SIZE command
  - https://bugs.php.net/bug.php?id=48674 - fopen() ftp wrapper and SIZE command _(11 votes)_
- **Feat**: Support FTP EPSV command
  - https://bugs.php.net/bug.php?id=69580 - I need an FTP stream that doesn't use EPSV _(1 vote)_
- **Feat**: Reuse FTP connection
  - https://bugs.php.net/bug.php?id=72343 - FTP wrapper should re-use connections
- **Feat**: Consider failing when opening a directory using fopen()
  - https://bugs.php.net/bug.php?id=69163 - `fopen(__DIR__, 'r')` succeeds _(1 vote)_
- **Feat**: Support fwrite buffering
  - https://bugs.php.net/bug.php?id=61168 - fwrite() should allow for buffering _(5 votes)_
- **Feat**: Impleemnt stream_select checking of other streams when read buffered stream present
  - https://github.com/php/php-src/issues/10177 - stream_select checking of other streams when read buffered stream present
  - https://bugs.php.net/bug.php?id=75584 - Docs?: stream_select() ignores proc_open() streams for buffered fopen() streams
- **Feat**: Look to support for select on filtered streams
  - https://github.com/php/php-src/pull/6926 - Allow to cast filtered streams to PHP_STREAM_AS_FD_FOR_SELECT
- **Feat**: Support filters on STDOUT
  - https://bugs.php.net/bug.php?id=34666 - print and echo do not apply filters on STDOUT _(1 vote)_
- **Feat**: Support nonblocking STDIN on Windows
  - https://bugs.php.net/bug.php?id=34972 - STDIN should allow nonblocking _(179 votes)_
- **Feat**: Improve stream_get_line to get rid of length limit
  - https://bugs.php.net/bug.php?id=48421 - stream_get_line() - allow $length to be optional _(5 votes)_
- **Feat**: Support setting of connection timeout
  - https://bugs.php.net/bug.php?id=36072 - stream_set_connection_timeout() _(2 votes)_
- **Feat**: Improve error reporting for php_network_addresses()
  - https://bugs.php.net/bug.php?id=71641 - Proper error-reporting in php_network_addresses() calls 
- **Feat**: Set IP(6)_RECVERR on connected datagram
  - https://github.com/php/php-src/pull/8635 -  set IP(6)_RECVERR on connected datagram sockets
- **Feat**: Support multiple persistent connections on UDS
  - https://bugs.php.net/bug.php?id=63293 - Add support to establish > 1 persistent connection to the same UNIX socket _(7 votes)_
- **Bug**: Look to the issue with occasionally missing STREAM_NOTIFY_PROGRESS on Win
  - https://github.com/php/php-src/issues/10031 - STREAM_NOTIFY_PROGRESS over HTTP emitted irregularly for last chunk of data
- **Feat**: Make stream notifications properly work on TCP
  - https://bugs.php.net/bug.php?id=52811 - the notification callback method never gets call when using socket streams _(9 votes)_
  - https://bugs.php.net/bug.php?id=63556 - stream_notification_callback _(1 vote)_
  - https://github.com/php/php-src/issues/8641 - STREAM_NOTIFY_COMPLETED over HTTP never emitted
- **Feat**: Look to supporting upload progress notification for things like HTTP POST
  - https://bugs.php.net/bug.php?id=80124 - HTTP stream contexts missing upload progress notification _(1 vote)_
- **Feat**: Support some additional methods for stream wrappers
  - https://bugs.php.net/bug.php?id=38025 - Missing stream wrapper methods _(12 votes)_
- **Feat**: Look to the LOCK_EX support for stream wrappers
  - https://bugs.php.net/bug.php?id=61201 - LOCK_EX in file_put_contents with custom streamwrapper fails _(4 votes)_
- **Feat**: Look to the ways of restoring of origin wrapper
  - https://bugs.php.net/bug.php?id=42929 - Cannot access the old stream wrapper from a wrapper class _(2 votes)_
- **Feat**: Glob stream wrapper support
  - https://github.com/php/php-src/issues/9224 - StreamWrapper support for glob()
- **Feat**: Allow colon only scheme (not requiring //)
  - https://bugs.php.net/bug.php?id=36678 - Use of URL like about:config in streams _(2 votes)_
- **Feat**: Consider ability to set default context options from ini
  - https://bugs.php.net/bug.php?id=70038 - peer verification needs to be a global option _(1 vote)_
- **Feat**: Investigate disabling temp_file for input stream
  - https://github.com/php/php-src/issues/8239 - For php://input fread() writes temp files
- **Feat**: Investigate multipart support for stream input
  - https://bugs.php.net/bug.php?id=76444 - can't read stream from multipart requests _(1 vote)_
- **Feat**: Investigate alternative / setting of http_response_header in relation to custom http stream wrapper
  - https://bugs.php.net/bug.php?id=63897 - Custom http stream wrappers should be able to set $http_response_header _(3 votes)_
- **Feat**: Support relative redirects in http stream wrapper
  - https://bugs.php.net/bug.php?id=64582 - file_get_contents() handles redirects wrong
- **Feat**: Support setting protocol version (consider future support for HTTP 2)
  - https://github.com/php/php-src/issues/8832 - Support "protocol_version" stream context option for proxy connections
- **Feat**: HTTP 2 support
  - https://bugs.php.net/bug.php?id=76625 - Support http2 in file_get_contents() and friends _(5 votes)_
- **Feat**: WinSSL support
  - https://bugs.php.net/bug.php?id=77505 - streams/HTTPS cannot be used with WinSSL/schannel _(2 votes)_

## Docs


- **Doc**: Better document stream_copy_to_stream
  - https://github.com/php/php-src/issues/9994 - stream_copy_to_stream() returns on socket timeout
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

### 2023-02

- **Bug**: Investigate stream_select after fork issue
  - https://bugs.php.net/bug.php?id=75749 - pcntl_fork does not duplicate stream_sockets

### 2022-10

- **Bug**: fread blocking unpredictible
  - https://bugs.php.net/bug.php?id=51056 - fread() on blocking stream will block even if data is available
  - https://bugs.php.net/bug.php?id=52602 - fread is blocking even with the use of stream_select
### 2022-07
- **Bug**: Fix open_basedir check in GlobIterator and glob:// stream
  - https://github.com/php/php-src/commit/1a9e6895f1d203f38655b52d5b6b823be7d14cbd
- **Feat**: Allow not close stream on rscr dtor in php cli sapi
  - https://github.com/php/php-src/pull/8833