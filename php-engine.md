# PHP Zend Engine TODO

## Source issues

### Execution

- **Feat**: Allow setting time limit with float
  - https://github.com/php/php-src/issues/13024 - set_time_limit function to accept float

### INI

- **Bug**: Look to parse ini tokens using keywords
  - https://bugs.php.net/bug.php?id=68347 - parse_ini_file: warning on string containing "on"
- **Feat**: Look into supporting namespaced contants parsing
  - https://bugs.php.net/bug.php?id=52227 - parse_ini_* does not parse namespaced constants _(9 votes)_
- **Feat**: Add support for INI variables pointing to other INIs with section scope
  - https://bugs.php.net/bug.php?id=34274 - parse_ini_file does not recognize ${key} _(4 votes)_

### List / Array / HashTable

- **Bug**: Check reference assigning to the list
  - https://bugs.php.net/bug.php?id=80066 - List Reference Assignment: Cannot reference an array value by return

### Objects / Functions

- **Bug**: Look to closure call reference handling
  - https://bugs.php.net/bug.php?id=72326 - Closure::call does not allow closure to accept arguments by reference

### GC

- **Bug**: Look to GC handling of circle references

### Signals

- **Bug**: Signal handling for ZTS
  - https://github.com/php/php-src/pull/10193 - fix: disable Zend Signals by default for ZTS builds

### Shutdown and exit

-  **Feat**: Look to handling shutdown callback after fatal error
  - https://github.com/php/php-src/issues/12967 - set_error_handler should be able to handle fatal error once

## Docs

- **Doc**: resource checking inconsistencies
  - https://bugs.php.net/bug.php?id=75868 - is_resource() gettype() get_resources() inconsistent result on closed resource
- **Doc**: static variable in class usage
  - https://bugs.php.net/bug.php?id=74198 - static (variables) docs do not explain behavior in class methods
- **Doc**: INI - Document parsing of new lines
  - https://bugs.php.net/bug.php?id=55091 - parse_ini_file: last escaped double-quote of multiline ends read