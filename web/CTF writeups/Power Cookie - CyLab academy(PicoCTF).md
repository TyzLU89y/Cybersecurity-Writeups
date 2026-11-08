# Power Cookie

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Can you get the flag?

## Solution

1. After accessing the website, we can see a button that told us to continue as guest. After we clicked the button, the app told us that there are guest services at the moment. So this might suggest that we don't have enough access.

2. Since the name of the challenge mentioned `Cookie`, it could be a good idea to look at our browser cookie. And we can see an entry with name `isAdmin` wnd value `0`. After changing the value to `1` and refreshing the page, we were able to get our flag. 
## Flag

`academy{gr4d3_A_c00k13_7bcbf214}`

## Key Takeaway

It is unsecure to store the authenticating data on the client side as it can be potentially be modified. A safer way to do this would be to let the server authenticating the identity of the user.

## References

- [https://learn.cylabacademy.org/library/288]
