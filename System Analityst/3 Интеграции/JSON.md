

## Простой JSON Schema

Сразу к практике. Допустим, нужно описать JSON для пользователя. В JSON будут имя, возраст и email. Начнем с простого:

```
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "name": {
      "type": "string"
    },
    "age": {
      "type": "integer",
      "minimum": 18
    },
    "email": {
      "type": "string",
      "format": "email"
    }
  },
  "required": ["name", "age", "email"]
}
```
