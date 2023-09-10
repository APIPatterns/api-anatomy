# HTTP Methods

API consumers interact with resources in an API using [HTTP Methods](https://www.iana.org/assignments/http-methods/http-methods.xhtml). There is a limited set of supported HTTP methods that can be reused across many resources.  Not every resource supports every method. 



```mermaid
graph LR
GET --> g200[200] --> Get
GET --> g200[200] --> Function
GET --> g204[204] --> Ping
GET --> g202[202] --> Report
POST --> po201[201] --> Create
POST --> po200[200] --> Action
POST --> po204[204] --> FireAndForget
POST --> po202[202] --> Job
PUT --> pu200[200] --> Replace
PUT --> pu204[204] --> ReplaceNoResponse
PUT --> pu200-201[200,201] --> ReplaceOrCreate
PATCH --> pa200-201[200,201] --> UpdateOrCreate
PATCH --> pa200-201-204[200,201,204] --> UpdateOrCreateNoResponse


```