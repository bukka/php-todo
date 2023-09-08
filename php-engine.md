# PHP Zend Engine TODO

## Source issues

### List / Array / HashTable

- **Bug**: Check reference assigning to the list
  - https://bugs.php.net/bug.php?id=80066 - List Reference Assignment: Cannot reference an array value by return

### Objects / Functions

- **Bug**: Look to closure call reference handling
  - https://bugs.php.net/bug.php?id=72326 - Closure::call does not allow closure to accept arguments by reference

### GC

- **Bug**: Look to GC handling of circle references


## Docs

- **Doc**: resource checking inconsistencies
  - https://bugs.php.net/bug.php?id=75868 - is_resource() gettype() get_resources() inconsistent result on closed resource
- **Doc**: static variable in class usage
  - https://bugs.php.net/bug.php?id=74198 - static (variables) docs do not explain behavior in class methods
