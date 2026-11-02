# SOAP

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

## Solution

1. After accessing the website, we can see three buttons with `Details` written on them. Clicking these buttons will add a line of text to the website.

2. By adding the website as a target in Burp Suite, we can see every time we clicked `Detail` it sends a request with `Content-Type: application/xml`. This might suggest an [XML external entity (XXE) injection](https://portswigger.net/web-security/xxe#what-is-xml-external-entity-injection) vulnerability.

3. Next is to use the repeater in Burp Suite to perform an XML Injection Attack. We can see the content of our initial request was:
```
<?xml version="1.0" encoding="UTF-8"?><data><ID>1</ID></data>
```
we need to define a new XML entity and it's contents are the contents of `/etc/passwd` and use the entity in the `ID` value. So our final payload will be:
```
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]><data><ID>&xxe;</ID></data>
```
Where `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>` defines our entity `xxe`s. `&xxe;` references our entity to let the server retrieve its contents and that contains our flag.
## Flag

`academy{XML_3xtern@l_3nt1t1ty_6249c1d4}`

## Key Takeaway

XXE vulnerabilities rise when the app use XML formats to transmit data and since the XML specification contains potential dangerous features. Standard parsers may support these features by default. So it is important to disable these features.

## References

- [https://learn.cylabacademy.org/library/376]
