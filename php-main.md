# PHP main TODO

## Source issues

### Output

- **Bug**: Errors - Properly escape html for all error types
  - https://bugs.php.net/bug.php?id=77074 - XSS through error messages _(3 votes)_
- **Bug**: OB - Prefent flusing on exit -  caused by exit unwinding
  - https://bugs.php.net/bug.php?id=81431 - header_register_calback no longer allows die() to stop executing outputting (patch without test attached) _(1 vote)_
- **Bug**: OB - Prevent flusing on fatal error
  - https://bugs.php.net/bug.php?id=67467 - print_r with $return=true outputs its argument if it is too large (OB comment to fix) _(5 votes)_
- **Bug**: Output - Check if output_add_rewrite_var could be more JavaScript friendly
  - https://bugs.php.net/bug.php?id=67887 - 	the URL rewrite mechanism handles `<a href=\"javascript` in a surprising manner _(4 votes)_
  - https://bugs.php.net/bug.php?id=76664 - Regression in URL rewrite when JavaScript href? _(3 votes)_
- **Bug**: Output - Look to the issue with rewriting JSON encoded href tag
  - https://bugs.php.net/bug.php?id=80192 - session.use_trans_sid brokes JSON encoded HTML string
- **Feat**: Look to converting NL in exception stack to `<br>` tag when html_errors enabled
  - https://bugs.php.net/bug.php?id=77075 - Add `<br>` to the exception reporting in HTML


### SAPI

- **Bug**: SAPI - Investigate if there is anything that can be done about incorrect content lenght in header()
  - https://bugs.php.net/bug.php?id=69414 - Script hangs forever _(2 votes)_
- **Bug**: SAPI - Look to explicitly enabling chroot only for some SAPI's
  - https://github.com/php/php-src/issues/11984 - The chroot() doesn't get properly enabled/disabled when building SAPIs
- **Bug**: SAPI - Fix incorrect counting of max_input_vars
  - https://bugs.php.net/bug.php?id=60707 - max_input_vars allows one extra var _(4 votes)_
- **Feat**: SAPI - Do not set charset for some mime type that do not support it
  - https://github.com/php/php-src/issues/11146 - SAPI should not add charset to each text subtype
- **Feat**: SAPI - Look to API for populating post data for other methods (will require RFC)
  - https://github.com/php/php-src/pull/11472 - Add populate_post_data() function


## Docs

- **Doc**: OB - Properly document ob_get_status()
  - https://bugs.php.net/bug.php?id=62019 - ob_get_status returns 'flags' bitmask instead of 'status' array key _(17 votes)_
- **Doc**: OB - Document return value of ob_list_handlers
  - https://bugs.php.net/bug.php?id=65826 - ob_list_handlers: outdated return values & examples _(1 vote)_
- **Doc**: OB - Document ob_start() flags
  - https://bugs.php.net/bug.php?id=64977 - ob_start() fails when passed default parameters _(2 votes)_
- **Doc**: OB - Document flushing flow with output buffering and how clean works in relation to that
  - https://bugs.php.net/bug.php?id=65115 - flush() disables compression from ob_gzhandler _(0 votes)_
  - https://bugs.php.net/bug.php?id=69404 - PHP_OUTPUT_HANDLER_FLUSHABLE only affects ob_flush() _(0 votes)_
  - https://bugs.php.net/bug.php?id=71486 - Output handler flags for ob_end_clean and ob_end_flush _(1 vote)_
  - https://bugs.php.net/bug.php?id=74399 - ob_*clean* methods do not respect missing cleanable flag; same for flushing _(3 votes)_
  - https://bugs.php.net/bug.php?id=76563 - ob_get_clean ignores return value of ob_start callback
- **Doc**: OB - Proper documentation of output buffering (probably better placed in PHP internals book) _(0 votes)_
- **Doc**: better $_SERVER docs
  - https://bugs.php.net/bug.php?id=74424 - $_SERVER documentation page needs improvement _(0 votes)_