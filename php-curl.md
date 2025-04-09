# PHP CURL tasks

## Source issues

- **Bug**: MacOS - Look more into that MacOS issue and curl initialization
  - https://bugs.php.net/bug.php?id=81394 - Apache faults when using cURL with IMAP enabled
  - https://github.com/php/php-src/issues/11818 - macOS now crashes fork() process instead of just warning output
- **Bug**: TLS - Check curl with alternative TLS backend 
  - https://bugs.php.net/bug.php?id=81276 - Using curl/libcurl with NSS backend fails to load curl extension
- **Bug**: TLS - Check possible memory leak with verify peer enabled
  - https://bugs.php.net/bug.php?id=76484 - emory leakage with CURLOPT_SSL_VERIFYPEER set to TRUE _(2 votes)_
- **Bug**: TLS - Look into removing the OpenSSL crypto locks clean up
  - https://bugs.php.net/bug.php?id=50966 - Some resource leak (odbc_connect and odbc_close) using dbase or Microsoft Acces _(1 vote)_
- **Bug**: TLS - Look into Win IIS extend protection issue
  - https://github.com/php/php-src/issues/14039 - php_curl does not work with IIS extended protection 
- **Test**: TLS - Check failing curl_setopt_ssl.phpt on macOS
  - https://github.com/php/php-src/issues/12901 - curl_setopt_ssl.phpt is intermittently failing on macOS
- **Test**: h2 - Check leaking caddy tests
  - https://github.com/php/php-src/issues/16074 - Leaking Curl tests on Ubuntu 24.04
- **Test**: h2 - Look into caddy win setup
  - https://github.com/php/php-src/issues/16093 - Setup Caddy Webserver for testing/CI
- **Bug**: h2 - check possible crash in push
  - https://bugs.php.net/bug.php?id=77497 - Empty reponse with H2 server push and timeout
- **Bug**: Look into multicleanup crash (when h2 push is used)
  - https://bugs.php.net/bug.php?id=81428 - Crash with cycle containing a curl_multi_handle
- **Bug**: ipv6 - check ipv6 related crash
  - https://bugs.php.net/bug.php?id=75862 - PHP --disable-ipv6, curl --enable-ipv6 _(2 votes)_
- **Bug**: writer - look into exception handling
  - https://github.com/php/php-src/issues/16513 - curl: exceptions in callbacks do not abort the request
- **Bug**: writer - look into CURLOPT_WRITEFUNCTION issue
  - https://github.com/php/php-src/issues/13711 - Infinite waiting for CURLOPT_WRITEFUNCTION in case of no response
- **Bug**: stderr - look into stream seeking issues
  - https://bugs.php.net/bug.php?id=76268 - stream_get_contents fail to seek on streams modified by curl_exec
  - https://github.com/php/php-src/pull/7669 - 7.4 — curl/interface.c: avoid crashing, when PHP is compiled without IPv6 support, and CURL has IPv6 support
- **Bug**: file - check write issues for some stream types
  - https://bugs.php.net/bug.php?id=72092 - CURLOPT_FILE is rewinded depending on stream type _(5 votes)_
  - https://bugs.php.net/bug.php?id=70693 - CURLOPT_FILE won't work with ftp handlers _(0 vote)_
- **Bug**: file - verify issue with setting CURLFile in CURLOPT_POSTFIELD related to missing $name
  - https://bugs.php.net/bug.php?id=77617 - curl_setopt_array Triggers warning when used with CURLFile in CURLOPT_POSTFIELD _(1 vote)_
- **Bug**: file - check 3rd argument strange behaviour when empty and if it would be worth to change it
  - https://bugs.php.net/bug.php?id=79004 - CURLFile's 3rd argument doesn't honor emptystring
- **Bug**: Check multiselect changes and inconsistencies in return values
  - https://bugs.php.net/bug.php?id=77030 - curl_multi_select() return value is inconsistent
- **Bug**: Check curl_errno return value after curl_multi_init
  - https://bugs.php.net/bug.php?id=79318 - curl_errno() is always 0 if there was an error while used with curl_multi()
- **Bug**: Check content type return value changes (BC)
  - https://github.com/php/php-src/issues/16929 - curl_getinfo($ch, CURLINFO_CONTENT_TYPE) returns false when Content-Type header is not set


## Docs

- **Doc**: Document that PEM format might depend on backend
  - https://bugs.php.net/bug.php?id=76388 - CURLOPT_SSLKEYPASSWD is not supported when curl is compiled with NSS
- **Doc**: Document CURLINFO_HEADER_OUT and VERBOSE
  - https://bugs.php.net/bug.php?id=69622 - VERBOSE and HEADER_OUT cURL options
- **Doc**: Check POST docs
  - https://bugs.php.net/bug.php?id=69644 - additional note for CURLOPT_POSTFIELDS
- **Doc**: Document CURLOPT_NOPROXY
  - https://bugs.php.net/bug.php?id=71836 - Missing CURLOPT_NOPROXY in documentation
- **Doc**: Check if cookie order should be documented
  - https://bugs.php.net/bug.php?id=62942 - Setting CURLOPT_COOKIE with curl_setopt_array problem _(3 votes)_
- **Doc**: Document pkg-config changes
  - https://bugs.php.net/bug.php?id=81661 - curl uses pkg-config as of PHP 7.4.0