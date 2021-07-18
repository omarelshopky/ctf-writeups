# Natas Level 10 --> Level 11

**Username:** natas11

**Password:** U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK 

**URL:**      http://natas11.natas.labs.overthewire.org

## Solution
* Open inspect, there is textbox take a code and button send us to a page contain source code lets see it
* In this page page it is obvious that what we will write in previous textbox will be inject in linux command "grep -i $code dictionary.txt" after filter {&|;}
* We can't use prvious code as they filtered some characters so think another way
* What if we grep from pass file and comment the rest
```bash
grep -i c /etc/natas_webpass/natas11 # dictionary.txt
```
* That's the password


## Natas12 Password
>  EDXp0pS26wLKHZy1rDBPUZk0RKfLGIR3

