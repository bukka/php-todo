# PHP Standard extension related tasks

## Source issues

### Arrays

- **Bug**: Check current return value
  - https://bugs.php.net/bug.php?id=74724 - current returns false but each returns value
- **Feat**: Improve handling of negative limit for explode()
  - https://github.com/php/php-src/issues/13074 - Explode from end with negative limit

### File System

- **Bug**: Get merged the chown fix for ZTS
  - https://bugs.php.net/bug.php?id=68861 - chown does not work when php is compiling with ZTS _(10 votes)_
  - https://github.com/php/php-src/pull/13876 - fix group/passwd api misuse if ZTS
- **Bug**: Look to changing lchown land chgrp issue on ZTS
  - https://bugs.php.net/bug.php?id=74357 - lchown fails to change ownership of symlink with ZTS _(0 votes)_
- **Bug**: Fix removing ACL and extended attrs during move_uploaded_file and rename
  - https://bugs.php.net/bug.php?id=65057 - move_uploaded_file() umask acl _(11 votes)_
  - https://bugs.php.net/bug.php?id=81404 - rename() does not keep extended file attributes
- **Bug**: Look to renaming directories across different file systems (copy recursively all files in them)
  - https://bugs.php.net/bug.php?id=54097 - rename() of dirs accross devices produces confusing copy error _(64 votes)_
- **Bug**: Look to the LFS support for 32bit
  - https://bugs.php.net/bug.php?id=45040 - 64 bit inode stat fails without LFS flags (ex: recursive mkdir) _(9 votes)_
  - https://bugs.php.net/bug.php?id=27792 - [PATCH] Functions fail on large files (filesize,is_file,is_dir,readdir) _(297 votes)
  - https://bugs.php.net/bug.php?id=65445 - filesize() fails for files with high inode number _(0 votes)_
- **Bug**: Look to the fseek inconsistency on 32bit past 2GB
  - https://bugs.php.net/bug.php?id=54902 - fseek inconsistencies with large (>2GB) files _(3 votes)_
- **Bug**: Look to the issue with opening anonymous pipes
  - https://bugs.php.net/bug.php?id=67085 -	filesystem functions don't handle anonymous pipes correctly _(2 votes)_
- **Bug**: Look to colon issue in files and possible support for relative colon paths on Windows
  - https://bugs.php.net/bug.php?id=81339 - NTFS streams on Windows are partially supported _(2 votes)_
  - https://bugs.php.net/bug.php?id=81725 - Colons in the filename when create file can cause problems _(0 votes)_
  - https://bugs.php.net/bug.php?id=72367 - Relative Drive:path incorrectly assumed to be Drive:\path _(2 votes)_
  - https://github.com/php/php-src/pull/5001 - Fix #78939 - Windows relative path with drive letter
  - https://bugs.php.net/bug.php?id=78939 - file_exists produces different results with TS and NTS builds _(1 vote)_
- **Bug**: Look to sambashare related issues
  - https://bugs.php.net/bug.php?id=62199 - is_readable() does not seem to tolerate crossing partitions inside a sambashare _(15 votes)_
- **Bug**: Look to the issues with UNC paths and auth on Windows
  - https://bugs.php.net/bug.php?id=52376 - opendir() cannot open UNC paths in IIS7 using passthrough auth. _(15 votes)_
- **Bug**: Investigage why is_writeable does not always correctly on Windows
  - https://bugs.php.net/bug.php?id=68926 - is_writable returns false but file_put_contents works _(21 votes)_
  - https://github.com/php/php-src/issues/12744 - is_readable() and is_writable() return false negative on Win32's network-mapped drives
  - https://bugs.php.net/bug.php?id=73543 - Network drive file: is_readable() == false but file can be read _(5 votes)_
- **Bug**: Look to the proper support of symplinks on Windows
 - https://bugs.php.net/bug.php?id=69473 - bug in symlink() prevents relative symlinks on Windows _(11 votes)_
- **Bug**: Look to the inconsisteny in simlinking of simlinks
  - https://bugs.php.net/bug.php?id=66497 - symlink improperly creates recursive link on existing symlink without a target - _(3 votes)_
- **Bug**: Check if open_basedir bypass with symlink is still an issue
  - https://bugs.php.net/bug.php?id=77850 - Open_basedir bypass _(4 votes)_
- **Bug**: Look to open_basedir bypass or root directory
  - https://bugs.php.net/bug.php?id=78141 - open_basedir bug when write files on root directory  _(0 votes)_
- **Bug**: Look to open_basedir bypass in glob wrapper
  - https://bugs.php.net/bug.php?id=76362 - Bypass open_basedir restriction via scandir and glob:// _(0 votes)_
- **Bug**: Check handling of non existing of open_basedir value
  - https://bugs.php.net/bug.php?id=81042 - open_basedir directories must exist _(1 vote)_
- **Bug**: Look to confusing open basedir message due to potentially invalid access check
  - https://bugs.php.net/bug.php?id=64573 - Confusing open_basedir errors when parent folders are inaccessible _(2 votes)_
- **Bug**: Look to real path normalization on OSX
  - https://bugs.php.net/bug.php?id=67220 - realpath() on MacOSX doesn't normalize the case of characters _(3 votes)_
- **Bug**: Investigate why calling clearstatcache() seems to not work in some cases
  - https://bugs.php.net/bug.php?id=52587 - Clearstatcache() has no effect _(5 votes)_
- **Bug**: Clear stat cache after touch(), fopen(), fread() and fwrite()
  - https://bugs.php.net/bug.php?id=72666 - touch(): stat cache clearing inconsistent between file:// paths and plain paths _(0 votes)_
- **Feat**: Option to disable stat cache
  - https://bugs.php.net/bug.php?id=28790 - Add php.ini option to disable stat cache
  - https://github.com/php/php-src/pull/5894 - Feature Request #28790 Add php.ini option to disable stat cache
- **Feat**: Extend glob() with parameter limiting number of returned paths
  - https://bugs.php.net/bug.php?id=81989 - Glob() miss a scope limit parameter, to limit the max returned paths _(5 votes)_
- **Feat**: Introduce new parameter for file lock in various functions
  - https://github.com/php/php-src/pull/11254 - make FILE_ constants not collide with LOCK_
- **Feat**: Support LOCK_NB for file_put_contents and friends
  - https://bugs.php.net/bug.php?id=81322 - file_put_contents should support LOCK_NB _(1 vote)_
  - https://bugs.php.net/bug.php?id=54453 - LOCK_NB works with LOCK_SH when file locked with LOCK_EX ONLY _(5 votes)_
  - https://bugs.php.net/bug.php?id=63709 - flock() doesn't trigger mandatory locks on linux _(6 votes)_
- **Feat**: Add extra param to chown and lchown to change group
  - https://bugs.php.net/bug.php?id=77319 - Add an optional group paramter for chown() and lchown() _(1 vote)_
- **Feak**: Look to the potential mulibyte support for fgetcsv
  - https://bugs.php.net/bug.php?id=72861 - fgetcsv get line error _(3 votes)_
- **Feat**: Refactore php_fgetcsv - horrible and flaky code (it can be optimized)
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

- **Bug**: Investigate why mail.mixed_lf_and_crlf is not always woring
  - https://github.com/php/php-src/issues/8086#issuecomment-1983073957 - Mail() function not working correctly in PHP 8.x
- **Bug**: mail() should not return true if fails (Windows related)
  - https://bugs.php.net/bug.php?id=43327 - wrong return value from mail(), if sendmail_path is wrong _(8 votes)_
- **Bug**: possible issue with preventing mail.force_extra_parameters to be set in PHP_INI_PERDIR
  - https://bugs.php.net/bug.php?id=71901 - mail.force_extra_parameters is not PHP_INI_PERDIR _(5 votes)_
- **Feat**: Look to restricing sendmail options
  - https://github.com/php/php-src/issues/12781 - Restrict additional command line flags by default in mail()
  - https://github.com/php/php-src/pull/12783 - Add blacklisted command line flags for sendline via mail()
- **Feat**: Look to `$message` filtering options - possibly some new INI
  - https://github.com/php/php-src/issues/12632 - mail() truncates message on full stop between two newlines
- **Feat**: Allow $to being NULL to skip `To:` header
  - https://bugs.php.net/bug.php?id=44170 - mail() function arguments ambiguity _(1 vote)_
- **Feat**: Allow internatiaonlized names on Windows mail()
  - https://bugs.php.net/bug.php?id=81615 - Windows mail should support internationalized email _(3 votes)_

### Math

- **Feat**: Check casting of object for is_numeric
  - https://bugs.php.net/bug.php?id=46524 - is_numeric doesn't take objects as parameter

### Network

- **Bug**: Network - Check if php_tvtoto can still overflow
  - https://bugs.php.net/bug.php?id=71507 - Overflow in php_tvtoto _(no vote)_
- **Bug**: DNS - Look to incorrect handling of server errors 
  - https://bugs.php.net/bug.php?id=73149 - dns_get_record(): A temporary server error occurred _(139 votes)_
- **Bug**: DNS - correctly handle SERVFAIL
  - https://bugs.php.net/bug.php?id=70473 - dns_get_record - Server error for any of DNS_A|DNS_AAAA bubbles up, no result _(5 votes)_
- **Bug**: DNS - checkdnsrr should correctly check MX CNAME
  - https://bugs.php.net/bug.php?id=68081 - checkdnsrr( 'example.com' ) returns `true` when no MX, only CNAME _(1 vote)_
- **Bug**: DNS - Multistring DNS should not be terminated by '\0'
  - https://bugs.php.net/bug.php?id=65478 - Multi-string DNS records obtained with dns_get_record contain nulls _(2 votes)_
- **Feat**: Network - IPv6 support for gethostbyname()
  - https://bugs.php.net/bug.php?id=49493 - Add IPv6 support in gethostbyname() _(123 votes)_
- **Feat**: Network - Look to inconsistent IPv6 handling
  - https://bugs.php.net/bug.php?id=76479 - Inconsistent IPv6 handling _(3 votes)_
- **Feat**: DNS - Check if there is any point to add SPF record (deprecated)
  - https://bugs.php.net/bug.php?id=54821 - Add support for SPF records to dns_get_record _(10 votes)_
- **Feat**: DNS - Add DNAME support and consider removing A6
  - https://bugs.php.net/bug.php?id=52632 - dns_get_record: Add DNAME, remove A6 _(3 votes)_
- **Feat**: DNS - Add other missing records in dns_get_record()
  - https://bugs.php.net/bug.php?id=65343 - Not all DNS types supported in dns_get_record _(6 votes)_
- **Feat**: DNS - Reduce warnings in dns_get_record
  - https://bugs.php.net/bug.php?id=50903 - dns_get_record sends warnings _(4 votes)_
- **Feat**: Network - INI to globally set bindto default
  -  https://bugs.php.net/bug.php?id=63076 - Force source IP on network operations _(3 votes)_
- **Feat**: Network - Consider alternative to ip2long allowing numbers starting with zero
  - https://bugs.php.net/bug.php?id=70845 - ip2long should not fail with number starting with zero _(no vote)_
- **Feat**: Add new function to display response text (something like http_response_code but for text)
  - https://bugs.php.net/bug.php?id=68219 - Make http_response_code() also returns the text of response _(1 vote)_

### Process and shell

- **Bug**: Investigate issues with locale handling in escapeshellarg
  - https://bugs.php.net/bug.php?id=54391 - escapeshellarg strip non-ascii characters _(10 votes)_
- **Bug**: Look to the shell (dash) escaping issue in escapeshellarg
  - https://bugs.php.net/bug.php?id=61706 - escapeshellarg behaves inconsistently depending on shell _(3 votes)_
- **Bug**: Investigate sec issue that is not really a security issue
  - https://bugs.php.net/bug.php?id=76035
- **Bug**: Investigate possibly incorrect PATH setting in exec when used with FPM
  - https://bugs.php.net/bug.php?id=69118 - exec command not executed _(3 votes)_
- **Bug**: Look to the potentially missing awaited process (zombie)
  - https://bugs.php.net/bug.php?id=69014 - proc_close and proc_get_status returns NULL. Zombies remain in process-list _(10 votes)_
- **Bug**: Check getting real exit code from proc_close
  - https://bugs.php.net/bug.php?id=53518 - pclose and proc_close do not return values for use with pcntl_wifexited _(4 votes)_
  - https://bugs.php.net/bug.php?id=70419 - proc_close return code is unreliable
- **Bug**: Check handling of background processes and waiting for their exit
  - https://bugs.php.net/bug.php?id=53085 - Php blocked waiting process exit _(1 vote)_
- **Bug**: Prevent filtering of env variables without value in proc_open
  - https://bugs.php.net/bug.php?id=71868 - Environment variables with no value are filtered out by proc_open() _(4 votes)_
- **Bug**: Investigate dropping env vars with hyphen in name for proc_open
  - https://bugs.php.net/bug.php?id=72904 - proc_open drops hyphenated environment variables _(1 vote)_
- **Bug**: Check possibly incorrect constants and env handling on Windows
  - https://bugs.php.net/bug.php?id=50503 - proc_open loses constants with $env _(3 votes)_
- **Bug**: Check if proc_open() chdir error is handled by posix_spawn correctly and check if we should somehow try to fix in legacy fork impl
  - https://bugs.php.net/bug.php?id=77656 - proc_open() ignores invalid cwd argument
- **Bug**: Leaked file discriptor in the legacy proc_open implementation (fork)
  - https://bugs.php.net/bug.php?id=67905 - proc_open leaks file descriptors on error _(1 vote)_
- **Feat**: Look into solution to clean up open file descriptors on request end
  - https://bugs.php.net/bug.php?id=38915 - Apache: system() (and similar) don't cleanup opened handles of Apache _(209 votes)_
- **Feat**: Look to the option to disable open handles inheritance in popen / proc_open
  - https://bugs.php.net/bug.php?id=70932 - Add ability to prevent handles inheritance in popen / proc_open _(10 votes)_
- **Feat**: Check whether posix spawn addresses any escaping issues and whether it makes sense to use execv or execve for legacy impl
  - https://bugs.php.net/bug.php?id=68599 - exec()/passthru() function should use execv, execve _(2 votes)_
- **Feat**: Add function num_cpus that returns number of cpu (interface discussion)
  - https://github.com/php/php-src/pull/11137 - feat: add function num_cpus (formerly nproc)
- **Feat**: Introduce function for setting ionice
  - https://bugs.php.net/bug.php?id=52166 - REF: support ionice _(5 votes)_
- **Feat**: Measure sleep time that was slept and if interrupted, optionally sleep again the rest of the time
  - https://bugs.php.net/bug.php?id=77603 - Continued sleep after signal interruption _(3 votes)_

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
- **Doc**: Output - Document output buffering
  - https://bugs.php.net/bug.php?id=60984 - Document output buffering mechanism
- **Doc**: Mail - Document introduction of mail.mixed_lf_and_crlf INI and previous CRLF changes
 - https://bugs.php.net/bug.php?id=81158 - Mails sent by mail function broken since PHP 8.0
- **Doc**: Mail - Fix mail function example
  - https://bugs.php.net/bug.php?id=70082 - mail() function description should provide right example of multi-part mail
- **Doc**: FS - Add note to file_exists docs that it is not cache and slower
  - https://bugs.php.net/bug.php?id=78285 - file_exists is 30 times slover than is_dir
- **Doc**: FS - Document locale dependency in pathinfo
  - https://bugs.php.net/bug.php?id=77239 -  pathinfo strips umlauts only at the beginning
- **Doc**: FS - Add note about trailing slash handling in pathinfo
  - https://bugs.php.net/bug.php?id=81079 - pathinfo() unexpected path/filename separation with trailing slash
- **Doc**: FS - Add note about realpath cache and difference between ZTS and non ZTS logic in it
  - https://bugs.php.net/bug.php?id=78634 - realpath function caches results
- **Doc**: Network - Clarify what happens if no argument for setcookie
  - https://bugs.php.net/bug.php?id=66725 - Clarification required as to what happens if domain argument isn't passed

## Changes

### 2023-01

- **Bug**: Mail() function not working correctly in PHP 8.x
  - https://github.com/php/php-src/issues/8086