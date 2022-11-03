# PHP OpenSSL tasks

## Source issues

### TLS

- **Bug**: OpenSSL 1.0.2 locking issues
  - https://github.com/php/php-src/issues/8620 - Segmentation fault on exit when using ldap_bind() 
- **Bug**: Check issue with TLS 1.3 in phpredis
  - https://bugs.php.net/bug.php?id=79501 - TLS connections freezing on 7.4 (all versions after 7.3.17)
- **Bug**: Check and fix SAN IP validation
  https://github.com/php/php-src/issues/9356 - Incomplete validation of IP Address fields in subjectAltNames
- **Bug**: Roundcube peer veryfication issue
  - https://bugs.php.net/bug.php?id=79909 - verify_peer => true, connection "Error: Login failed ... Unknown reason"
- **Bug**: Check issue with connection to server with chain containing 3 intermediates wiht RabbitMQ
  - https://bugs.php.net/bug.php?id=78414 - TLS handshake fails when the certificate chain has more than 2 certificates
- **Bug**: Issue with proxied file_get_contents with https
  - https://bugs.php.net/bug.php?id=76196 - proxied file_get_contents calls lag the cert check one behind for further calls
- **Bug**: Check corrupted wsdl fetching result if fetching gzip
  - https://bugs.php.net/bug.php?id=79575 - Content-Length header name is getting corrupted
- **Bug**: Allow getting client certificate when provided
  - https://bugs.php.net/bug.php?id=80770 - It is not possible to get client peer certificate with stream_socket_server
- **Bug**: Check why stream_context_set_default does not set options for veryfying self signed cert
  - https://bugs.php.net/bug.php?id=69319 - stream_context_set_default() options not set as default in streaming functions
- **Bug**: Consider notice for unsupported method flag
  - https://bugs.php.net/bug.php?id=81213 - Stream crypto methods SSLv2 and v3 switch to TLS1.0
- **Bug**: The `SSL: Success` warning in failed connection does not make much sense
  - https://github.com/php/php-src/issues/9261#issuecomment-1218471408 - Problem with enabling crypto on stream socket connection
- **Bug**: Check stream_socket_client async issue
  - https://bugs.php.net/bug.php?id=49295 - stream_socket_client() fails on SSL+async
- **Feat**: Refactore async code and provide info about WANT_READ and WANT_WRITE to PHP code
  - https://github.com/php/php-src/pull/2605 - Avoid triggering SIGPIPE after stream_socket_shutdown(SHUT_WR) of a SSL stream (bug report containing discussion)
  - https://bugs.php.net/bug.php?id=68732 - Unchecked return value (this should be addressed as part of refactoring)
  - https://bugs.php.net/bug.php?id=75288 - stream_socket_enable_crypto() blocks during handshake
- **Feat**: Check if liveness poll skipping improvement is worth it
  - https://github.com/php/php-src/pull/8829 - Improve php_openssl_sockop_set_option logic for liveness poll skipping
- **Feat**: Add option to not add SSL_OP_IGNORE_UNEXPECTED_EOF (opt in protection for truncation attack) - create a proper test with proxy and TCP FIN
  - https://github.com/php/php-src/issues/8369#issuecomment-1126940364 - note about that in the bug
- **Feat**: Allow multiple peer fingerprints in the context
  - https://bugs.php.net/bug.php?id=81528 - Support multiple peer_fingerprint values per algorithm
- **Feat**: Support TLS PSK
  - https://bugs.php.net/bug.php?id=79280 - Add support for TLS-PSK
- **Feat**: Extend TLS 1.3 support - 0-RTT (early data), ciphrsuite options and possible more
- **Feat**: Support OCSP stapling


### Crypto

- **Bug**: pkey - fix --no-ec build
  - https://github.com/php/php-src/issues/9064 - PHP fails to build if openssl was built with --no-ec
- **Bug**: pkey - Missing types supported by openssl_public_encrypt
  - https://bugs.php.net/bug.php?id=76676 - OPENSSL_KEYTYPE_EC (and others) not supported by openssl_public_encrypt()
- **Bug**: pkey - Incorrect returned array for SM2 key (DH key in it)
  - https://github.com/php/php-src/issues/9422#issuecomment-1229484671 - comment in openssl ext sm2 compatibility
- **Feat**: pkey - SM2 support
  - https://github.com/php/php-src/issues/9422 - openssl ext sm2 compatibility
- **Feat**: pkey - Improve php_openssl_dh_compute_key to support ECDH before OpenSSL 3.0 and extend tests
- **Feat**: pkey - Allow setting padding for openssl_verify
  - https://bugs.php.net/bug.php?id=80495 - Enable to set padding in openssl_verify
- **Feat**: pkey - Consider adding PKCS#8 export format support
  - https://bugs.php.net/bug.php?id=77602 - OpenSSL extension lacks PKCS#8 support
- **Feat**: seal/open - Allow AEAD
  - https://github.com/php/php-src/issues/7737 - openssl_seal()/_open() is not able to handle gcm cipers, e.g. aes-256-gcm
- **Bug**: CSR Allow multiple fields in openssl_csr_new for distinguished_names argument
  - https://bugs.php.net/bug.php?id=48520 - openssl_csr_new does not allow multiple values/field in dn
- **Bug**: CSR - Correctly set SAN
  - https://bugs.php.net/bug.php?id=71050 - SubjectAltName (SAN) is Not included in openssl_csr_sign of a new CSR
- **Bug**: CSR - Do not put extraattribs to Subject
  - https://bugs.php.net/bug.php?id=80269 - OpenSSL sets Subject wrong with extraattribs parameter
- **Feat**: Add function for more detailed parsing of CSR - php openssl csr parser ignores SANs
  - https://bugs.php.net/bug.php?id=55820 - php openssl csr parser ignores SANs
  - https://bugs.php.net/bug.php?id=29961 - an openssl_csr_parse function would be handy
- **Bug**: X509 - Check new line parsing in subjectAltName
  - https://bugs.php.net/bug.php?id=60388 - openssl_x509_parse extensions=>subjectAltName
- **Bug**: X509 - Look to the issue with default certs added to store in setup_verify
  - https://bugs.php.net/bug.php?id=65154 - setup_verify implicitly adds default CA paths
- **Bug**: X509 - Check why checking X509_PURPOSE_SSL_SERVER with openssl_x509_checkpurpose returns false
  - https://github.com/php/php-src/issues/8371 - check_cert() insists on all provides certificates to validate against system CA store
  - https://github.com/php/php-src/issues/8372 - check_cert() and php_openssl_store_errors do not pick up validation errors
- **Bug**: X509 - Check why checking X509_PURPOSE_ANY with openssl_x509_checkpurpose returns false
  - https://bugs.php.net/bug.php?id=55362 - X509_PURPOSE_ANY is not recognized by openssl
- **Feat**: X509 - Add addition X509 purpose constants
  - https://github.com/php/php-src/pull/6312 - Add X509 purpose constant (requires changes to support 1.0.2)
- **Feat**: X509 - Analyse if returning large serial numbers can cause slow down
  - https://github.com/php/php-src/pull/6445 - Fix #77411 - large serialNumber returned as hex with OpenSSL 1.1
  - https://bugs.php.net/bug.php?id=77411 - openssl_x509_parse serialNumber not always integer with OpenSSL version 1.1
- **Feat**: X509 - Extend openssl_x509_parse with more info about pub key if possible
  - https://bugs.php.net/bug.php?id=77761 - openssl_x509_parse does not create entries for public key type and size
- **Feat**: X509 - Optimize order of operations in php_openssl_load_all_certs_from_file
- **Bug**: PKCS7 - Add test for PR to fix openssl_pkcs7_verify with signers_certificates_filename
  - https://github.com/php/php-src/pull/6927 - openssl_pkcs7_verify() may ignore untrusted CAs
  - https://bugs.php.net/bug.php?id=50713 - openssl_pkcs7_verify() may ignore untrusted CAs
- **Bug**: PKCS7 - Investigate why envelope encrypted with cert created using openssl_csr_sign is not decrypted
  - https://bugs.php.net/bug.php?id=66122 - Certification cannot be used directly after openssl_csr_sign
- **Feat**: PKCS7 - Add constants for all PKCS7 flags
  - https://bugs.php.net/bug.php?id=47728 - openssl_pkcs7_sign ignores new openssl flags
- **Feat**: PKCS7 - New function to retrieve signer certificates (using PKCS7_get_signer_info)
  - https://bugs.php.net/bug.php?id=72249 - Add Support for PKCS7_get_signer_info
- **Feat**: PKCS7 - Allow adding a signature with custom digest (using PKCS7_add_signature)
  - https://bugs.php.net/bug.php?id=68366 - Does not use certificate's signing algorithm
- **Feat**: PKCS7 - Look to the non file arg variants for openssl_pkcs7_(sign|verify|encrypt|decrypt) (if not addressed by #50718)
  - https://bugs.php.net/bug.php?id=55045 - openssl_pkcs7_sign() & openssl_pkcs7_encrypt()
  - https://bugs.php.net/bug.php?id=52356 - In memory support for openssl_pkcs7_*
  - https://bugs.php.net/bug.php?id=22978 - (openssl_pkcs7_verify) pem saved into variable
- **Bug**: PKCS12 - openssl_pkcs12_read should check file path - investigate how it actually read the file
- **Bug**: CMS - openssl_cms_read should check file path - investigate how it actually read the file (uses PEM_read_bio_CMS)
  - should apply for PKCS7 as well
- **Bug**: CMS - openssl_cms_verify should clean exit if sigbio is NULL
- **Feat**: CMS - Extend with some new features in PKCS7 if applicable
- **Feat**: CMS - Add AES GCM constant
  - https://bugs.php.net/bug.php?id=81724 - openssl_cms/pkcs7_encrypt only allows specific ciphers
- **Feat**: CMS - Try to reuse CMS and PKCS7 code - reduce duplications
- **Bug**: config - add path check for config filename (possible break so only master probably)
  - https://github.com/php/php-src/issues/9317
  - php_openssl_parse_config function
  - MINIT config filename
  - consider also cafile locations from ini
- **Bug**: pkey - RAND_file_name could potentially not work correct with open basedir check and do rand file checks
- **Bug**: pkey - Do not try to use Rand file when generating key
  - https://bugs.php.net/bug.php?id=78444 - openssl_pkey_new generates OpenSSL errors with OpenSSL 1.1.1
- **Bug**: general - Review binary file mode settings (PKCS7_BINARY and CMS_BINARY)
  - passing flags does not make much sense in many cases
- **Feat**: general - Look to the stream support for the input params (start with investigation and implemetation ideas)
  - https://bugs.php.net/bug.php?id=50718 - OpenSSL* doesnt support streamwrappers
- **Feat**: constants - Consider defining LIBRESSL_VERSION_NUMBER when available
  - https://bugs.php.net/bug.php?id=71143 - Define LIBRESSL_VERSION_NUMBER when available
- **Feat**: crypt - Consider tag length veryfication
  - https://bugs.php.net/bug.php?id=75804 - authenticated encryption tag is broken
- **Feat**: CRL functions support
  - https://bugs.php.net/bug.php?id=40046 - OpenSSL CRL generation support (patch)
- **Feat**: PKCS11 support (waiting for available provider)
  - https://github.com/php/php-src/pull/6860 - RFC7512 URI support
  - https://github.com/php/php-src/issues/7797 - SSL context options for in memory cert and pk (addressed by PKCS11 PR)
- **Feat**: FIPS - check if it works - FIPS Support
  - https://bugs.php.net/bug.php?id=54339
- **Bug**: build - Check shared build issue
  - https://bugs.php.net/bug.php?id=73609 - "run-tests.php" don't respect configuration


## Docs

- tls - Document crypto_method context option
  - https://bugs.php.net/bug.php?id=68131 - crypto_method context option not documented.
- crypt - openssl_encrypt - Remove insecure examples
  - https://bugs.php.net/bug.php?id=80843 - Remove examples from comments as they are invariably insecure
- crypt - AEAD tag setting clarification
  - https://bugs.php.net/bug.php?id=80236 - How $tag works in openssl_encrypt() with GCM mode is unclear
- crypt - extend openssl_encrypt and openssl_decrypt docs
  - https://bugs.php.net/bug.php?id=77282 - openssl_decrypt "options" parameter section is incomplete
  - https://bugs.php.net/bug.php?id=74134 - openssl_encrypt/decrypt docs need improvement, like examples
- crypt - Document that AES-256-XTS is not supported
  - https://bugs.php.net/bug.php?id=78628 - AES-256-XTS cipher method does not work
- pkey - Document openssl_public_encrypt without padding (that exact size is required)
  - https://bugs.php.net/bug.php?id=61203 - RSA encryption fails without padding
- CSR - extend openssl_csr_new documentation including a note about text param
  - https://bugs.php.net/bug.php?id=65186 - openssl_csr_new allows creation from text
- installation - Update https://www.php.net/manual/en/openssl.installation.php to reflect that `--with-openssl` no longer works
  - https://bugs.php.net/bug.php?id=79401 - --with-openssl no longer accepts a directory

## Changes

### 2022-10

- **Bug**: pkey / md alg - fix compilation without some old digests
  - https://github.com/php/php-src/pull/8431 - openssl.c: Add opensslconf.h checks for md2, md4, md5 and rmd160
  - https://github.com/php/php-src/pull/8135 - openssl: allow support for nonessential hash function to be absent
  - https://github.com/php/php-src/issues/8430 - openssl.c - ignores opensslconf.h & fails to link

### 2022-08

- **Feat**: crypt - Add chacha20-poly1305 support
  - https://bugs.php.net/bug.php?id=76935 - "chacha20-poly1305" is an AEAD but does not work like AEAD
- **Feat**: crypt - New function to retrieve key length (using EVP_CIPHER_key_length)
- **Bug**: Persistent connection after error handler is not closed
  - https://github.com/php/php-src/issues/8409 - SSL handshake timeout leaves persistent connections hanging

### 2022-06

- **Bug**: Fix openssl path checking for VCWD and null bytes (#50293 and #81713) in OpenSSL functions
  - https://github.com/php/php-src/pull/8667
### 2022-05

- **Bug**: Fix close_notify changes in OpenSSL 3.0 causing connection issues
  - https://bugs.php.net/bug.php?id=79589 - error:14095126:SSL routines:ssl3_read_n:unexpected eof while reading
  - https://github.com/php/php-src/issues/8369 - OpenSSL 3: Support of SSL_OP_IGNORE_UNEXPECTED_EOF context option
### 2022-03

- **Doc**: Requirements - Mention in the docs that OpenSSL 3.0 won't be updated for versions before 8.1
  - https://bugs.php.net/bug.php?id=81540 - OpenSSL 3.0.0 is not supported prior to 8.1.0