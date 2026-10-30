# 3v@l

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

ABC Bank's website has a loan calculator to help its clients calculate the amount they pay if they take a loan from the bank. Unfortunately, they are using an eval function to calculate the loan. Bypassing this will give you Remote Code Execution (RCE). Can you exploit the bank's calculator and read the flag?

## Solution

1. From the challenge description and the name, we can know that the vulnerability here is going to be RCE through the `eval()` function. After connectong to the website and reading the source for the website, we can know that there are regex and blacklisted words that will prevent us from exploiting the `eval()` function. So we need to find ways to bypass that.
   
2. We can know from the comments that the word `os` was banned, so we needed to find other ways to execute external commands. Luckily, the module `subprocess` can be used to do exactly that and it isn't in the list of banned words.

To execute a command, we needed to use the `subprocess.check_output()` function. Unfortunately, the `.` character is also banned. So we will have to bypass that with the function `getattr()`.

Lastly, for our command payload, we can know the flag file is named `/flag.txt` and we need to use the command `cat` to display its content. But `cat` is also in the blacklist of words. So we will have to concatenate a series of `chr()` functions to assemble our command. 

3. Finally, we put all of the above together to get our full payload:
```
getattr(__import__('subprocess'), 'check_output')([chr(99)+chr(97)+chr(116), chr(47)+chr(102)+chr(108)+chr(97)+chr(103)+chr(46)+chr(116)+chr(120)+chr(116)])
```
and the flag is being returned to us. 

## Flag

`academy{D0nt_Use_Unsecure_f@nctionsa1bfa17b}`

## Key Takeaway

The `eval()` function is extremely dangerous and it is very vulnerable to RCE attacks. Best to never use it in production, no matter how careful you are with it. 

## References

- [https://learn.cylabacademy.org/library/484]
