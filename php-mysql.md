# PHP MySQL related tasks

### MySQLi issues

2008-2019

- **Bug**: Verify connection stats enabling and usage
  - https://bugs.php.net/bug.php?id=61837 - Problem collecting stats with mysqlnd _(0 votes)_
- **Bug**: Look into local in file MYSQLI_OPT_LOCAL_INFILE overwrite
  - https://bugs.php.net/bug.php?id=77496 - mysqli->real_connect() overwrites MYSQLI_OPT_LOCAL_INFILE setting
- **Bug**: Check mysqli_commit working when MYSQLI_ASYNC
  - https://bugs.php.net/bug.php?id=69656 - mysqli_commit does not commits with MYSQLI_ASYNC, mysqli_kill returns false _(10 votes)_
- **Bug**: Test possible issues with persistent connection and ssl_set
  - https://bugs.php.net/bug.php?id=78870 - Connection errors appear in error.log
  - https://bugs.php.net/bug.php?id=55283 - SSL options set by mysqli_ssl_set ignored for MySQLi persistent connections _(12 votes)_
- **Bug**: ssl_set should try to enable peer veryfication
  - https://bugs.php.net/bug.php?id=54962 - either real_connect or ssl_set is not working properly _(1 vote)_
- **Bug**: Look into improving timeout behavior
  - https://bugs.php.net/bug.php?id=76703 - MYSQLI_OPT_READ_TIMEOUT cannot be changed after connection established

## MySQLnd issues

- **Bug**: Look into special hostname based peer veryfication enabling
  - https://bugs.php.net/bug.php?id=72048 - No way to disable peer name verification _(58 votes)_
  - https://github.com/php/php-src/issues/8769 - ext-mysqlnd: can't set SSL server hostname verification independent of general certificate validation
- **Bug**: Investigate MySQL perf and scaling issue:s 
  - https://github.com/php/php-src/commit/58006537fc5f133ae8549efe5118cde418b3ace9
  - https://github.com/php/php-src/issues/9634
  - https://bugs.php.net/bug.php?id=81719
  - https://bugs.php.net/bug.php?id=74971 - (HY000/2002): Resource temporarily unavailable
  - https://bugs.php.net/bug.php?id=76565 - Very slow DB queries
- **Bug**: Investigate large packets failures
  - https://bugs.php.net/bug.php?id=78797 - mysqlnd cannot read large OK/ERR packets
  - https://github.com/php/php-src/issues/9787 - Mysqlnd: packet headers bigger than buffer (4096) miss DB errors and put driver in inconsistent state
- **Bug**: Look to the MariaDB packet splitting issue
  - https://github.com/php/php-src/issues/10063 - max_allowed_packet=16777216 causes test failure on ext/mysqli/tests/mysqli_real_connect_compression_error.phpt
- **Bug**: Possible crash in stmt eof and result
  - https://github.com/php/php-src/blob/62e53e6f4965f37d379a3fd21f65a4210c5c86b5/ext/mysqlnd/mysqlnd_ps.c#L351-L355
- **Bug**: Look into the port setting issues and IPv6 parsing
  - https://github.com/php/php-src/issues/8978 - MySQLi: SSL certificate verification fails (port doubled) 
  - https://github.com/php/php-src/pull/10922 - Fix implicit/explicit port in mysqlnd
  - https://bugs.php.net/bug.php?id=67563 - mysqli compiled with mysqlnd does not take ipv6 adress as parameter _(17 votes)_
- **Bug**: Implement missing `MYSQL_READ_DEFAULT_FILE`
  - https://bugs.php.net/bug.php?id=43812 - MYSQLI_READ_DEFAULT_FILE option ignored when using mysqlnd
- **Bug**: Look into JWT auth failure
  - https://github.com/php/php-src/issues/10800 - mysqli::real_connect(): Authentication data too long. Won't fit into the buffer and will be truncated. Authentication will thus fail
- **Feat**: Support ED25519 auth
  - https://github.com/php/php-src/issues/14258 - Implement ED25519 auth for mysqlnd

## Tests

- Look to adding MariaDB to CI
  - https://github.com/php/php-src/pull/10062 - Add MariaDB to the Github actions
- Extend fake server coverage

