# PHP GnuPG tasks

## Source issues

- **Feat**: Build - Homebrew support in search path _(in progress)_
  - https://github.com/php-gnupg/php-gnupg/issues/42 - PHP 8.0 Mac Apple Silicon - configure: error: Please reinstall the gpgme distribution
  - https://github.com/php-gnupg/php-gnupg/pull/43 - Add /opt/homebrew to the configuration SEARCH_PATH (my pr)
- **Feat**: CI - Add GitHub actions CI for running tests with multiple gpg and PHP versions
- **Bug**: sign - Investigate why setarmor for sign doesn't work
  - https://github.com/php-gnupg/php-gnupg/issues/38 - gnupg::setarmor(0) not respected
- **Bug**: crypt - mem leak for encrypting empty key
  - https://github.com/php-gnupg/php-gnupg/issues/37 - gnupg_decrypt() will return boolean false for decrypting an encrypted empty string
- **Bug**: crypt - Investigate issues with encrypting with multiple keys
  - https://github.com/php-gnupg/php-gnupg/issues/32 - Can't decrypt for every recipient if the message was encrypted using multiple keys
  - https://github.com/php-gnupg/php-gnupg/pull/33 - Fix decryption using multiple keys (needs test and proper review)
- **Feat**: export - Add support for exporting multiple keys
  - https://github.com/php-gnupg/php-gnupg/issues/10 - Adding Support for exporting multiple Keys
- **Feat**: export - Way to export message keys
  - https://github.com/php-gnupg/php-gnupg/pull/12 - Adding messagekeys($enctext) method which returns recipient info
- **Feat**: verify - look to some more descriptive status
  - https://github.com/php-gnupg/php-gnupg/issues/19 - Improve status on gnupg_verify function result
- **Feat**: core - Replace resource with object
- **Feat**: core - Use snake case for object method names
- **Feat**: Build - static extension compilation
  - https://bugs.php.net/bug.php?id=73509 - static extension compilation problem
- **Feat**: Build - Windows try to get gpg4win to work with PHP build (message to mailing list)
  - https://github.com/php-gnupg/php-gnupg/issues/21 - add config.w32 to aid compilation on windows

## Feedback required

- https://github.com/php-gnupg/php-gnupg/issues/39 - How can i install php-gnupg extension?
- https://github.com/php-gnupg/php-gnupg/issues/31 - Can't get php-gnupg to work
- https://github.com/php-gnupg/php-gnupg/issues/42 - PHP 8.0 Mac Apple Silicon - configure: error: Please reinstall the gpgme distribution

## Docs

- **Docs**: Crypt - better docs for ways how to choose recipients in encrypt
  - https://bugs.php.net/bug.php?id=58335 - Can't choose recipient in encrypt()
- **Docs**: Add proper gnupg class documentation


## Changes

### 2022-03

- **Docs**: Document `gnupg_deletekey`
- **Docs**: Document `gnupg_gettrustlist`
- **Docs**: Document `gnupg_listsignatures`

### 2022-01

- **Docs** - Documented `gnupg_init` options
  - https://github.com/php-gnupg/php-gnupg/issues/11 - gpg_import fails with "import failed" (closed)
  - https://github.com/php-gnupg/php-gnupg/issues/18 - gnupg_verify does not verify clearsign messages (closed)
- **Docs** - Documented `gnupg_geterrorinfo`
- **Docs** - Documented `gnupg_getengineinfo`
- **Docs** - Improve CS in examples