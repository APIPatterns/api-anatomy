# Category Path Segment

For large APIs with many resources it is often useful to group related resources under a category path segment.  Generally this kind of path segment would appear early in the URL.  

```yaml
openapi: 3.0.3
info:
  title: "Accounting path segment used to group related resources"
  version: "1.0.0"
servers:
  - url: https://api.example.org/
paths: 
  /accounting/invoices:
    get:
      responses:
        200: 
          description: ok
  /accounting/generalLedger:
    get:
      responses:
        200: 
          description: ok
  /accounting/accounts:
    get:
      responses:
        200: 
          description: ok
```

A category segment can be used as an alternative to creating separate APIs for each of the categories.