# Secrets

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

We have several pages hidden. Can you find the one with the flag?

## Solution
1. After accessing the website, we can see a webpage that displays some information. After some exploring around the page, we weren't able to get useful information from the webpage it self. So we needed to find some other way. 

2.After inspecting the sources of the page, we can find a file under the directory of `secret/assets/`, after trying some possible urls, we were able to visit the root directory of `/secret/`.

3. Further inspection of the page, we can find another directory called `/hidden/`. It is reasonable to assume our previous approach was correct, so after accessing the page `/secret/hidden/` and inspecting page, we can find yet another direcory called `/superhhidden`. Repeating our process before, we can finally find the flag at the source of `/secret/hidden/superhidden/`
4. The structure of the directory is like this: 
<img width="402" height="457" alt="image" src="https://github.com/user-attachments/assets/9c83a9c3-2714-4d4f-9a60-4c7aee664f2a" />


## Flag

`academy{succ3ss_@h3n1c@10n_e77e3359}`

## Key Takeaway

Just hiding the secrets under multiple directories without controlling user access is not safe, the app should always set checks for identity before letting access to certain directories. 

## References

- [https://learn.cylabacademy.org/library/296]
