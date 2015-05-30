---
---
# Getting information from Zendesk:

## Basic curl command

**Note:** If you use tokens like below, remember to add /token: between the username and the token.

```
λ curl https://somecompany1432285103.zendesk.com/api/v2/tickets.json  -v -u my.address@somecompany.com/token:890fewfxxhehehe788d8ebxRRnot000yet0smile
*   Trying 192.161.147.1...
...
* TLSv1.0, TLS handshake, CERT (11):
* TLSv1.0, TLS handshake, Server key exchange (12):
* TLSv1.0, TLS handshake, Server finished (14):
...
{"tickets":[{"url":"https:// ...
```

Personlly I often prefer redirecting the output to a file: 
```
λ curl https://somecompany1432285103.zendesk.com/api/v2/tickets.json  -v -u my.address@somecomapany.com/token:890fewfxxhehehe788d8ebxRRnot000yet0smile >> some_tickets.json
```


# JSON to CSV Conversion using jq

Using jq to transform the JSON output to plain CSV:
```
λ cat some_tickets.json |jq -r ".tickets[]|[.id,.subject,.status]|@csv"
1,"This is a sample ticket requested and submitted by you","pending"
2,"Test with multi-level ""drop down""","open"
3,"Report system doesn't work","open"
```


