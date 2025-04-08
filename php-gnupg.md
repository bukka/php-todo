# PHP GnuPG tasks

## Source issues

- **Bug**: crypt - Investigate issues with encrypting with multiple keys
  - https://github.com/php-gnupg/php-gnupg/issues/32 - Can't decrypt for every recipient if the message was encrypted using multiple keys
  - https://github.com/php-gnupg/php-gnupg/pull/33 - Fix decryption using multiple keys (needs test and proper review)
- **Feat**: export - Add support for exporting multiple keys
  - https://github.com/php-gnupg/php-gnupg/issues/10 - Adding Support for exporting multiple Keys
- **Feat**: export - Way to export message keys
  - https://github.com/php-gnupg/php-gnupg/pull/12 - Adding messagekeys($enctext) method which returns recipient info
- **Feat**: generate - Introduce support for generating / creating keys - preferrably using gpgme_op_createkey
- **Feat**: keyinfo - Add `can_encrypt`, `can_sign`, `can_certify` and `can_authenticate` to the main key
- **Feat**: keyinfo - Add user signatures
- **Feat**: sign - support key signing using gpgme_op_keysign
- **Feat**: verify - Look to some more descriptive status
  - https://github.com/php-gnupg/php-gnupg/issues/19 - Improve status on gnupg_verify function result
  - https://github.com/php-gnupg/php-gnupg/issues/45 - Verification of Valid Signature fails - potentially because key is expired
- **Feat**: manipulate - Add support for key manupaltion - gpgme_op_setexpire, gpgme_op_setownertrust
- **Feat**: errors - Introduce error constants for easier matching of error code from error info
- **Feat**: gpg - Check if there is some way to identify issues caused by gpg configuration
- **Feat**: core - Replace resource with object and get rid of phpc as part of it
- **Feat**: core - Use snake case for object method names
- **Feat**: CI - cover more gpgme and PHP versions
- **Feat**: CI - add macos and arm runners
- **Feat**: Build - static extension compilation
  - https://bugs.php.net/bug.php?id=73509 - static extension compilation problem
- **Feat**: Build - Windows try to get gpg4win to work with PHP build (message to mailing list)
  - https://github.com/php-gnupg/php-gnupg/issues/21 - add config.w32 to aid compilation on windows

## Dodcumentation issues

- **Doc**: sign - Document gnupg constants
  - https://github.com/php-gnupg/php-gnupg/issues/38 - gnupg::setarmor(0) not respected

## Feedback required

- https://github.com/php-gnupg/php-gnupg/issues/39 - How can i install php-gnupg extension?
- https://github.com/php-gnupg/php-gnupg/issues/31 - Can't get php-gnupg to work
- https://github.com/php-gnupg/php-gnupg/issues/42 - PHP 8.0 Mac Apple Silicon - configure: error: Please reinstall the gpgme distribution


## Docs

- Add missing tests for following functions:
  - `gnupg_getprotocol`
  - `gnupg_clearsignkeys`
  - `gnupg_clearencryptkeys`
  - `gnupg_cleardecryptkeys`
  - `gnupg_gettrustlist`

## Docs

- **Docs**: Crypt - better docs for ways how to choose recipients in encrypt
  - https://bugs.php.net/bug.php?id=58335 - Can't choose recipient in encrypt()
- **Docs**: Add proper gnupg class documentation


## Changes

### 2025-04

- **Task**: crypt - Investigate if User ID hint is always 16 bytes
  - https://github.com/bukka/php-gnupg/blob/a32dc2f988ee9b3afe1234642a2febb9a0cc435e/gnupg.c#L685 - line that relies on 16 bytes uid_hint

### 2025-03

- **Bug**: crypt - mem leak for encrypting empty key
  - https://github.com/php-gnupg/php-gnupg/issues/37 - gnupg_decrypt() will return boolean false for decrypting an encrypted empty string
- **Bug**: crypt - segfault when using some private keys with passphrase in gpg 2.3
  - https://github.com/php-gnupg/php-gnupg/issues/46 - gnupg.so error with gnupg 2.3.7

### 2025-02

- **Bug**: engine - check issue with not checking engine selection error
  - https://github.com/php-gnupg/php-gnupg/issues/47 - Return value of gpgme_ctx_set_engine_info is not checked, causes confusing errors
- **Feat**: CI - Add GitHub actions CI for running tests with multiple gpg and PHP versions

### 2022-03

- **Docs**: Document `gnupg_deletekey`
- **Docs**: Document `gnupg_gettrustlist`
- **Docs**: Document `gnupg_listsignatures`

### 2022-02

- **Feat**: Build - Homebrew support in search path _(in progress)_
  - https://github.com/php-gnupg/php-gnupg/issues/42 - PHP 8.0 Mac Apple Silicon - configure: error: Please reinstall the gpgme distribution
  - https://github.com/php-gnupg/php-gnupg/pull/43 - Add /opt/homebrew to the configuration SEARCH_PATH
### 2022-01

- **Docs** - Documented `gnupg_init` options
  - https://github.com/php-gnupg/php-gnupg/issues/11 - gpg_import fails with "import failed" (closed)
  - https://github.com/php-gnupg/php-gnupg/issues/18 - gnupg_verify does not verify clearsign messages (closed)
- **Docs** - Documented `gnupg_geterrorinfo`
- **Docs** - Documented `gnupg_getengineinfo`
- **Docs** - Improve CS in examples