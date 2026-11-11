# Mod 26

- **Platform:** CyLab academy(PicoCTF)
- **Category:** cryptography 
- **Difficulty:** easy

## Challenge

Cryptography can be easy, do you know what ROT13 is? values.txt

## Solution

1. After downloading the file, we can see a string of letters:
```
npnqrzl{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_5p5s5o36}
```
And according to the description, I thought trying ROT13 might be a good idea. By applying ROT13 to this string again, we can get the flag.
## Flag

`academy{next_time_I'll_try_2_rounds_of_rot13_5c5f5b36}`

## Key Takeaway

As one of the simplest cryptography algorithms, the decryption of an encrypted ROT13 string is simply applying ROT13 again. As the principle of ROT13 is just rotating each character in the string by 13 characters, that is, the string 'a' would be encrypted to 'n' and 'n' will be encrypted to 'a' again. 

## References

- [https://learn.cylabacademy.org/library/144]
