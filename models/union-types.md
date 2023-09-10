
- Union type with primitives
- Union type with arrays
- Union type with objects

```yaml

components:
  schemas:
    primitives:
      oneOf:
        - type: string
        - type: number

```