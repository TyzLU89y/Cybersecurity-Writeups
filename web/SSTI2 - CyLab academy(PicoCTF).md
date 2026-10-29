# SSTI2

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :)

## Solution

1. After SSTI1, we could presume that SSTI2 is also about Server Side Template Injection, so at first I tried to use `{{7*7}}` which announced

  ```text
  49
  ```
  so this suggests a possible vulnerability. 

2.  By trying `{{7*'7'}}` and the website anounced
  ```text
  777777
  ```
<img width="680" height="410" alt="image" src="https://github.com/user-attachments/assets/cb7e9e62-9263-48f7-9079-2a446c83f2a3" />

  this meant that this website is possibly built with Jinja2 or Twig, which are both python liberaries. 

3. By trying a number of combanations, we can identify that `.` and `_` were in the blacklist of characters. So we need to bypass these.
For `_`, As a matter of fact, python automatically interpret bytestrings to text. So we can use the bytestring for `_` to replace it in our payload, which is `\x5f`




## Flag

`academy{L00k5_l1k3_y0u_solv3d_it_d69457c6}`

## Key Takeaway

SQL injections are one of the most common and powerful vulnerabilities, it is always worth a shot when things are unclear and don't know where to start

## References

- [https://learn.cylabacademy.org/library/304]
