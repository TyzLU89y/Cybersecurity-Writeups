# SQLiLite

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Can you login to this website?

## Solution

1. First off, I tried to login with common credentials like
 ```
Username: admin
Password: admin
```
and that returned as failed login. 

2. It came to my attention that the login process is done with a plaintext SQL query, and the failed query was shown to me: `SQL query: SELECT * FROM users WHERE name='admin' AND password='admin'`
so next step for me was to construct a SQL injection attack. 

3. By observing the structure of the query, we can know that the main payload should be at the name section, so I tried the following payload. 

```text
username: admin' or 1=1--
password: admin
```
and logged in successfully. 

But now the webpage didn't show the flag directly, but it hinted us that the flag is in plainsight. So I tried to inspect the source code of this webpage and found out the flag in hidden text.

## Flag

`academy{L00k5_l1k3_y0u_solv3d_it_d69457c6}`

## Key Takeaway

SQL injections are one of the most common and powerful vulnerabilities, it is always worth a shot when things are unclear and don't know where to start

## References

- [https://learn.cylabacademy.org/library/304]
