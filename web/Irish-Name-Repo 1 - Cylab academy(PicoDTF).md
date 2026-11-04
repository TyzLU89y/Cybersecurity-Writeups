# Irish-Name-Repo 1 

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Do you think you can log us in? Try to see if you can login!

## Solution

1. After accessing the website and navigating it around a little bit, we can find the admin login page on the top left of the page.
```
Username: admin
Password: admin
```
and that returned a failed login. 
2. The next thing I tried was a SQL Injection. I used the credentials:
```
Username: admin' --
Password: admin
```
and that logged in successfully and gave us the flag. 
## Flag

`academy{s0m3_SQL_271c9a2b}`

## Key Takeaway

SQL injection vulnerabilities rise when the program takes in user input directly to construct a SQL query without sanitizing. It is usually better to use prepared statements than taking input from users. 

## References

- [https://learn.cylabacademy.org/library/80]
