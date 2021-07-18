# Natas Level 9 --> Level 10

**Username:** natas10

**Password:** nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu 

**URL:**      http://natas10.natas.labs.overthewire.org

## Solution
* Open inspect, there is textbox take a code and button send us to page contain source code lets see it
* In this page page it is obvious that what we will write in previous textbox will be inject in linux command "grep -i $code dictionary.txt"
* So we can inject command to get our target by write ";cat /etc/natas_webpass/natas10;" in textbox so the command will be as follow:
```bash
grep -i ;cat /etc/natas_webpass/natas10; dictionary.txt
```
* That's the password


## Natas11 Password
>  U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK

