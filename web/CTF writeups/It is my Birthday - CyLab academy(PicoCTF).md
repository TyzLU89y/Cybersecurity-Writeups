# It is my Birthday

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

I sent out 2 invitations to all of my friends for my birthday! I'll know if they get stolen because the two invites look similar, and they even have the same md5 hash, but they are slightly different! You wouldn't believe how long it took me to find a collision. Anyway, see if you're invited by submitting 2 PDFs to my website.

## Solution

1. After accessing the website, we are asked to upload 2 files. So first I tried to upload 2 of the same file. And it returned `The files are not different`, so we had to find other ways.

2. After some searching, it has come to my attention that md5 has been proven to be not collision proof since 2005. So I found some example files of md5 collision to upload. And uploading that gave us a response containing the app's source code. And we can find the flag in a line of comment. 

## Flag

`academy{c0ngr4ts_u_r_1nv1t3d_44f9d0a}
`

## Key Takeaway

MD5 is no longer considered secure against collision attacks. A collision occurs when two different inputs produce the same hash value. Using MD5 to verify file integrity or distinguish files in security-sensitive applications can therefore be unsafe. SHA-256 is a more secure alternative because it currently provides strong collision resistance.

## References

- [https://learn.cylabacademy.org/library/109]
- [https://www.mscs.dal.ca/~selinger/md5collision/]
