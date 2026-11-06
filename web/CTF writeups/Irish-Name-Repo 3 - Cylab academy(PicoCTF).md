# Irish-Name-Repo 3

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Try to see if you can login as admin!

## Solution

1. Same as the previous challenges of this series, we need to login as admin. We can see that the login screen has changed to just a password field. by trying the usual credentials like `admin`, and usual SQL injection payloads like `' or 1=1 --`, these were met with very little success. 

2. After looking at our request, we can see we also submitted a parameter called `debug`. By changing that parameter to 1, we can get our SQL query returned as well. If we tried to use `admin` we can see that it has turned to `nqzva` in the actual query. This suggests that the app has done a ROT13 encryption on our payload.

3. It has came to my attention that two ROT13 operations will not affect the payload. So we simmply had to upload the payload after 1 ROT13 operation. The final payload is:
```
' be 1=1 --
```
and we can get the flag. 

## Flag

`academy{3v3n_m0r3_SQL_7d1b96d3}`

## Key Takeaway

Using a simple encryption algorithm like ROT13 on the password is not a good practice as it can be decrypted and controlled easily. A better practice would to be using a hash algorithm. 

## References

- [https://learn.cylabacademy.org/library/8]
