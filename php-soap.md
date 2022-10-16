# PHP SOAP tasks

## Source issues

- **Bug**: SDL - Allow the same names if namespace is different
  - https://bugs.php.net/bug.php?id=45282 - SoapClient has namespace issues when WSDL is distributed _(136 votes)_
  - https://bugs.php.net/bug.php?id=46878 - my wsdl is not loaded correctly _(4 votes)_
- **Bug**: Client/SDL - Investigate missing nested types in SoapClient.__getTypes (possibly related to namespaces)
  - https://bugs.php.net/bug.php?id=45404 - SoapClient.__getTypes don't care about inheritance _(32 votes)_
- **Bug**: Server - Incorrect method called
  - https://bugs.php.net/bug.php?id=49169 - SoapServer calls wrong function, although "SOAP action" header is correct _(76 votes)_
- **Bug**: Server - Report validation errors
  - https://bugs.php.net/bug.php?id=45966 - SoapServer does not report WSDL validation errors _(74 votes)_
- **Bug**: Client/Server - Investigate what can be done about calling constructor for classmap
  - https://bugs.php.net/bug.php?id=45155 -	Constructors not called when using classmap option in SoapClient _(74 votes)_
- **Bug**: Encoding - Proper DateTime object conversion
  - https://bugs.php.net/bug.php?id=44383 - PHP DateTime not converted to xsd:datetime _(85 votes)_
- **Bug**: Encoding - Incorrect handling of abstract types
  - https://bugs.php.net/bug.php?id=47924 - Bug #47924 	Exchange 2007: UpdateItem: Fatal error: SOAP-ERROR: Encoding: object hasn't 'Path' _(31 votes)_
  - https://bugs.php.net/bug.php?id=49577 - Invalid returntype of anyType _(6 votes)_
- **Bug**: Encoding/SDL - SubstitutionGroup in schema is not supported
  - https://bugs.php.net/bug.php?id=48570 - SubstitutionGroup in XML schema not supported _(17 votes)_
- **Bug**: Encoding/SDL - Error for ref element
  - https://bugs.php.net/bug.php?id=46679 -	WSDL Error SOAP-ERROR unresolved element 'ref'_(14 votes)_
  - http://wssie.eau-loire-bretagne.fr/AELB-IWS-MONITORING/services/MonitoringService?wsdl (stored locally just in case)
- **Bug**: Encoding/SDL - Parameter ignored if special SOAP name used (seems like some sort of reserved words issue)
  - https://bugs.php.net/bug.php?id=49155 - SoapServer passes parameters as null if one has special wsdl definition _(7 votes)_
- **Bug**: Encoding - Ignored enumeration restriction
  - https://bugs.php.net/bug.php?id=47934 - SOAP server ignores enumeration restrictions in WSDL _(25 votes)_
- **Bug**: Encoding - Incorrect int and float types conversion
  - https://bugs.php.net/bug.php?id=47624 - SOAP response has int type for a key value that is out of range _(14 votes)_
  - https://bugs.php.net/bug.php?id=48717 - Cannot pass datatype long (> 2147483647) in SOAP requests _(23 votes)_
- **Bug**: Encoding - Check a way to put namespaces to the nested tags
  - https://bugs.php.net/bug.php?id=48966 - namespace in soap headers not put into nested tags _(34 votes)_
- **Bug**: Encoding - Look to the increased namespace alias - whether it would be possible to provide custom (more a feature maybe)
  - https://bugs.php.net/bug.php?id=48165 - SoapClient and external import in WSDL make ns1, ns2, ns3 alias _(17 votes)_
- **Bug**: Client - Incorect respone for __getLastResponseHeader
  - https://bugs.php.net/bug.php?id=49278 - SoapClient::__getLastResponseHeaders returns NULL if wsdl operation !has output _(12 votes)_
- **Bug**: Encoding - Investigate if null values can still be omitted in encoding
  - https://bugs.php.net/bug.php?id=62378 - PHP incorrectly encodes null values in SOAP _(11 votes)_
- **Bug**: Decoding - When attribute and node value is present, value is not decoded
  - https://bugs.php.net/bug.php?id=46616 - Value dropped when Soap response with nodes containing attributes and value _(10 votes)_
- **Bug**: Encoding - Investigate why xsi:type is not included for the reported case
  - https://bugs.php.net/bug.php?id=45027 - __soapCall returns an object with missing fields _(2 votes)_
- **Bug**: Streams - Look to support for multipart responses
  - https://bugs.php.net/bug.php?id=47810 - SoapClient and Multipart response _(44 votes)_
- **Bug**: Streams - Better handling of connection timeout
  - https://bugs.php.net/bug.php?id=48584 - soapclient's option connection_timeout not respected while fetching wsdl _(23 votes)_
- **Bug**: Streams - Problem with decompression using deflate
  - https://bugs.php.net/bug.php?id=47925 - PHPClient can't decompress response (transposed uncompress methods?) _(14 votes)_
- **Bug**: Streams - Look to a better re-using of connection
  - https://bugs.php.net/bug.php?id=47314 - SoapClient leave tcp connections in "time_wait" _(19 votes)_
- **Bug**: Streams - Support for digest auth
  - https://bugs.php.net/bug.php?id=47762 - SoapClient does not fetch WSDL requiring Digest auth _(13 votes)_
- **Bug**: Streams - Fix proxy support
  - https://bugs.php.net/bug.php?id=48244 - SoapClient doRequest fails when proxy is used _(3 votes)_
- **Bug**: Streams - Fix ingnoring http wrapper in calls _(1 vote)_
  - https://bugs.php.net/bug.php?id=44417 - call function ignore http wrapper
- **Bug**: Errors - Look to better handle SOAP fatal errors
  - https://bugs.php.net/bug.php?id=81239 - use_soap_error_handler doesn't do anything
- **Bug**: Client - Look to handling of ignored user agents
  - https://bugs.php.net/bug.php?id=48777 - Option to control SoapFault HTTP Status return (Reopen of #43507) _(9 votes)_
- **Bug**: Client - Fix ordering of parameter in assoc array
  - https://bugs.php.net/bug.php?id=49013 - SOAPClient interprets the parameters array incorrectly _(2 votes)_
- **Feat**: Client - helper for signed messages
  - https://github.com/php/php-src/pull/8035 - SoapClient feature: Helper function to signed SOAP messages



