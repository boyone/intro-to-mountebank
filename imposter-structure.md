# Imposter Structure

```json
{
  "port": <port>,
  "protocol": "http",
  "stubs": [
    {
      "predicates": [
        { "equals": { "method": <method> } },
        { "equals": { "path": <path> } },
      ],
      "responses": [
        {
          "is": {
            "statusCode": <statusCode>,
            "headers": {},
            "body": {}
          }
        }
      ]
    }
  ]
}
```
