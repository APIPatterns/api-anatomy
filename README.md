# API Anatomy

## Resource Design

A HTTP api is defined by a set of resources that a consumer interacts with to achieve some desired objective. Each resource is idenified by a URI. That's why it is called a Universal Resource Identifier. Most API designers these days use just the path portion of the URI to identify the domain concept of interest. The authority part, i.e. schema and host, are just used to identify where the service is deployed, and the query parameters are used to mainpulate the response in some way to change how the domain concept is presented.

### Path segments

| Kind | Description
|---|---|
|Category | Organizational segment used to group related resources together in the hierarchy. e.g. <code>https://example.org/<strong>accounting</strong>/invoices</code>|
|Data Partition | Segment used to partition different sets of similarly structured data. e.g. <code>https://example.org/<strong>acme</strong>/employees</code>|
|Version | Segment used to partition resource hierarchies due to breaking changes in resource structure or behavior. e.g. <code>https://example.org/<strong>v1</strong>/users</code>|
|Global key/value pair| A segment pair used to attach some value to resources in the sub hierarchy.  e.g. <code>https://example.org/<strong>subscription/XHJSD-JSDS-UERJE</strong>/resources</code> |
|Collections | A segment used to indicate a set of some domain concept. |
|Item | A segment used to indicate a specific instance of some domain concept within a set. |
|Relationship| A segment used to indicate a relationship between one domain concept and another. |
|Multi-segment | A set of segments used to allow API consumers to define a hierarchy for a set of domain concepts. |
|Matrix| A rarely used capability to insert a multi-dimensional table of domain concepts into a hierarchy. |
|View| A path segment used to explicitly indicate an alternate resource for the same domain concept. |
|Action| A segment used to perform an unsafe operation on either a related resource or some kind of data processing on the transfered information. |
|Function| A segment used create results that are usually an aggregation of domain concepts or some derivative of a domain concept. |

#### Behavior
    - does the order imply hierarchy. Some types require a location in the URLs

### Query parameters

Query parameters are used to create variants of the resource identified by the path. Each of these variants is technically a resource on its own as it has a distinct URL. However, generally variants created by query parameters will share many of the same characteristics of the resource identified by just the path.  

#### Kinds

| Kind | Description
|---|---|
| Projection| Creates a resource that contains a subset of the properties contained in the path only resource.|
| Filtering| Creates a resource that contains a subset of the members of the path only resource. |
| Sorting||
| Limits||
| Paging||
| Transclusion||
| Sparse identifiers||
| Behavior modifiers||
| Representation format||

#### Types
    - strings
    - arrays of strings
    - expressions
    - json
    - dynamic form data
    - dates 
    - Constrained types

#### Behavior
    - Dependent parameters
    - Parameter ordering
    - Parameter name casing
    - Encoding

## Application protocol ???

| Feature | Description
|---|---|
| Tunneled requests | |
| Batches | |
| Long running | |
| NoContent or Content | |
| Prefer header | |
| Accept | |
| Idempotency | |
| Redirects | |
| Authenticated Interactions | |
| Paid interactions | |
| Throttling | |
| Partial failure | |
| Redirects | |
| Cachable content | |
| Detecting changes in data | |

## Representation Design

| Feature | Description
|---|---|
| Media types | |
| Multi format responses | |
| Batch | |
| Polymorphic responses | |
| Null vs absence | |
| Deprecation | |
| Collections vs items | |
| Facets | |
| Annotations | |
| Links | |

## Other

- Security
- Privacy
- Workflow (sequences of requests)
- Errors