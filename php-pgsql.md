# PHP PgSQL related tasks

### pgsql issues

- **Bug**: Look into performance issue for getting the types (mainly caching them)
  - https://github.com/php/php-src/issues/9692 - pg_field_type first call is very slow
  - https://bugs.php.net/bug.php?id=75705 - pg_field_type() slow and consumes CPU on a large database
- **Bug**: Look into issue with bytea converstion
  - https://bugs.php.net/bug.php?id=73250 - pg_convert doesn't support bytea
- **Bug**: UUID converstion support missing
  - https://bugs.php.net/bug.php?id=72124 - pg_convert prefixes UUIDs with escape string constant
- **Bug**: Look into other missing conversion types
  - https://bugs.php.net/bug.php?id=73264 - pg_convert rejects valid values for several data types
- **Bug**: Look into search path issue for pg_meta_data search
  - https://bugs.php.net/bug.php?id=76916 - pg_meta_data Does Not Respect PostgreSQL search_path
- **Feat**: Look into meta data cache option
  - https://github.com/php/php-src/pull/11193 - ext/pgsql: adding cache for the tables meta data.
- **Feat**: Check and possibly extend pg_meta_data
  - https://bugs.php.net/bug.php?id=38707 - primary and foreign key data in pg_meta_data
- **Feat**: Look into some boolean (and int) autoconversion options
  - https://bugs.php.net/bug.php?id=60187 - pgsql module returns strings from SELECT queries for each unempty field
  - https://bugs.php.net/bug.php?id=68156 - pg_query_params Sets Boolean False to Blank String
  - https://bugs.php.net/bug.php?id=78855 - Native PHP types in database fetches
- **Feat**: Look into supporting array and other type if not already
  - https://bugs.php.net/bug.php?id=41241 - Realization array type. SQL 2003, S091
- **Feat**: Look into extending pg_copy_from and pg_copy_to with escape
  - https://github.com/php/php-src/issues/7996 - new parameter in pg_copy_from and pg_copy_to
  - https://github.com/php/php-src/pull/14441 - Fix GH-7996: Adding new parameter to pg_copy_from/pg_copy_to
- **Feat**: Add support for fields ordering to pg_copy_from
  - https://bugs.php.net/bug.php?id=69457 - pg_copy_from: order of table fields
- **Feat**: Look into some pg fetch alternatives
  - https://bugs.php.net/bug.php?id=44757 - use sql-id as key
- **Feat**: Look into pipeline improvements / fixes
  - https://github.com/php/php-src/issues/9344 - PGSQL pipeline mode
  - https://github.com/php/php-src/pull/13225 - pgsql pipeline mode
  - https://github.com/php/php-src/pull/12686 - Fix GH-12685: Adding PGSQL_STATUS_PIPELINE_ABORTED constant for
  - https://github.com/php/php-src/issues/12685 - PGSQL pipeline mode constant PGRES_PIPELINE_ABORTED not found and naming problem
- **Feat**: Look into getting SQLSTATE from libpq (would require changes in libpq)
  - https://github.com/php/php-src/issues/18335 - Feature Request: Add SQLSTATE return when the pg_connect() failed to the error text


### Docs

- **Doc**: Look into updating pg_query_params() return type docs
  - https://bugs.php.net/bug.php?id=63046 - pg_query_params() NULLs aren't converted (contrary to the docs)
- **Doc**: Clarify how pg_get_result works
  - https://bugs.php.net/bug.php?id=79253 - doc for pg_get_result() fails to mention its implementation is syncronous
- **Doc**: Document name limits
  - https://bugs.php.net/bug.php?id=81173 - Fatal error. PHP7-8 PG Prepared statement name collision