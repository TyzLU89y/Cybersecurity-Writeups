# Forbidden Paths

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Can you get the flag?

We know that the website files live in `/var/www/html/` and the flag is at `/flag.txt` but the website is filtering absolute file paths. Can you get past the filter to read the flag?

## Solution

1. After accessed the website, we can see a box for us to enter the filename and the app will read the contents of the file.  I first tried one of the files listed on the webpage and it worked as expected. Then I tried `flag.txt` which returned as file does not exist.

2. To begin exploiting, I tried the absolute file path for the flag `/flag.txt` and which returned not authorized. Not suprised since the description already said absolute file paths will be filtered. Then I tried `/` but it returns not authorized instead of file does not exist. So this tells us that the filter might be related to the  `/` character.

3. Since the filter is working on absolute file paths, one potential vulnerability is that the app only filters strings starting with `/`, So I tried `../` and returned file does not exist. So relative file paths are still effective.

4. From the description we can know that the files are read from the  `/var/www/html/` directory. So we need to return to the root directory and read the `flag.txt` there. The `..` operator in UNIX-like systems can return to the upper directory. So our final payload is:
```
../../../flag.txt
```
and using this payload can give us the flag. 

## Flag

`academy{7h3_p47h_70_5ucc355_afd5d939}`

## Key Takeaway

Filter entries with a blacklist is very likely tobe bypassed, in production it will be better to use a whitelist instead. 

## References

- [https://learn.cylabacademy.org/library/270]
