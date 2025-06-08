# PHP Streams tasks

## Source issues

- **Bug**: stream_socket_get_name() IPv6 handling
  - https://github.com/php/php-src/issues/16117 - stream_socket_get_name() can return ipv6 address even when ipv6 is not available
- **Bug**: Fix error issue with fgets() when stream filter fails
  - https://github.com/php/php-src/issues/13264 - fgets() does not return false on error from a zlib.inflate filtered stream with large content and invalid checksum
- **Bug**: Look into proc_open breakage with user stream
  - https://github.com/php/php-src/issues/17943 - Using stream wrappers breaks proc_open
- **Bug**: Make listen non blockign to prevent issues with not respecting timeout
  - https://github.com/php/php-src/issues/13220 - stream_socket_accept() timeout sometimes doesn't work?
- **Bug**: Disable usage of mmap that is causing segfaults
  - https://github.com/php/php-src/issues/13011 - SIGBUS Signal 7 Issue
- **Bug**: Look to the inconsistencies in stream filters seeking
  - https://bugs.php.net/bug.php?id=49874 - ftell() and fseek() inconsistency when using stream filters _(8 votes)_
  - https://github.com/php/php-src/pull/6359 - Disallow seeking on filtered streams
- **Feat**: Look to addition solution for preserving socket errors and error notifications in general
  - https://bugs.php.net/bug.php?id=42387 - Streams layer has no error notification facility _(2 votes)_
  - https://bugs.php.net/bug.php?id=34380 - need stream equivalent to socket_last_error _(12 votes)_
  - https://bugs.php.net/bug.php?id=63793 - Provide direct access to socket errors without php_sockets _(9 votes)_
  - https://bugs.php.net/bug.php?id=64803 - async stream_socket_client return _(2 votes)_
  - https://bugs.php.net/bug.php?id=65679 - stream_socket_client() does not set $errstr _(4 votes)_
  - https://github.com/php/php-src/pull/838 - preserve errno for stream_select and stream_socket_pair
  - https://github.com/php/php-src/issues/10109 - Change error code of fsockopen from E_WARNING to EXCEPTION
- **Feat**: Consider some additional socket functions
  - https://bugs.php.net/bug.php?id=49416 - Add stream_socket_listen() and stream_socket_set_option() functions
- **Feat**: Changing pipes streams logic to match logic for sockets
  - https://github.com/php/php-src/issues/10171 - Streams blocking read and EOF handling for pipes
  - https://bugs.php.net/bug.php?id=33781 - add "stream_set_timeout" support for pipes
  - https://bugs.php.net/bug.php?id=54717 - stream_set_timeout doesn't work for STDIO streams
  - https://bugs.php.net/bug.php?id=66232 - proc_open: Inconsistent handling of EOFs on pipes
- **Feat**: Look to support for closing socket on exec (might be better do it optionally)
  - https://bugs.php.net/bug.php?id=43290 - Proposed new socket function: socket_set_close_on_exec
  - https://bugs.php.net/bug.php?id=67383 - exec() leaks file and socket descriptors to called program (general for all parts of PHP - not good idea)
- **Feat**: Look more to incorrect return value from fclose and similar - specifically in relation to exec
  - https://bugs.php.net/bug.php?id=60110 - fclose(), file_put_contents(), copy() do not return false properly
  - https://github.com/php/php-src/pull/12067 - Fix bug #60110 (fclose(), file_put_contents(), copy() do not return false properly)
- **Feat**: Look to improving support for descriptors
  - https://github.com/php/php-src/issues/9551 - File descriptors / some procfs entries not openable by php
- **Feat**: Consider failing when opening a directory using fopen()
  - https://bugs.php.net/bug.php?id=69163 - `fopen(__DIR__, 'r')` succeeds _(1 vote)_
- **Feat**: Try to finish improvements for _php_stream_copy_to_stream_ex
  - https://github.com/php/php-src/pull/10603 - Improvements to _php_stream_copy_to_stream_ex()
- **Feat**: Look to better non blocking support in _php_stream_copy_to_stream_ex
  - https://github.com/php/php-src/issues/11753 - stream_copy_to_stream returns false when data copied is less than $maxlength
- **Feat**: Support fwrite buffering
  - https://bugs.php.net/bug.php?id=61168 - fwrite() should allow for buffering _(5 votes)_
- **Feat**: Look to possibility of not copying var string but instead introduce cow
  - https://github.com/php/php-src/issues/11106 - Use zval storage for php://memory stream
- **Feat**: Look into copying proc files
  - https://bugs.php.net/bug.php?id=62072 - The "copy" function can't copy files from /proc
- **Feat**: Better handle interuption during polling
  - https://bugs.php.net/bug.php?id=79564 - poll() cannot be interrupted
  - https://github.com/php/php-src/pull/5521 - Don't continue polling on EINTR
- **Feat**: Implement stream_select checking of other streams when read buffered stream present
  - https://github.com/php/php-src/issues/10177 - stream_select checking of other streams when read buffered stream present
  - https://bugs.php.net/bug.php?id=75584 - Docs?: stream_select() ignores proc_open() streams for buffered fopen() streams
- **Feat**: Consider some internal API for allowing external objects to use stream_select
  - https://bugs.php.net/bug.php?id=78613 - Allow using curl handles with stream_select()
- **Feat**: Look to support for select on filtered streams
  - https://github.com/php/php-src/pull/6926 - Allow to cast filtered streams to PHP_STREAM_AS_FD_FOR_SELECT
- **Feat**: Issue with user stream filter after destruction
  - https://bugs.php.net/bug.php?id=75931 - Call stream filter constructor first and destructor last
- **Feat**: Support filters on STDOUT
  - https://bugs.php.net/bug.php?id=34666 - print and echo do not apply filters on STDOUT _(1 vote)_
- **Feat**: Look to not closing STDIN and STDOUT
  - https://github.com/php/php-src/issues/11399 - PHP incorrectly closes file handles when used to replace STDIN/STDOUT/STDERR
- **Feat**: Support nonblocking STDIN on Windows
  - https://bugs.php.net/bug.php?id=34972 - STDIN should allow nonblocking _(179 votes)_
  - https://github.com/php/php-src/issues/12939 - Capture keypresses on Windows
- **Feat**: Improve stream_get_line to get rid of length limit
  - https://bugs.php.net/bug.php?id=48421 - stream_get_line() - allow $length to be optional _(5 votes)_
- **Feat**: Support setting of connection timeout
  - https://bugs.php.net/bug.php?id=36072 - stream_set_connection_timeout() _(2 votes)_
- **Feat**: Improve error reporting for php_network_addresses()
  - https://bugs.php.net/bug.php?id=71641 - Proper error-reporting in php_network_addresses() calls 
- **Feat**: Set IP(6)_RECVERR on connected datagram
  - https://github.com/php/php-src/pull/8635 -  set IP(6)_RECVERR on connected datagram sockets
- **Feat**: Support for SO_LINGER socket option
  - https://github.com/php/php-src/pull/14129 - GH-14111 main/streams: adding SO_LINGER to stream options.
- **Feat**: Support multiple persistent connections on UDS
  - https://bugs.php.net/bug.php?id=63293 - Add support to establish > 1 persistent connection to the same UNIX socket _(7 votes)_
- **Bug**: Look to the issue with occasionally missing STREAM_NOTIFY_PROGRESS on Win
  - https://github.com/php/php-src/issues/10031 - STREAM_NOTIFY_PROGRESS over HTTP emitted irregularly for last chunk of data
  - https://github.com/php/php-src/pull/10492 - Fix GH-10031: [Stream] STREAM_NOTIFY_PROGRESS over HTTP emitted irregularly for last chunk of data
- **Feat**: Make stream notifications properly work on TCP
  - https://bugs.php.net/bug.php?id=52811 - the notification callback method never gets call when using socket streams _(9 votes)_
  - https://bugs.php.net/bug.php?id=63556 - stream_notification_callback _(1 vote)_
  - https://github.com/php/php-src/issues/8641 - STREAM_NOTIFY_COMPLETED over HTTP never emitted
- **Feat**: Look to supporting upload progress notification for things like HTTP POST
  - https://bugs.php.net/bug.php?id=80124 - HTTP stream contexts missing upload progress notification _(1 vote)_
- **Feat**: Support some additional methods for stream wrappers
  - https://bugs.php.net/bug.php?id=38025 - Missing stream wrapper methods _(12 votes)_
- **Feat**: Consider adding method for checking if user is super user
  - https://bugs.php.net/bug.php?id=72600 - Consider root special perms with stream_wrapper _(2 votes)_
- **Feat**: Consider supporting realpath for custom stream wrappers
  - https://github.com/php/php-src/issues/12118 - Add "realpath" support for custom stream wrapper
- **Feat**: Look to the LOCK_EX support for stream wrappers
  - https://bugs.php.net/bug.php?id=61201 - LOCK_EX in file_put_contents with custom streamwrapper fails _(4 votes)_
- **Feat**: Look to the ways of restoring of origin wrapper
  - https://bugs.php.net/bug.php?id=42929 - Cannot access the old stream wrapper from a wrapper class _(2 votes)_
- **Feat**: Streams wrappers autoloading
  - https://github.com/php/php-src/issues/11087 - autoloader for custom stream wrappers
- **Feat**: Glob stream wrapper support
  - https://github.com/php/php-src/issues/9224 - StreamWrapper support for glob()
- **Feat**: Look to the way how to get stream resource in called stream wrapper method
  - https://bugs.php.net/bug.php?id=72561 - 5.2.2 regressed with incorrect seeking in stream wrappers (comment with use case for seek)
- **Feat**: Implement set of interfaces for user stream wrapper
  - https://github.com/php/php-src/issues/10506 - Add StreamWrapperInterface
- **Feat**: Allow colon only scheme (not requiring //)
  - https://bugs.php.net/bug.php?id=36678 - Use of URL like about:config in streams _(2 votes)_
- **Feat**: Warn or deprecate invalid context option
  - https://github.com/php/php-src/issues/16105 - stream_context_create silently ignores invalid options
- **Feat**: Consider ability to set default context options from ini
  - https://bugs.php.net/bug.php?id=70038 - peer verification needs to be a global option _(1 vote)_
- **Feat**: Investigate disabling temp_file for input stream
  - https://github.com/php/php-src/issues/8239 - For php://input fread() writes temp files
- **Feat**: Investigate multipart support for stream input
  - https://bugs.php.net/bug.php?id=76444 - can't read stream from multipart requests _(1 vote)_
- **Feat**: Make HTTP stream selectable even if filters are used
  - https://github.com/php/php-src/pull/6926 - Allow to cast filtered streams to PHP_STREAM_AS_FD_FOR_SELECT
- **Feat**: Clean up php_stdiop_cast fd type handling
  - https://github.com/php/php-src/issues/17524 - Cleaning up types in php_stdiop_cast
- **Feat**: Handle setting of EOF for keep alive connections that are not closed by server
  - https://bugs.php.net/bug.php?id=80931 - file_get_contents() hangs with HTTP/1.1 if server doesn't close connection
  - https://github.com/php/php-src/pull/6874 - Fix #80931: HTTP stream hangs if server doesn't close connection
- **Feat**: Add stream context request header value validation (e.g. checking for LF)
  - https://github.com/php/php-src/issues/18238 - Double Content-Type headers added to request if context->http->header is a multiline string
- **Feat**: Look to the trailer support
- **Feat**: Investigate alternative / setting of http_response_header in relation to custom http stream wrapper
  - https://bugs.php.net/bug.php?id=63897 - Custom http stream wrappers should be able to set $http_response_header _(3 votes)_
- **Feat**: Handling HTTP 304 in copy and others
  - https://bugs.php.net/bug.php?id=67351 - copy() should handle HTTP 304 response
  - https://github.com/php/php-src/pull/6177 - Fix #67351: copy() should handle HTTP 304 response
- **Feat**: Support relative redirects in http stream wrapper
  - https://bugs.php.net/bug.php?id=64582 - file_get_contents() handles redirects wrong
- **Feat**: Support setting protocol version (consider future support for HTTP 2)
  - https://github.com/php/php-src/issues/8832 - Support "protocol_version" stream context option for proxy connections
- **Feat**: HTTP 2 support
  - https://bugs.php.net/bug.php?id=76625 - Support http2 in file_get_contents() and friends _(5 votes)_
- **Feat**: WinSSL support
  - https://bugs.php.net/bug.php?id=77505 - streams/HTTPS cannot be used with WinSSL/schannel _(2 votes)_
- **Feat**: Look to the fopen wrapper better support for FTP SIZE command
  - https://bugs.php.net/bug.php?id=48674 - fopen() ftp wrapper and SIZE command _(11 votes)_
- **Feat**: Support FTP EPSV command
  - https://bugs.php.net/bug.php?id=69580 - I need an FTP stream that doesn't use EPSV _(1 vote)_
- **Feat**: Reuse FTP connection
  - https://bugs.php.net/bug.php?id=72343 - FTP wrapper should re-use connections

## Docs

- **Doc**: Document changes in return value for fwrite and fread in PHP 7.4 migration guide
  - https://bugs.php.net/bug.php?id=79965 - Why does the manual say fread/fwrite changed in PHP 7.4?
- **Doc**: Consider documentation of stream types
  - https://bugs.php.net/bug.php?id=72804 - docs on rewind explicitly says it must be opened by fopen()
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



## Changes

### 2025-05

- **Bug**: Look to a proper fix for socket name
  - https://bugs.php.net/bug.php?id=74556 - stream_socket_get_name returns \0 string instead of false

### 2025-04

- **Bug**: Look into HTTP header parsing consistency
  - https://github.com/php/php-src/issues/17829 - PHP behavior for parsing http header value is not consistent across http APIs

### 2024-11

- **Bug**: Fix EINPROGRESS error issues happening in Redis ext
  - https://github.com/php/php-src/pull/13252 - Fix EINPROGRESS very rarely occurring on synchronous php_network_connect_socket()

### 2024-01

- **Bug**: stream_select on freebsd possibly incorrect (David checked it and no longer re-creatable on the latest FreeBSD version)
  - https://bugs.php.net/bug.php?id=60186 - stream_select ignores the timeout on freebsd

### 2023-12

- **Bug**: Investigate custom stream wrappers issue with dynamic properties and FFI
  - https://github.com/php/php-src/issues/9698 - stream_wrapper_register crashes with FFI\CData provided as class

### 2023-11

- **Bug**: fopencookie issue visible in imagecreatefrompng
  - https://bugs.php.net/bug.php?id=79945 - using php wrappers in imagecreatefrompng causes segmentation fault

### 2023-10

- **Bug**: Issue with reading image info in getimagesize with StreamWrappers
  - https://bugs.php.net/bug.php?id=75708 - getimagesize with "&$imageinfo" fails on StreamWrappers
### 2023-08

- **Bug**: File existence check should be false for unsupported protocol
  - https://bugs.php.net/bug.php?id=76857 - Can read “non-existant” files
- **Bug**: Seeking past the end on memory stream does not work
  - https://bugs.php.net/bug.php?id=52335  - fseek() on memory stream behavior different then file
  - https://github.com/php/php-src/issues/9441 - fseek does not work with php://input even though the stream is advertised as seekable

### 2023-07

- **Bug**: Look to potentially incorrect seeking of stream wrappers
  - https://bugs.php.net/bug.php?id=72561 - 5.2.2 regressed with incorrect seeking in stream wrappers

### 2023-02

- **Bug**: feof() behavior change for UNIX based socket resources
  - https://github.com/php/php-src/issues/10406 - feof() behavior change for UNIX based socket resources in PHP 8.2
  - https://github.com/php/php-src/pull/10877 - Fix GH-10406: feof() behavior change for UNIX based socket resources

### 2023-02

- **Bug**: Investigate stream_select after fork issue
  - https://bugs.php.net/bug.php?id=75749 - pcntl_fork does not duplicate stream_sockets

### 2022-10

- **Bug**: fread blocking unpredictible
  - https://bugs.php.net/bug.php?id=51056 - fread() on blocking stream will block even if data is available
  - https://bugs.php.net/bug.php?id=52602 - fread is blocking even with the use of stream_select

### 2022-08

- **Bug**: Socket metadata are inherited
  - https://github.com/php/php-src/issues/8472 - The resource returned by stream_socket_accept may have incorrect metadata

### 2022-07

- **Bug**: Fix open_basedir check in GlobIterator and glob:// stream
  - https://github.com/php/php-src/commit/1a9e6895f1d203f38655b52d5b6b823be7d14cbd
- **Feat**: Allow not close stream on rscr dtor in php cli sapi
  - https://github.com/php/php-src/pull/8833