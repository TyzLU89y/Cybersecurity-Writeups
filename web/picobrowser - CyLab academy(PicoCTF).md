# picobrowser

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

This website can be rendered only by picobrowser, go and catch the flag!

## Solution

1. After accessing the website, we can see a button with text `flag`. After clicking the button, we were prompted that it can only be accessed through a browser called `picobrowser` and it displays the `user-agent` field in our request.

2. By adding `picobrowser` to our `user-agent` field and then resend the modified request. We will be able to obtain the flag in our response. 

## Flag

`academy{p1c0_s3cr3t_ag3nt_33592427}`

## Key Takeaway

The `user-agent` request header in a http request identifies the client software making the request.

## References

- [https://learn.cylabacademy.org/library/9]
