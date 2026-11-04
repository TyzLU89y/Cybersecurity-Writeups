# login

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

My dog-sitter's brother made this website but I can't get in; can you help?

login.mars.cylabacademy.net

## Solution

1. After accessing the website, we were greeted with a login screen. So I tried with a random login credential like:
```
Username: admin
Password: admin
```
and the website returned with `Incorrect Password`.

2. After reading `.../index.js`, we can see that comparisons of username and password were done on the output of a function called `btoa()`.
After reading the javascript documents, we can know that the function returns a base64-encoded ASCII string.  
3. by decoding the two strings:
```
"YWRtaW4"
"cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ"
```
we can get the result:
```
admin
picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}
```
and these are the correct credentials for logging in. And the password is also the flag.


## Flag

`picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}`

## Key Takeaway

When checking credentials for logging in, it is crutial to not use any reversable and monotonic functions to perform the check. 

## References

- [https://learn.cylabacademy.org/library/200]
