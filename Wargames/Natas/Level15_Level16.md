# Natas Level 15 --> Level 16

**Username:** natas16

**Password:** WaIHEacj63wnNIBROHeqi3p9t0m5nhmh

**URL:**      http://natas16.natas.labs.overthewire.org

 
## Solution
* Click view sourcecode there you can see the query they use to access, there isn't anything special so we can inject simple code to bypass.
```
$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
```

* You got the password!!

> WaIHEacj63wnNIBROHeqi3p9t0m5nhmh
