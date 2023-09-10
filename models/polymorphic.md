# Polymorphic Responses

- Representing inheritance
- Inline schemas with a single allOf for the base type
- Array of anyOfs with one being the base type (why oneOf is likely wrong)


Simulating inheritance using allOf.
```yaml
components:
  schemas:
    cat:
        type: object
        allOf: 
            - $ref: "#/components/schemas/animal"
    animal:
        type: object
        properties:
          species:
            type: string
```

Any allOf constraint with a single $ref array member is considered a declaration of a base type.

1. Given a schema
2. If schema is a component type, name equals component name
    else type name is generated based on some context
3. If schema contains allOf and other "important properties???",
     2a. If allOf has one child schema that is a $ref, $ref points to base type
            else merge the allOfs into the current type
     2b. if schema contains oneOf. Throw up hands.
4. if schema contains oneOf or anyOf
      4a. create wrapper class called ???
      4b. Create properties that correstpond to child schemas
        - primitives use the type name 
        - objects use the paths and other context to construct "best possible names".


## Still to investigate:
Nested allOfs
allOf primitive types?
Should anyOf and oneOf be treated different for modelling

Kiota => anyOf with shared properties actually deserialize the property twice.

## Proposing new keywords

```yaml
components:
  schemas:
    foo:  
      allOfAsExtends: # inheritance
        - $ref: '#/components/schemas/base'
        - $ref: '#/components/schemas/Otherbase'
      allOf:   # spread
        - $ref: '#/components/schemas/creationInfo'
```


















Simulating using anyOf..
```yaml

paths: 
    /felines/{id}:
        responses:
            200:
              description: ok
              schema:
                title: feline
                anyOf:
                  - $ref: "#/components/animal"
                  - $ref: "#/components/cat"
                  - $ref: "#/components/tiger"                  
components:
  schemas:
    dog:
        type: object
    tiger:
        type: object
    cat:
        type: object
    animal:
        type: object
        properties:
          species:
            type: string
    
```
