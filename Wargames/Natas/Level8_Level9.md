# Natas Level 8 --> Level 9

**Username:** natas9

**URL:**      http://natas9.natas.labs.overthewire.org

## Solution
* Open inspect, there is textbox take a code and button send as to page contain source code lets see it
* In this page page it is obvious that what we will write in previous textbox will be encoded then compare to code stored in "encodedSecret"
* We must decode this pass to know what we should write, he encode ours in this steps:
  1. base64
  2. reverse the string
  3. convert from binary to hexa
* So we must do it in reverse lets convert it from hexa to binary (PHP)
```
<?php
echo hex2bin("3d3d516343746d4d6d6c315669563362");
?>
```
* Reverse the String (Python)
```
code = " ==QcCtmMml1ViV3b"[::-1]
print(code)
```
* Decode base64 (Linux command)
```
echo b3ViV1lmMmtCcQ==  | base64 -d
```
* Submit it the password will appear

## Password
> W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl  

