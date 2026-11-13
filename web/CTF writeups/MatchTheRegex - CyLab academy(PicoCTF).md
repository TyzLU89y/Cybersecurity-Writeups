# MatchTheRegex

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

How about trying to match a regular expression

## Solution

1. After accessing the website, we can see a text box prompted to let us enter text. After trying some usual tries, we were met with limited success. So we will have to find other ways.

2. After inspecting the source code, we can see that the the app was searching up a regex in a page called `/flag`. So we better find something that would appear in the flag.

3. After some trying, we can find the regex is `academy`, and submitting this will get us the flag. 

## Flag

`academy{succ3ssfully_matchtheregex_4d5352dc}`

## Key Takeaway

Regular expressions can be used to search for strings matching a particular pattern. Understanding what pattern an application expects can help identify valid inputs.

## References

- [https://learn.cylabacademy.org/library/356]
