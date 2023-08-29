# PHP JSON tasks

## Source issues

- **Feat**: encoding serialization - serializable generators
  - https://bugs.php.net/bug.php?id=72238 - Make Generator class serialisable in JSON
- **Feat**: encoding - Check and possibly close JSON_NUMERIC_CHECK change request
  - https://bugs.php.net/bug.php?id=80484 - json_encode() without converting string to float
- **Feat**: encoding - Changes in encoding lead zero
  - https://bugs.php.net/bug.php?id=79908 - json_encode encodes negative zero as int
  - https://github.com/php/php-src/pull/7234 - json_decode decodes negative zero as positive zero
- **Feat**: encoding - Consider proposed JSON_NUMERIC_LEADZERO option
  - https://bugs.php.net/bug.php?id=79189 - json_encode with JSON_NUMERIC_CHECK and extra option
- **Feat**: encoding - customisable pretty printing - indent
  - https://bugs.php.net/bug.php?id=76005 - Ability to specify indentation string for json_encode with JSON_PRETTY_PRINT
  - https://github.com/php/php-src/pull/7093 - Add json_encode indent parameter
- **Feat**: encoding - customisable pretty printing - new line
  - https://bugs.php.net/bug.php?id=74419 - JSON_PRETTY_PRINT prints only Unix newlines
- **Feat**: encoding - option to disallow objects
  - https://bugs.php.net/bug.php?id=78786 - json_encode should have an option to disallow objects
- **Feat**: decoding - Optional disallowing of duplicite keys
  - https://bugs.php.net/bug.php?id=78765 - enhancement to json_decode : treat a JSON string with duplicate keys as invalid
- **Feat**: decoding - Consider option to return non parsed json string for recursion out of scope (not probably possible)
  - https://bugs.php.net/bug.php?id=75915 - json_decode recursion level misleading
- **Feat**: decoding - Look to simd support and possible replacing of json parser to be LL
- **Feat**: Errors - Look to re-considering JSON_THROW_ON_ERROR behaviour
  - https://bugs.php.net/bug.php?id=77997 - json_last_error should work even if JSON_THROW_ON_ERROR
- **Feat**: spec - JsonSchema support 
  - https://bugs.php.net/bug.php?id=69422 - json_encode() needs encoding specification


## Changes

### 2023-08

- **Bug**: encoding serialization - var_dump inside jsonSerialize issue
  - https://bugs.php.net/bug.php?id=81524 - json_encode() on JsonSerializable populates the properties HashTable
  - https://github.com/php/php-src/pull/7589 - Use HT for recursion protection in JSON encode (perf issue fix)
  - https://github.com/php/php-src/pull/9703 - Don't build prop table during json_encode(JsonSerializable) (breaking attempt)

### 2022-03

- **Doc**: Closed request to better documented json_decode as it is just type juggling
  - https://bugs.php.net/bug.php?id=81685 - Using json_decode with an integer as first parameter doesn't return NULL