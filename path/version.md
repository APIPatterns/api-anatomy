# Version Path Segment

It is common for APIs to be designed with one of the left-most path segments being reserved for a version identifier. Numerous API design guidelines describe this as a best practice. It does make it easier for the API provider to introduce a significant amount of breaking changes, however the burden is transfered to the API consumer who must accomodate all the new changes in order to take advantage of any new change.

```yaml
openapi: 3.0.3
info:
  title: "Version path segment at the front"
  version: "1.0.0"
servers:
  - url: https://api.example.org/
paths: 
  /{version}/invoices:
    get:
      responses:
        200: 
          description: ok
  /{version}/customers:
    get:
      responses:
        200: 
          description: ok
```

If the version segment is the left most path segment and is used for all paths, it can be represented as a server variable.

```yaml
openapi: 3.0.3
info:
  title: "Version path segment at the front"
  version: "1.0.0"
servers:
  - url: https://api.example.org/{version}/
    variables:
      version:
        default: "1.0"
        enum:
          - "1.0"
          - "2.0"
paths: 
  /invoices:
    get:
      responses:
        200: 
          description: ok
  /customers:
    get:
      responses:
        200: 
          description: ok
```
