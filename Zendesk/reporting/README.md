# Getting information from Zendesk:

## Basic curl command
curl https://somecompany1432285103.zendesk.com/api/v2/tickets.json  -v -u my.address@somecomapany.com/token:890fewfxxhehehe788d8ebxRRnot000yet0smile

# JSON to CSV Conversion using jq

Using jq to transform the JSON output to plain CSV:
```
λ cat some_tickets.json |jq -r ".tickets[]|[.id,.subject,.status]|@csv"
1,"This is a sample ticket requested and submitted by you","pending"
2,"Test with multi-level ""drop down""","open"
3,"Report system doesn't work","open"
```


