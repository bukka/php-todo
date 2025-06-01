# PHP-FPM tasks

## Source issues

### UNIX and request handling

- **Bug**: unix - ACL entries check missing
  - https://github.com/php/php-src/issues/18357 - php-fpm listen.acl_users and listen.acl_groups not checking for duplicate ACL entries causing Invalid argument (22)
  - https://github.com/php/php-src/pull/18362 - check for duplicate ACL entries when applying listen.acl_*
- **Test**: main - properly test the logic for processing env vars (especially the httpd logic) and verify it works with httpd balancer
- **Feat**: fcgi / main - refactore processing of fcgi env vars
- **Feat**: main - Identify Apache load balancer by SERVER_SOFTWARE
  - https://bugs.php.net/bug.php?id=71379 - Add support for Apache 2.4 mod_proxy_balancer to FPM
- **Feat**: main - Change PHP_SELF to SCRIPT_NAME without pathinfo fix and enabled path discard
  - https://github.com/php/php-src/issues/11025 - FPM: Always use script name in PHP_SELF if cgi.discard_path = 1 and cgi.fix_pathinfo = 0
- **Feat**: main - look to the option to disable setting envs to $_SERVER
  - https://github.com/php/php-src/issues/13110 - Add option to hide Environment Variables from $_SERVER
- **Feat**: main - look to the implementation of the worker mode
  - https://externals.io/message/122027 - RFC proposal: worker mode primitives for SAPIs 
- **Feat**: unix - look more to setting CPU affinity and test it
  - https://github.com/php/php-src/pull/10075 - fpm binding master and children processes to specific core(s)
- **Feat**: unix - extra check for selinux deny_ptrace
  - https://github.com/php/php-src/pull/7648 - fpm dumpable process setting extra check for SElinux based systems.
- **Feat**: unix - check if there is anything that can be done about better handling of SELinux denial of access
  - https://bugs.php.net/bug.php?id=71532 - Child terminates when SELinux denies access to library
- **Feat**: unix - middle ground between chrooted and non-chrooted env (ideas from suphp)
  - https://bugs.php.net/bug.php?id=68125 - FPM check if script is in specified path before execute (ie docroot)
- **Feat**: unix - add option to rewrite fcgi path envs if chroot enabled
  - https://bugs.php.net/bug.php?id=62279 - PHP-FPM chroot never-solved problems (extends #55322)
  - https://bugs.php.net/bug.php?id=55322 - Apache : TRANSLATED_PATH doesn't consider chroot
- **Feat**: systemd - Add CapabilityBoundingSet
  - https://github.com/php/php-src/pull/4960 - Add CapabilityBoundingSet to systemd unit file (my PR)
- **Feat**: systemd - Properly support PrivateTmp
  - https://bugs.php.net/bug.php?id=73466 - systemd option PrivateTmp= having no effect for a pool that is chrooted.

### FastCGI and other protocols

- **Bug**: fcgi - Investigate keepalive header mess up with nginx
  -  - https://github.com/php/php-src/issues/18275 - fastcgi_finish_request() doesn't eof requests with no body, allowing setting response headers for othe requests
- **Bug**: fcgi - Investigate deadlock for keepalive connection after fastcgi_finish_request()
  - https://github.com/php/php-src/issues/10335 - FPM: keepalived connection with fastcgi_finish_request causes dead lock
 - **Feat**: fcgi / main - look to support for close parameter in fastcgi_finish_request
  - https://github.com/php/php-src/pull/10273 - FPM: fastcgi_finish_request supports force close connection param
- **Feat**: fcgi - Allow flushing of headers if no content
  - https://github.com/php/php-src/issues/12385 - flush with fastcgi does not force headers to be sent
- **Feat**: fcgi / main - Add notice about aborting if flushing after using fastcgi_finish_request()
  - https://github.com/php/php-src/issues/9741 - flush() halts script after fastcgi_finish_request()
- **Feat**: fcgi - Support FCGI_ABORT_REQUEST
  - https://bugs.php.net/bug.php?id=76419 - connection_aborted() under FPM doesn't work properly
- **Feat**: fcgi - allow missing content length and abort if supplied content length does not match as well as flag to restore current behavior
  - https://github.com/php/php-src/pull/7509 - Fixed reading in streamed body using fastcgi
  - https://github.com/php/php-src/issues/12343 - PHP processing a truncated POST request
- **Feat**: fcgi / main - do not process requests that timeouts on client (e.g. nginx) - extra option to get client timeout - consider also fcgi request balancing process
  - https://github.com/php/php-src/issues/14548 - New config to adjust timeouts between NGINX and PHP-FPM (fix PHP zombie process)
- **Feat**: fcgi - spec update to no content length bytes
  - https://bugs.php.net/bug.php?id=79723 - sapi_cgi_read_post() ignores EOF
  - https://bugs.php.net/bug.php?id=51191 - Request body is 0-size when chunked requests are used 
  - https://github.com/php/php-src/pull/7509 - Fixed reading in streamed body using fastcgi
- **Feat**: fcgi - do not require any CGI parameters to allow overwriting on pool level
  - https://bugs.php.net/bug.php?id=74995 - Control/set fastcgi parameters from pool config file
- **Feat**: fcgi - spec update to allow using FCGI over TLS
- **Feat**: fcgi - spec update to allow larger headers than 64k
  - https://trac.nginx.org/nginx/ticket/239 - Support for large (> 64k) FastCGI requests
- **Feat**: fcgi - implement TLS support with client cert auth
- **Feat**: http - look to the implementation for http
- **Feat**: http - allow serving static assets
  - https://bugs.php.net/bug.php?id=73313 - over fpm does not respect in .user.ini engine off directive

### Socket and general things

- **Bug**: socket - non portable socket binding on FreeBSD
  - https://bugs.php.net/bug.php?id=77501 - listen = 9000 only listens on one interface
  - https://bugs.php.net/bug.php?id=77482 - Wont bind to IPv4 if IPv6 enabled
- **Feat**: socket - check routing options for other platforms similar to above listen.rtable
  - https://github.com/php/php-src/pull/8470 - FPM add routing view global option (for FreeBSD for now).
- **Feat**: socket - Add listen.rtable for OpenBSD
  - https://github.com/php/php-src/pull/11890 - sapi/fpm: adding listen.rtable option for OpenBSD
- **Feat**: socket - Enable tcp_info for OpenBSD
  - https://github.com/php/php-src/pull/11561 - fpm: enable tcp_info api for OpenBSD
- **Feat**: socket - listen backlog updates / improvements
  - https://github.com/php/php-src/pull/12977 - Update listen backlog on reload and stop enforcing default backlog
- **Feat**: socket - improve listen queue status info
  - https://github.com/php/php-src/issues/9943 - FPM improve listen queue status info
  - https://bugs.php.net/bug.php?id=76323 - FPM /status reports wrong number of listen queue len
  - https://bugs.php.net/bug.php?id=80739 - PHP-FPM status page shows listen queue 0 (main details here)
- **Feat**: socket - Consider re-enabling warning for non empty listening queue or remove commented out code in process ctl.
  - https://github.com/php/php-src/blob/2ac5948f5cbaf3351fe18ab1068422487c9c215f/sapi/fpm/fpm/fpm_process_ctl.c#L349-L359
- **Feat**: socket - Implement vsock support
  - https://github.com/php/php-src/issues/12818 - php-fpm vsock support
- **Feat**: general - review return values in FPM code
  - https://github.com/php/php-src/pull/9911 - Change return values to bool or void in FPM
- **Feat**: general - Convert worker pools and children list to continous array for fast look up in stdio 

### Config

- **Bug**: conf - look to uid and gid possible overflow
  - found as a bug in security audit
- **Feat**: conf - add support for getting environment variables in configuration
  - https://bugs.php.net/bug.php?id=75994 - Environment permanently breaks for worker process.
  - https://bugs.php.net/bug.php?id=76798 - Can't configure PHP-FPM via environment variables (check if it worked before 7.1.15 and 7.2.1)
- **Feat**: conf - allow syntax for not evaluating env keys
  - https://bugs.php.net/bug.php?id=81253 - unexpected result of setting env[LC_MESSAGES] in php-fpm pool config
- **Feat**: conf - env file support (discussion with Arne)
- **Bug**: conf - possibly incorrect order of ini setting
  - https://bugs.php.net/bug.php?id=75741 - enable_post_data_reading not working on PHP-FPM
  - https://github.com/php/php-src/issues/8157 - post_max_size evaluates .user.ini too late in php-fpm?
  - https://github.com/php/php-src/pull/8955 - activate sapi module before POST handling to allow to apply user.ini
- **Bug**: conf - possible overwritting issue with php_admin_value and php_value
  - https://bugs.php.net/bug.php?id=80012 - PHP_ADMIN_VALUE parameter is not correctly inherited
  - https://bugs.php.net/bug.php?id=72253 - phpinfo shows only first block of admin_value[disable_functions]
  - https://bugs.php.net/bug.php?id=72018 - php_admin_value override
  - https://bugs.php.net/bug.php?id=68171 - php_admin_value[extension] order not maintained
  - https://bugs.php.net/bug.php?id=68018 - php_value directive modifies "Changeable" context (patch)
  - https://bugs.php.net/bug.php?id=60387 - Problem with php_(admin)?_value/flag and load order
  - https://github.com/php/php-src/issues/8398 - php_value[xxx] in php-fpm pool - first declaration wins
- **Feat**: conf - Introduce ZEND_INI_ADMIN for PHP ini admin values and not overwrite some system ini that cannot be overriden
  - https://github.com/php/php-src/issues/8699 - Wrong value from ini_get() for shared files because of opcache optimization
  - https://github.com/php/php-src/issues/9722 - FPM is maliciously compliant when asked to set opcache.preload
  - https://github.com/php/php-src/issues/10117 - php_admin_[flag|value] falsely applies config changes
  - https://github.com/php/php-src/pull/8997 - Fix GH-8699: ini_get() opcache optimization in 8.1 (see discussion of the change)
- **Feat**: main - PHP_ADMIN_VALUE and PHP_VALUE should be cleared on request end
  - https://bugs.php.net/bug.php?id=63965 - php-fpm site-specific settings go global
  - https://bugs.php.net/bug.php?id=53611 - fastcgi_param PHP_VALUE pollutes other sites
  - https://bugs.php.net/bug.php?id=61867 - user_ini_filename ignored for cached user_config (might need a check if this will be addressed by the above)
- **Feat**: main - option disable PHP_ADMIN_VALUE and PHP_VALUE
  - https://bugs.php.net/bug.php?id=64103 - Bypass PHP Security Settings with PHP-FPM
  - https://bugs.php.net/bug.php?id=70134 - open_basedir bypass with IP-based PHP-FPM
  - https://bugs.php.net/bug.php?id=72129 - PHP_VALUE, PHP_ADMIN_VALUE... changed by environment variables set in .htaccess
  - https://bugs.php.net/bug.php?id=77190 - PHP_VALUE can be changed by PHP-FPM environment variables without checking
  - https://bugs.php.net/bug.php?id=78305 -	Injection of INI settings into FPM worker processes
  - https://bugs.php.net/bug.php?id=79417 - PHP-FPM: php_admin_value can be overwritten in .htaccess
  - https://bugs.php.net/bug.php?id=80385 - Response data preceded by post data
- **Feat**: conf - allow multiple includes per file
  - https://bugs.php.net/bug.php?id=68022 -	FPM should allow multiple includes per file (patch)
- **Feat**: conf - look to pool specific includes (discussion with Arne)
- **Feat**: conf - Introduce -ttt config test mode to not print to log
  - https://github.com/php/php-src/pull/13256#issuecomment-1925317214 - Let php-fpm -tt dump info regardless of log_level (comment)
- **Bug**: conf - if error in the config, correctly put file name and file line of the error to the error message
  - https://bugs.php.net/bug.php?id=65500 - debug_backtrace doesn't identify file name when config contains invalid comment
- **Feat**: conf - optional pool prefix support
  - https://github.com/php/php-src/pull/3563 - Introducing "pool:" prefix on [section] FPM ini configuration
- **Feat**: conf - add compile option to set default FPM config path
  - https://bugs.php.net/bug.php?id=61073 - php-fpm config file path option lacking
- **Feat**: conf - Review FPM_PHP_INI_TO_EXPAND list in fpm_php.h as some are outdated

### Logs

- **Feat**: access log - long lines support - using the same logic as zlog ideally
  - https://github.com/php/php-src/pull/5634 - PR to discussiong it and removing unused MAX_LINE_LENGTH
  - https://github.com/php/php-src/issues/12302 - CONF Var log_limit and fpm_log_write show error "the log buffer is full ..."
  - https://github.com/php/php-src/pull/18415 - bump FPM_LOG_BUFFER from 1024 to 2048
  - https://github.com/php/php-src/pull/18328 - Allow FPM_LOG_BUFFER to be adjusted in conf file, changed the buffer to be dynamically allocated
- **Feat**: error log - master logging should be separated from child logs (special option for master log)
  - https://bugs.php.net/bug.php?id=69662 - PHP Startup errors are erroneously logged as master user in pool error log
  - https://bugs.php.net/bug.php?id=72357 - Pool logs created with master owner:group
- **Feat**: error log - allow setting format with variables for zlog errors
  - https://github.com/php/php-src/pull/11939 - Add URI in FPM logs (comment with suggestion)
- **Feat**: trace - slowlog - the SIGSTOP and SIGCONT stop script connection in stream (fsockopen) or mysql
  - https://bugs.php.net/bug.php?id=67471 - fpm slow log && fsockopen :Operation now in progress
  - https://bugs.php.net/bug.php?id=67087 - slowlog kills mysql connection
- **Feat**: trace - slowlog - option to set file permission for slow log and possibly other log files
  - https://bugs.php.net/bug.php?id=69509 - fpm slowlog file permissions feature
  - https://bugs.php.net/bug.php?id=61435 - PHP-FPM logs are not readable by group/others by default
  - https://github.com/php/php-src/pull/771 - fpm: relax log permissions (bug #61435)
- **Feat**: trace - slowlog - add request information - maybe some custom configurable fmt
  - https://bugs.php.net/bug.php?id=81501 - Log request information in slowlog
  - https://bugs.php.net/bug.php?id=79137 - Add request parameters to slow log script report
  - https://github.com/php/php-src/issues/18536 - PHP-FPM slow log entires should include the request URL
- **Feat**: access log - fmt flag for path info or available env to use
  - https://bugs.php.net/bug.php?id=81670 - Access log contains wrong values for "%r" (request URI) format string
- **Feat**: access log - respect locale for time - consider logging after request shutdown
  - https://bugs.php.net/bug.php?id=69561 - FPM access.log strftime locale not configurable
- **Feat**: access log - Allow suppression of queries
  - https://github.com/php/php-src/issues/10116 - /status?json&full is not suppressed when access.suppress_path used
- **Bug**: stdio - Nodaemonized FPM in Bash background process hangs
  - https://github.com/php/php-src/issues/10058 - If "php-fpm --nodaemonize" is called to be sent into background it hangs the calling process
- **Feat**: stdio - Use non blocking pipe for stderr
  - https://github.com/php/php-src/issues/11447 - fpm: some workers get stuck on "\0fscf\0" write to master process over time
- **Feat**: log - allow separation access and error log to stdout and stderr
  - https://bugs.php.net/bug.php?id=73886 - Handle access log & error log on Docker
  - https://github.com/php/php-src/pull/2310 - Fix #73886: Handle access log & error log on Docker (discussion)
- **Feat**: error log - SAPI log message does not split logs in Apache logs
  - https://github.com/php/php-src/issues/10890 - FPM: error_log entries all on same line
- **Feat**: error log - Customizable decoration / log_message output
  - https://github.com/php/php-src/issues/10671 - php-fpm decorate_workers_output = no removes timestamp
- **Feat**: error log - Update config with better description of decoration behavior
  - https://github.com/php/php-src/issues/13118 - Logs wrapped with newlines even when output decoration is disabled


### Status

- **Feat**: status - support full parameter for openmetrics
  - https://github.com/php/php-src/issues/9494 - FPM status with OpenMetrics format and FULL parameter
  - https://github.com/php/php-src/pull/9646 - expose per process metrics in fpm status
  - https://github.com/php/php-src/pull/12759 - expose metrics per process in fpm status
- **Feat**: status - value queries and v2 openmetrics
  - https://github.com/php/php-src/pull/7291#discussion_r676184017
- **Feat**: status - consider listing some config options values
  - https://github.com/php/php-src/issues/15011 - FPM status add more process infos
  - https://github.com/php/php-src/issues/16221 - Include the configured max_children in the fpm status page
- **Feat**: status - add parameters to list extra fields for fcgi envs
  - https://github.com/php/php-src/issues/8880 - Support fastcgi parameter in FPM for status page to display request meta data
  - https://github.com/php/php-src/pull/2713 - Enhancement: php-fpm status page shows ip address of the client (closed but idea is there)
  - https://bugs.php.net/bug.php?id=72319 - FPM status page shows wrong request_uri (generic solution for this bug - would be worth to do path info as well)
- **Feat**: status - Report proc memory and possibly other proc stats
  - https://github.com/php/php-src/issues/10600 - php-fpm status page - full view - show current worker memory usage
- **Feat**: status / ping - healtcheck support based on metrics similar to https://github.com/renatomefi/php-fpm-healthcheck
  - https://github.com/php/php-src/issues/12600 - php-fpm ping or status is to many CPU usage
- **Feat**: ping - integrate ping.listen similar to pm.status_listen
  - https://bugs.php.net/bug.php?id=68678 - FPM Ping should use a reserved worker
- **Feat**: scoreboard - track number of terminated requests
  - https://bugs.php.net/bug.php?id=78789 - Count number of request_terminate_timeout reached + killed in scoreboard
- **Bug**: status - Consider escaping script in status (unlikely so low priority)
  - https://github.com/php/php-src/issues/11464 - FPM: Consider escaping script in status
- **Bug**: status - start time invalid on Solaris (only Solaris 10 so it is a low priority)
  - https://bugs.php.net/bug.php?id=69289 - fpm_status uses wrong time_format for json and xml output


### Event and pools

- **Feat**: event - make default timeout in event loop configurable (currently hard coded 1s)
  - https://bugs.php.net/bug.php?id=71854 - FPM: Please make epoll sleep interval configurable
- **Feat**: event - Cleaning up child events when the child is killed
  - https://github.com/php/php-src/pull/9817 - FPM delete child log event before child is killed
  - https://github.com/php/php-src/pull/11940 - Remove events from the child queue
- **Feat**: signal: consider changing SIGTERM for primary idle killing instead of SIGQUIT
  - https://github.com/php/php-src/issues/12626 - Core dumps with PHP-FPM on dynamic mode
  - https://github.com/php/php-src/blob/8f02d7b7e499490312969cdfa9a3a81b9458595a/sapi/fpm/fpm/fpm_process_ctl.c#L138-L139
- **Feat**: reload - consider using SIGHUP as another reload signal
  - https://bugs.php.net/bug.php?id=67553 - Add SIGHUP as a reload signal
- **Feat**: reload - reduce number of reallocation or use buffering (stack or smart str) for sockets clean up env
  - https://github.com/php/php-src/blob/b0b416b705f5b535d95dc7d275347f89f3ef87ea/sapi/fpm/fpm/fpm_sockets.c#L71
- **Feat**: pool - look to introducing pool manager process handlig - reduce load on master and better (possibly more secure) separation and reload and balancing protocol
  - https://github.com/php/php-src/issues/11723 - FPM pool manager
  - https://bugs.php.net/bug.php?id=75440 - Fpm reload should be graceful, not killing running processes (possibly master could just re-read config and let proc mangers deal with it
  - https://bugs.php.net/bug.php?id=60961 - Graceful Restart (USR2) isn't very graceful (similar to above bug listing problems with graceful reload)
  - https://github.com/php/php-src/pull/3758 - php-fpm: graceful restart without blocking/losing requests (Mike's old PR with some useful discussion about reload)
  - https://bugs.php.net/bug.php?id=74778 - opcache_clear() puts php-fpm master in a cpu loop
  - https://bugs.php.net/bug.php?id=74709 - PHP-FPM process eating 100% CPU attempting to use kill_all_lockers (separating opache MINIT)
  - https://github.com/php/php-src/issues/8072 - php-fpm trying to kill another user's pool results in an infinite loop and 99% cpu usage (separating opache MINIT)
  - https://bugs.php.net/bug.php?id=67141 - PHP FPM vhost pollution
  - https://github.com/php/php-src/issues/14605 - Random Blank white page frequently while using php8.2-fpm
  - https://github.com/php/php-src/pull/6772 - Add FPM early bootstrapping mode
- **Feat**: pool - look to the alternative way of dynamically loading pool configuration and restarting it
  - https://bugs.php.net/bug.php?id=61595 - implement dynamic loading of pools config via file or SQL
  - https://bugs.php.net/bug.php?id=51973 - a way to restart single pools, enable/disable modules per pool
- **Feat**: pool / conf - look to supporting zend_extension in php_admin_value
  - https://bugs.php.net/bug.php?id=73408 - Loading Zend Extensions in FPM Pool Configuration
- **Feat**: pool / access log - add support stime and utime options to the pool manager
  - https://bugs.php.net/bug.php?id=62951 - Log utime and stime (patch)
- **Feat**: pool / proc - control group (;linux namespace) support
  - https://bugs.php.net/bug.php?id=80657 - Linux namespace support
  - https://bugs.php.net/bug.php?id=70605 - Option to attach a pool to a cgroup
- **Feat**: proc - look to using spawnign (fork + exec) for child creation (some sort of child executable)
  - https://github.com/php/php-src/issues/11818 - macOS now crashes fork() process instead of just warning output
- **Feat**: core - look to proper handling of huge pages to also handle reported crashes (might require some opcache work)
  - https://bugs.php.net/bug.php?id=81444 - php-fpm crashes with bus error under kubernetes

### Process management

- **Bug**: proc - ondemand race condition
  - https://github.com/php/php-src/pull/1308 - pm.ondemand forks fewer child workers than it should
  - https://bugs.php.net/bug.php?id=69724 - pm.ondemand forks fewer child workers than it should (bug for the above PR - contains extra patches)
  - https://bugs.php.net/bug.php?id=72935 - ONDEMAND: Race condition causes incoming connections hang
- **Feat**: proc - stage redefinition to consider children idle if in reading header stage
  - https://bugs.php.net/bug.php?id=78405 - FPM with keepalive: Kills worker when no request is seen for $terminate_timeout
  - https://github.com/php/php-src/pull/8163 - Fix #78405: FPM with keepalive kills workers after $terminate_timeout
  - https://bugs.php.net/bug.php?id=69367 - access.log invalid time request
- **Feat**: proc - alternative for process idle for better scaling in ondemend mode - might need some refactoring:
  - https://bugs.php.net/bug.php?id=77060 - PHP-FPM pm.process_idle_timeout behaviour (doc bug confusion asking about this behaviour)
- **Feat**: proc - look to some option in ondemand for killing inactive connections
  - https://bugs.php.net/bug.php?id=69890 - pm.ondemand does not kill children after reaching max limit
- **Feat**: proc - look to ondemand scheduling issues / improvements - using epoll (optionally for all modes)
  - https://github.com/php/php-src/issues/12798 - PHP-FPM: Killing idle child issue using pm=ondemand
  - https://github.com/php/php-src/pull/4101 - epoll discussion
  - https://github.com/php/php-src/pull/4104 - correct computation of idle time
  - https://bugs.php.net/bug.php?id=68824 - php-rpm pm=static causes load peaks when pm.max_requests is reached (epoll should resolve this)
  - https://bugs.php.net/bug.php?id=77959 - Scheduling of PHP-FPM processes in "ondemand"
  - https://bugs.php.net/bug.php?id=77060 - PHP-FPM pm.process_idle_timeout behaviour
- **Feat**: proc - look to using reuse port for listen based scheduling (round robin) instead of fcgi lock
- **Feat**: proc - Redefine boundary of pm.start_servers and pm.min_spare_servers
  - https://bugs.php.net/bug.php?id=62630 - issues with starting FPM in conditions of high load
- **Feat**: proc - consider defining timeout when no children available
  - https://bugs.php.net/bug.php?id=65503 - Timeout when max_children reached
  - https://github.com/php/php-src/issues/11260 - Timeout when max-childrens reached
- **Feat**: proc - Introduce delay for process restarts to prevent CPU exhaustion
  - https://github.com/php/php-src/issues/9632 - FPM delayed process restarting
- **Feat**: proc - add function to terminate child (this should be probably explicitly enabled in pool config)
  - https://bugs.php.net/bug.php?id=62948 - apache_child_terminate() for FPM
- **Feat**: proc - kill grand children on the child request end
  - https://github.com/php/php-src/issues/12155#issuecomment-1712492065 - PHP 8.2 FPM Leaks processes on pcntl_fork
- **Feat**: proc - free child allocated data on child termination
  - https://github.com/php/php-src/issues/11461 - FPM: Freeing child allocated data
  - https://bugs.php.net/bug.php?id=75635 - Memory leak in fpm log


## Feedback required

- https://github.com/php/php-src/issues/12449  - PHP-FPM: 8.2 random lockups of daemon

## Testing

- **Test**: status - Rewrite status check to better inform about errors and support full output
- **Test**: signals - Rename and clean up the signal reloading tests
  - bug74085-concurrent-reload.phpt
  - bug76601-reload-child-signals.phpt
- **Test**: proc - try to make sigquit test work
  - https://github.com/php/php-src/issues/8443 - sapi/fpm/tests/bug77023-pm-dynamic-blocking-sigquit.phpt test is failing frequently
- **Test**: proc - make proc idle test stable
  - https://github.com/php/php-src/pull/7561#issuecomment-980802605
- **Test**: proc - skip ondemand tests on unsupported platforms
  - https://bugs.php.net/bug.php?id=81110 - Tests use unsupported ondemand process manager
- **Test**: logs - Make log-bwd-multiple-msgs-stdout-stderr work again
- **Test**: socket - Check why bug68381 test fails with ASAN (currently skip with ASAN)
- **Test**: fcgi - Rename and clean up HTTP Status header truncation
- **Test**: binary - better integrate exit code test - bug78323.phpt

### Testing notes

Status fields
```php
    /**
     * @var array
     */
    private $defaultProcFields = [
        'pid'                 => '\d+',
        'state'               => 'Running',
        'start time'          => '\d+',
        'start since'         => '\d+',
        'requests'            => '\d+',
        'request duration'    => '\d+',
        'request method'      => '(GET|HEAD|PUT|POST|PATCH)',
        'request uri'         => '\s+',
        'content length'      => '\d+',
        'user'                => '\s+',
        'script'              => '\s+',
        'last request cpu'    => '\d+.\d+',
        'last request memory' => '\d+',
    ];
```

## Docs

- extend access log documentation - better document %e options for example
  - https://bugs.php.net/bug.php?id=62828 - Need documentation for access.format tokens
  - add note for milisecond TYPO - find version when millisecond was introduced
- proc - improve docs for pm directives - create a new section on process management
  - https://bugs.php.net/bug.php?id=81242 - Unclear documentation for process management directives


## Changes

#### 2024-12

- **Bug**: event - FreeBSD kqueue time outs
  - https://bugs.php.net/bug.php?id=76630 - php-fpm time outs unexpectedly

#### 2024-10

- **Bug** - PHP_AUTH re-use mem corruption
  - https://github.com/php/php-src/pull/16227 - Fix GH-15395: php-fpm: zend_mm_heap corrupted with cgi-fcgi request

#### 2024-07

- **Bug**: event - check for the maximum file descriptors in devpoll
  - https://bugs.php.net/bug.php?id=65774 - no max file descriptor check for events.mechanism = /dev/poll

#### 2024-06

- **Bug**: ping - look to the issue with status listen and returned 404
  - https://github.com/php/php-src/issues/14037 - PHP-FPM ping.path and ping.response config vars are ignored.
  - https://github.com/php/php-src/pull/13980 - Make /ping of php-fpm work again

#### 2024-03

- **Bug**: conf - invalid parsing of boolean value if in environment variable
  - https://github.com/php/php-src/issues/13563 - Setting boolean values via env in php config fails for all values other than 1 and ""
- **Feat**: proc - remove extra zeros in proc name
  - https://bugs.php.net/bug.php?id=77044 - Process Name has lots of null appended

#### 2024-02

- **Bug**: main - run config test just once in daemonised mode
  - https://github.com/php/php-src/issues/11086 - FPM: config test runs twice in daemonised mode

#### 2024-01

- **Bug**: main - argv and argc should not be included in env vars
  - https://bugs.php.net/bug.php?id=75712 - php-fpm's import_environment_variables impl should not copy $_ENV, $_SERVER

#### 2023-12

- **Bug**: proc - FreeBSD issue with pinging master
  - https://github.com/php/php-src/issues/12157 - php-fpm master processes runs 100% CPU and keeps spawning new ones
- **Bug**: signal - sigpipe might cause fpm to be unresponsive
  - https://bugs.php.net/bug.php?id=67320 - Ignored sigpipes in php-fpm cause php to become unresponsive

#### 2023-10

- **Bug**: conf - investigate issue with loading some extensions in pool config
  - https://github.com/php/php-src/issues/9921 - php_admin_value[extension] = ext.so in fpm config does not register module handlers
- **Bug**: fcgi - FCGI_GET_VALUES does not seem to work
  - https://bugs.php.net/bug.php?id=76922 - FastCGI terminates connection immediately after FCGI_GET_VALUES

#### 2023-09

- **Bug**: unix - validate extension_dir setting with chroot set
  - https://bugs.php.net/bug.php?id=64151 - Invalid include extension_dir

#### 2023-08

- **Bug**: socket - Add FD_CLOSEXEC on listening socket so it is not iherited by proc_open
  - https://bugs.php.net/bug.php?id=76067 - system() function call leaks php-fpm listening sockets
  - https://bugs.php.net/bug.php?id=80992 - fork() don't close fpm_globals.listening_socket
  - https://github.com/php/php-src/pull/11708/ - Set CLOEXEC on listened sockets when forking FPM children

#### 2023-06

- **Bug**: status - Check correctness of the XML escaping and whether it should be in CDATA
  - https://bugs.php.net/bug.php?id=69250 - PHP FPM status report produces invalid JSON and XML

#### 2023-05

- **Bug**: error log - Investigate why error goes to stderr instead of error log file
  - https://bugs.php.net/bug.php?id=63555 - errors outputed to stderr instead of logfile using fastcgi
- **Bug**: status - JSON is not escaped and can be invalid
  - https://bugs.php.net/bug.php?id=64539 - FPM status page: query_string not properly JSON encoded
- **Bug**: events - Prevent freeing child before accessing stdio pipe
  - https://github.com/php/php-src/pull/11084 - FPM: Postpone child freeing in event loop

### 2023-04

- **Bug**: core - crash with Runkit extension - dangling pointer
  - https://bugs.php.net/bug.php?id=72055 - php-fpm crashes on working with Runkit (contains patch)
- **Bug**: main - Apache sets extra leading slash in SCRIPT_FILENAME for UDS 
  - https://bugs.php.net/bug.php?id=67998 - Wrong SCRIPT_FILENAME
- **Bug**: main - verify the PATH_TRANSLATED logic with cgi.fix_pathinfo
  - https://bugs.php.net/bug.php?id=68053 - PHP-FPM with cgi.fix_pathinfo 0 loads script from PATH_TRANSLATED
- **Bug**: main - Look to the suggested changes for Apache and fcgi env vars
  - https://bugs.php.net/bug.php?id=51983 - [fpm sapi] pm.status_path not working when cgi.fix_pathinfo=1
- **Bug**: error log - check how changes is error log file permission impacts IP and time logged
  - https://bugs.php.net/bug.php?id=62660 - PHP error logging with FPM fails to display an IP address and correct time

### 2023-03

- **Bug**: main - correctly decode path_info before comparing to comply with cgi spec
  - https://bugs.php.net/bug.php?id=74129 - Incorrect SCRIPT_NAME with apache ProxyPassMatch when spaces are in path

### 2023-02

- **Bug**: main - check handling of multiple headers
  - https://bugs.php.net/bug.php?id=78844 - FPM does not support multiple HTTP request headers with the same name
- **Bug**: main / fcgi - investigate if file uploads can cause disk space exhaustion
  - https://bugs.php.net/bug.php?id=75889 - Overloading disk with temporary files
  - https://bugs.php.net/bug.php?id=70620 php-fpm can interrupt sapi_deactivate cleanup (Security bug - exposed by the #75889)
- **Bug**: event - Re-classify unknown child alert
  - https://github.com/php/php-src/issues/10315 - FPM unknown child alert not valid
  - https://github.com/php/php-src/issues/10258 - Unknown child (SOME_ID)
  - https://github.com/php/php-src/issues/9792 - ALERT: oops, unknown child (103) exited with code 0
  - https://github.com/php/php-src/issues/9438 - ALERT: oops, unknown child (?) exited with code 32
- **Bug**: scoreboard - slow request causing counter reset
  - https://bugs.php.net/bug.php?id=70645 - Resetting counters on status page
### 2023-01

- **Bug**: proc - fix the comment in www.conf to better clarify user, group, listen.user and listen.group (possibly also check docs correctness)
  - https://bugs.php.net/bug.php?id=67244 - Wrong owner:group for listening unix socket
- **Bug**: main - ASAN fixes

### 2022-12

- **Bug**: proc - verify user existence when runnin `php-fpm -t`
  - https://bugs.php.net/bug.php?id=68591 - Configuration test does not perform uid lookups
  - https://bugs.php.net/bug.php?id=75057 - php-fpm -t doesn't verify does user exist (duplicate)
- **Bug**: main - fastcgi.error_header does not change the header for subsequent requests
  - https://github.com/php/php-src/issues/9981 - FPM does not reset fastcgi.error_header
- **Bug**: scoreboard - inconsistent idle process count
  - https://bugs.php.net/bug.php?id=74542 - Inconsistent php-fpm status page
- **Bug**: error log - missing new line
  - https://bugs.php.net/bug.php?id=77106 - Missing newlines between PHP messages

### 2022-11

- **Bug**: The fpm_stdio_child_said can happen after the child is deleted
  - https://github.com/php/php-src/issues/8517 - Random crash of php8 - segfault...
  - https://github.com/php/php-src/pull/9444 - Fix GH-8517: FPM child pointer can be possibly uninitialized
- **Bug**: proc - initgroups fails if user numeric (uid)
  - https://bugs.php.net/bug.php?id=80669 - Can't initgroups() when specifying numeric user
- **Bug**: main - fastcgi.error_header sets header after request is sent
  - https://bugs.php.net/bug.php?id=68207 - Setting fastcgi.error_header can result in an E_WARNING being triggered
  - https://github.com/php/php-src/pull/9980 - Fix bug #68207: Setting fastcgi.error_header can result in a WARNING

### 2022-10

- **Bug**: SaltStack no longer works for PHP-8.0
  - https://github.com/php/php-src/issues/9754 - SaltStack (using Python subprocess) hangs when running php-fpm 8.1.11

### 2022-09

- **Test**: tester - Reworked logging for better debugging
  - https://github.com/php/php-src/pull/9588 - Rework FPM tests logging for better debugging
    - allow out of order log entries with some being optional and debug only collected (some sort of event based collector)
    - print all logs when error including some tracing info if possible (change log levels to debug)
### 2022-08

- **Bug**: main - incorrectly marking headers as sent when previous connection aborted
  - https://bugs.php.net/bug.php?id=77780 - "Headers already sent..." when previous connection was aborted

### 2022-06

- **Bug**: syslog - fix syslog ident issues
  - https://github.com/php/php-src/pull/7334 - fix for 81324
  - https://bugs.php.net/bug.php?id=81324 - php-fpm will not set syslog ident for children
  - https://bugs.php.net/bug.php?id=74469 - syslog.ident setting ignored when logging errors (error_log=syslog)
  - https://bugs.php.net/bug.php?id=67764 - fpm: syslog.ident don't work (truncated ?)

### 2022-05

- **Bug**: fcgi - Fix issue with content-length 0 causing nginx 502
  - https://bugs.php.net/bug.php?id=72185 - php-fpm writes stdout with contentlength =0 causing nginx 502
  - https://github.com/php/php-src/pull/3198 - fix - needs a test

### 2022-04

- **Feat**: socket - change default for listen.backlog on Linux to -1
  - https://github.com/php/php-src/pull/8410 - fpm: listen backlog should default to -1 also on Linux (reviewed and merged)
- **Bug**: proc - look to the issue with dynamic mode leaving too many idle children
  - https://bugs.php.net/bug.php?id=77023 - PHP-FPM cannot shutdown processes
- **Bug**: scoreboard - active processes above max_children (possibly related to lock issue above)
  - https://bugs.php.net/bug.php?id=76003 - FPM /status reports wrong number of active processes
- **Feat**: socket - emit error for invalid port setting (reviewed, tested and merged)
  - https://github.com/php/php-src/pull/8225 - fpm warns about port settings
- **Feat**: selinux dumpable (reviewed and merged)
  - https://github.com/php/php-src/pull/7648 - fpm dumpable process setting extra check for SElinux based systems

### 2022-03

- **Doc**: configuration - missing settings - review also as there are more missing
  - https://bugs.php.net/bug.php?id=67094 - Missing FPM settings in documentation (already done so just closed)
  - https://bugs.php.net/bug.php?id=63888 - Missing several PHP FPM ini entries in online documentation (already done so just closed)
  - missing values:
    - pm.max_spawn_rate - PHP 8.1
    - pm.status_listen - PHP 8.0
    - request_slowlog_trace_depth - PHP 7.2
    - request_terminate_timeout_track_finished - PHP
    - apparmor_hat
- **Doc**: socket - documentation listen.allowed_clients empty value (`any` is not correct name)
  - https://bugs.php.net/bug.php?id=80580 - listen.allowed_clients does not operate as expected with blank or "any" value
- **Doc**: socket - clarify docs for listen backlog values
  - https://bugs.php.net/bug.php?id=78611 - listen.backlog is not -1, and -1 does not mean 'unlimited'.

### 2022-02

- **Bug**: scoreboard - fixed locking of getting proc info
  - https://bugs.php.net/bug.php?id=76109 - Unsafe access to fpm scoreboard
  - https://bugs.php.net/bug.php?id=81275 - status page, contain bugus value in request duration sometimes
  - https://github.com/php/php-src/pull/3188 - Implement fpm_scoreboard_copy and use it for fpm_handle_status_request
  - https://github.com/php/php-src/pull/8049 - Implement fpm_scoreboard_copy (extended rebase of 3188)
  - https://github.com/php/php-src/issues/7931 - PHP-FPM worker process stuck after slow log tracing
- **Doc**: document status page
  - https://bugs.php.net/bug.php?id=72105 - Missing Documentation: PHP-FPM status page
  - https://github.com/php/doc-en/pull/738 - Documentation for the FPM status page and fpm_get_status()
  - https://github.com/php/doc-en/pull/1420 - FPM Status Page
