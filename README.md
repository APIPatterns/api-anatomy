# API Anatomy

This repository is an attempt at defining a set of application level terminology for HTTP API design.  Along with each term is a description and an OpenAPI description of an example API demonstrating its use.  

The intent of this collection is not to suggest best practices but to be a set of scenario examples that tooling developers can use to verify that they provide broad support for API designers.

## Resource Design

A HTTP api is defined by a set of resources that a consumer interacts with to achieve some desired objective. Each resource is idenified by a URI. That's why it is called a Universal Resource Identifier. Most API designers these days use just the path portion of the URI to identify the domain concept of interest. The authority part, i.e. schema and host, are just used to identify where the service is deployed, and the query parameters are used to mainpulate the response in some way to change how the domain concept is presented.

### Path segments

| Kind | Description
|---|---|
|[Category](./path/category.md) | Organizational segment used to group related resources together in the hierarchy. e.g. <code>https://example.org/accounting/invoices</code>|
|[Data Partition](./path/data-partition.md) | Segment used to partition different sets of similarly structured data. e.g. <code>https://example.org/acme/employees</code>|
|[Version](./path/version.md) | Segment used to partition resource hierarchies due to breaking changes in resource structure or behavior. e.g. <code>https://example.org/v1/users</code>|
|[Key/value pair](./path/key-value-pair.md)| A segment pair used to attach some value to resources in the sub hierarchy.  e.g. <code>https://example.org/subscription/XHJSD-JSDS-UERJE/resources</code> |
|[Collection](./path/collection.md) | A segment used to indicate a set of some domain concept. e.g. <code>https://example.org/movies</code> |
|[Item](./path/item.md) | A segment used to indicate a specific instance of some domain concept within a set. e.g. <code>https://example.org/movies/some-movie-id</code>|
|[Relationship](./path/relationship.md)| A segment used to indicate a relationship between one domain concept and another. e.g. <code>https://example.org/movies/some-movie-id/actors</code>|
|[Multi-segment](./path/multi-segment.md) | A set of segments used to allow API consumers to define a hierarchy for a set of domain concepts. e.g. <code>https://example.org/bookmarks/personal/cooking/testkitchen</code> |
|[Matrix](./path/matrix.md)| A rarely used capability to insert a multi-dimensional table of domain concepts into a hierarchy. e.g. <code>https://example.org/countries;continent=asia/cities</code> |
|[View](./path/view.md)| A path segment used to explicitly indicate an alternate resource for the same domain concept. e.g. <code>https://example.org/recipies/eggnog;printable</code> |
|[Action](./path/action.md)| A segment used to perform an unsafe operation on either a related resource or some kind of data processing on the transfered information. <code>https://example.org/me/invites/accept</code>|
|[Function](./path/function.md)| A segment used create results that are usually an aggregation of domain concepts or some derivative of a domain concept. <code>https://example.org/me/documents/recentlyUsed</code>|

#### Behavior

The set of path segments defines a hierarchy. Path segments provide context to the following segments. This can have a significant impact for some types of path segment. A version segment at the far left of a path, has a very different impact than one at the far right of the path.
The hierarchial nature of a path is the major differentiator between path segments and query parameters.  

### Query parameters

Query parameters are used to create variants of the resource identified by the path. Each of these variants is technically a resource on its own as it has a distinct URL. However, generally, variants created by query parameters will share many of the same characteristics of the resource identified by just the path.  

#### Kinds

| Kind | Description
|---|---|
| Projection| Identifies a resource that contains a subset of the information contained in the path-only resource. Consider this a vertical slice of the path-only resource. https://example.org/books?select=Title,Author |
| Filtering| Identifies a resource that contains a subset of the items from of the path-only resource. Consider this a horizontal slide of the path-only resource. e.g. http://example.org/books?author=Smith|
| Sorting|Identifies a resource that contains a set of items from the path-only resource in some specified order. e.g. <code>https://example.org/tasks?orderBy=Deadline</code> |
| Range | Identifies a resource that contains a subset of items from the path-only resource based on a ordinal constraints. e.g. <code>https://example.org/tasks?top=10&skip=50</code> |
| Transclusion| Enables a caller to include a representation of a related resource into the representation of the path-only resource. e.g. <code>https://example.org/users/22?$expand=manager</code>|
| Sparse identifiers| Identifies a resource using n property values within a n-space. e.g. <code>https://example.org/map/image?lat=100&long=50</code> |
| Behavior modifiers| Identifies a resource that is a variant of the path-only resource in some domain specific way. e.g. <code>https://example.org/me/calendar?view=week</code> |
| Representation format|Identifies a resource that is a variant of the path-only resource in the format of the reprentation. e.g. <code>https://example.org/me/tasks?format=CSV</code>|

#### Parameter Types

URLs are serialized as strings when being used by HTTP. However, the values used for parameters in the URL often have additional semantics and are do not have standardized string serializations.

| Type | Serialization Notes |
|---|---|
| strings | Percent encoding. (Reserved, gen-delims, semi-delims), quoted or not, single or double  |
| arrays of strings | comma delim |
| expressions |  |
| json | |
| dynamic form data |  |
| dates | ISO, unix |
| numbers |  |
| Constrained types | enums? |

#### Behavior

| Type | Serialization Notes |
|---|---|
| Dependent parameters | |
| Parameter ordering | |
| Parameter name casing | |
| Encoding issues | |

## Requests

| Feature | Description
|---|---|
| Tunneled requests | |
| Batches | |
| Prefer header | |
| Accept | |
| Idempotency | |
| Authenticated Interactions | |
| Paid interactions | |
| Detecting changes in data | |

## Responses

| Feature | Description
|---|---|
| Redirects | |
| Throttling | |
| Long running | |
| NoContent or Content | Some HTTP interactions return a representation of the resource that is being interacted with, others do not. Whether content is returned or not is generally based on a combination of the method and the status code. |
| Partial failure | |
| Redirects | |
| Cachable content | |
| Deleted | |

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