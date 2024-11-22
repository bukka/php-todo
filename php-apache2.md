# Apache2 tasks

- https://bugs.php.net/search.php?cmd=display&package_name[]=Apache2+related&direction=DESC&limit=30&status=Open&reorder_by=bug_type (done)
- https://bugs.php.net/search.php?cmd=display&package_name[]=Apache+related (done)
- https://github.com/php/php-src/issues?q=is%3Aopen+is%3Aissue+label%3A%22SAPI%3A+apache2handler%22 (done)
- https://github.com/php/php-src/pulls?q=is%3Aopen+is%3Apr+label%3A%22SAPI%3A+apache2handler%22 (done)

## Source issues

- **Bug**: Check security bug
  - https://bugs.php.net/bug.php?id=68486
- **Bug**: Look into handling of incomplete posts
  - https://bugs.php.net/bug.php?id=61471 - Incomplete POST does not timeout but is passed to PHP _(15 votes)_
- **Bug**: Look into POST vars on 404
  - https://bugs.php.net/bug.php?id=64672 - POST variables not received by custom 404 _(1 vote)_
- **Bug**: Investigate ErrorDocument failure
  - https://bugs.php.net/bug.php?id=80558 - Apache ErrorDocument subrequest fails horribly
- **Bug**: Look into incorrect setting of no_local_copy when mod_cache is used
  - https://bugs.php.net/bug.php?id=49106 - PHP incorrectly sets no_local_copy=1 on response as Apache 2 module _(28 votes)_
- **Bug**: Check sending duplicite Set-Cookie headers
  - https://bugs.php.net/bug.php?id=75554 - session_regenerate_id() causes duplicate Set-Cookie header to be sent _(12 votes)_
  - https://github.com/php/php-src/pull/3231 - Fix #75554 - Recreate all Set-Cookie headers from current sapi_headers
- **Bug**: Check connection closing when header is used
  - https://bugs.php.net/bug.php?id=73936 - Certain special header() calls wrongly prevent connection from closing _(1 vote)_
- **Bug**: Look into headers case sensitivity issue when setting it to $_SERVER
  - https://bugs.php.net/bug.php?id=77953 - Headers are case-sensitive to $_SERVER _(7 votes)_
- **Bug**: Look into handling of multiple authorization headers
  - https://bugs.php.net/bug.php?id=68851 - PHP and Apache2 interpret duplicate Authentication headers differently _(0 votes)_
- **Bug**: Look into logging with external auth
  - https://bugs.php.net/bug.php?id=47061 - 	User not logged under Apache
- **Bug**: Look into error handling in Apache
  - https://bugs.php.net/bug.php?id=75897 - error_log() results in inappropriate/inconsistent Apache severity
- **Bug**: Look into env setting for walk to top - what issue can this create?
  - https://github.com/php/php-src/pull/14953 - sapi/apache2: apache env with walk_to_top going to the parent request
- **Bug**: SSI include virtual did not seems to work correctly
  - https://bugs.php.net/bug.php?id=48260 - Size of PHP file affects behaviour of virtual() or #include virtual _(0 votes)_
- **Bug**: Look into freeing threads logic
  - https://bugs.php.net/bug.php?id=32220 - thread_resources for thread not getting freed when apache kills thread _(7 votes)_
- **Bug**: Check possible shutdown crash
  - https://bugs.php.net/bug.php?id=78619 - PHP7.4RC2 ZTS zend_signal_handler_defer crashes on apache shutdown
- **Bug**: Investigate more FreeBSD shutdown crash
  - https://github.com/php/php-src/issues/12844 - mod_php 8.1.26 crashes on apache graceful restart
- **Bug**: Investigate static TSRM cache issue
  - https://github.com/php/php-src/issues/8445 - libphp.so dumps core in sapi_register_post_entry+0x31()
- **Bug**: MPM ITK hang due opcache - killing locker perm issue - similar to FPM one
  - https://github.com/php/php-src/issues/9910 - opcache + MPM ITK might cause apache2 to hang
- **Feat**: Review mpm_winnt relate issue fix
  - Don't involve PHP in Apache mpm_winnt control process
- **Feat**: Review apache_connection_stream addition
  - https://github.com/php/php-src/pull/14047 - RFC - Added the apache_connection_stream() function for CGI WebSockets
- **Feat**: Introduce apache_finish_request
  - https://github.com/php/php-src/issues/11250 - apache_finish_request() alternative to fastcgi_finish_request()
- **Feat**: Look into connection status detection improvements
  - https://bugs.php.net/bug.php?id=43219 - connection_status() can function properly without output
- **Feat**: Look into resetting CWD - cwd is reset when shutdown handler runs
  - https://bugs.php.net/bug.php?id=40661 - cwd is reset when shutdown handler runs _(4 votes)_
- **Feat**: Consider introducing function to get request line
  - https://bugs.php.net/bug.php?id=70809 - Prevent usage of $_SERVER (performance penalty)
- **Feat**: Improve getallheaders to get only single header
  - https://bugs.php.net/bug.php?id=76008 - Add parameters to getallheaders or apache_request_headers _(1 vote)_
- **Feat**: Introduce slowlog like feature
  - https://bugs.php.net/bug.php?id=73335 - mod_php: slowlog feature (similar to fpm)
- **Feat**: Check if there is anything to improve headers already sent reporting
  - https://bugs.php.net/bug.php?id=77758 - Warning: headers already sent should identify what triggered the send _(1 vote)_


## Build issues

- **Bug**: APR 1.7.5 build issue
  - https://github.com/php/php-src/issues/16682 - Building apache2handler with APR 1.7.5 fails if compiler doesn't support __has_attribute
- **Bug**: Build apxs error
  - https://bugs.php.net/bug.php?id=75250 - Installation fails with INSTALL_ROOT when httpd.conf file is not present


## Docs issues

- **Doc**: Document handling of LimitRequestBody
  - https://bugs.php.net/bug.php?id=69322 - LimitRequestBody excession not handled correctly
- **Doc**: Document handling of http_response_code
  - https://bugs.php.net/bug.php?id=75009 - http_response_code() error code support depends on SAPI
- **Doc**: Document env handling
  - https://bugs.php.net/bug.php?id=71607 - putenv/getenv parameters are passed to subrequests
- **Doc**: Document locale handling
  - https://bugs.php.net/bug.php?id=81596 - PHP in apache with mod_perl ignores locale, while CLI version doesn't.
