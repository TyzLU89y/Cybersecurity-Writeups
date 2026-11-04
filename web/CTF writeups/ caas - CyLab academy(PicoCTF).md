# caas

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Now presenting cowsay as a service
Download index.js:
index.js

## Solution

1. After accessing the service, it tells us that:
```
Make a request to the following URL to cowsay your message:
https://caas.mars.cylabacademy.net/cowsay/{message}
```
and after trying some strings in the `message` field and got nothing but a cow speaking the exact same sentence. It's better to start looking at other informations.

2. After reading `index.js`, we can see that what ever is in the `message` field is executed as a command. The `|` operator is a shell pipe operator that can pipe the outputs of the first command to the second command. And the backend of this app could interpret this character as a shell operator. So we could try adding a new command after the cowsay command like:
```
https://caas.mars.cylabacademy.net/cowsay/a | ls
```
and that worked like a normal `ls` command returning a list of files. The file that seemed most interesting was `falg.txt`. So we can try reading the contents of that file with:
```
https://caas.mars.cylabacademy.net/cowsay/a | cat falg.txt
```
and that returned our flag. 

## Flag

`picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}`

## Key Takeaway

When accepting user input as a part of a command, it is dangerous to just take in the input without doing any sanitation. Which could possibly lead to a OS Command Injection vulnerability.

## References

- [https://learn.cylabacademy.org/library/202]
