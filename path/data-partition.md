# Data Partition Path Segment

For SAAS APIs, there is often a unique set of data for each API consumer customer.  A data partition path segment can be used to distinguish between data the different sets of data.  Using the path to make this distinction in case there is future need to reference data from multiple datasets in a single application.

```yaml
openapi: 3.0.0
info:
  title: "Accounting path segment used to group related resources"
  version: "1.0.0"
paths: 
  /{datapartition}/invoices:
    parameters:
      - $ref: "#/components/parameters/datapartition"
    get:
      responses:
        200: 
          description: ok
  /{datapartition}/generalLedger:
    parameters:
      - $ref: "#/components/parameters/datapartition"
    get:
      responses:
        200: 
          description: ok
  /{datapartition}/accounts:
    parameters:
      - $ref: "#/components/parameters/datapartition"
    get:
      responses:
        200: 
          description: ok
components:
  parameters:
    datapartition:
      name: datapartition
      in: path
      required: true
      schema:
        type: string

```