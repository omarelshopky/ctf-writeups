# Natas Level 12 --> Level 13

**Username:** natas13

**URL:**      http://natas13.natas.labs.overthewire.org

## Solution
* Open inspect, there is textbox take a background color code and button send us to a page contain source code
* Open source code it generate random path with extention taken from requests (default "v3id13wvte.jpg") to uploaded file, then put it in upload folder 
* Write php script echo the password from pass folder
```php
<?php
  echo shell_exec("cat /etc/natas_webpass/natas13");
?>
```
* Upload the script then intercept requests with burp to change filename ext to php to execute script onclick
* You got the password!!

## Password
> jmLTY0qiPZBbaKc9341cqPQZBJv7MQbY  
