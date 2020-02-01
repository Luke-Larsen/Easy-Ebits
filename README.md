# Easy PHP Ebits
A simple way to communicate with the Ebits daemon

## Instilation
- Simply add the easyEbits.php to your project folder
- Then on your php file do the code
 ``` require('easyEbits.php'); ```

## Development
Initialize ebits connection/object
```
$Ebits = new Ebits('username','password');
```

Optionally, you can specify a host and port.
```
$Ebits = new Ebits('username','password','host','port');
```
If you wish to make an SSL connection you can set an optional CA certificate or leave blank This will set the protocol to HTTPS and some CURL flags
```
$Ebits->setSSL('/full/path/to/mycertificate.cert');
```
Make calls to Ebitsd as methods for your object. Responses are returned as an array. Here are a few examples
```
$Ebits->getblockcount();
$Ebits->getblockchaininfo();
$Ebits->getblock('000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f');
```
> A list of commands can be found in the commands.txt in this github

The full response (while not usually needed) is stored in $this->response

When a call fails for any reason, it will return FALSE and put the error message in $this->error
```
echo $Ebits->error;
```
The HTTP status code can be found in $this->status and will either be a valid HTTP status code or will be 0 if cURL was unable to connect.
```
echo $Ebits->status;
```
