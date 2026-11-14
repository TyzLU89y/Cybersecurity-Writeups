# No Sql Injection

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Can you try to get access to this website to get the flag?

You can download the source here

## Solution

1. After accessing the website, we can see a login page. After trying some usual credentials and sql injection methods, we were met with little success. So we have to find other ways.

2. After checking the app source, we can see that it didn't use a sql query, instead, it used a Nosql query. So I searched up [Nosql Injections](https://brightsec.com/blog/nosql-injection-explained-what-it-is-and-how-to-prevent-it/) and found some payloads that are worth trying.

3. After opening the webpage in Burp Suite, we can send the request in the rigged web broser that it provided. After sending the payload as:
```
Username: {"$ne": null}
Password: {"$ne": null}
```
We were able to login. 

4. After we logged in, we are shown a admin page. After some looking around, we found very little useful information. So we had to look elsewhere. After some more browsing, I found a interesting string in the login response:
```
YWNhZGVteXtqQmhEMnk3WG9OelB2XzFZeFM5RXc1cUwwdUk2cGFzcWxfaW5qZWN0aW9uXzIyOTAyMmZmfQ==
```
This looked like a Base64 string, 


## Flag

`academy{jBhD2y7XoNzPv_1YxS9Ew5qL0uI6pasql_injection_229022ff}`

## Key Takeaway

The `user-agent` request header in a http request identifies the client software making the request.

## References

- [https://learn.cylabacademy.org/library/9]
