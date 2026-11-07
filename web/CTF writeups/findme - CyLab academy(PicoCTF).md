# findme

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Help us test the form by submiting the username as `test` and password as `test!`

## Solution

1. Since we are given a login credential, I logged into the website with it. And the website redirected us to a page with a search box to search for flags. After some testing with the search box, I found that it was pretty useless. So we had to look elsewhere.

2. After opening the website in Burp Suite, we can see that after we logged in, we had 2 redirects. The process is roughly:

```
/login 
  --> /next-page/id=YWNhZGVteXtwcm94aWVzX2Fs
    --> /next-page/id=bF90aGVfd2F5XzY2MWZjMzk4fQ==
      --> /home
```
The 2 intermediate pages looks pretty interesting, their `id` field looks like it is a Base64 coded text. By concatenating the two strings together we get:
```
YWNhZGVteXtwcm94aWVzX2FsbF90aGVfd2F5XzY2MWZjMzk4fQ==
```
Which decodes to:
```
academy{proxies_all_the_way_661fc398}
```
And that is our flag. 
## Flag

`academy{proxies_all_the_way_661fc398}`

## Key Takeaway

Redirections are sometimes interesting, as they may reveal information that is not immediately visible in the browser.

## References

- [https://learn.cylabacademy.org/library/349]
