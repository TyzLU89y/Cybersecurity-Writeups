# Roboto Sans

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

The flag is somewhere on this web application not necessarily on the website. Find it.

## Solution

1. After accessing the website, since the description hinted us that the flag is not necessarily on the website, and the title of this challenge kinda resonates with robot. So I decided to try checking the `robots.txt` file. And it has returned:
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```
2. It has came to my attention that there are some strings that appears to be coded to Base64. Which are:
```
ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
```
After turing it back to text we get:
```
flag1.txtjs/myfi
js/myfile.txt
(Last line doesn't really decode to any valid text)
```
And now we have three files `flag1.txt`, `js/myfi` and `js/myfile.txt`.

3. After adding the file names to the url, we can find the flag at the file `js/myfile.txt`.
## Flag

`academy{Who_D03sN7_L1k5_90B0T5_f7d32834}`

## Key Takeaway
The `robots.txt` file in a web app gives crawling instructions to crawlers, indicating which paths they should avoid accessing. But it doesn't actually prevent you accessing the paths, and sometimes it can contain important information.
This challenge is quite trivial, so I guess the key takeaway here is to read the title and description carefully as it can sometimes give you really useful information.

## References

- [https://learn.cylabacademy.org/library/291]
