# Imposter Structure

```json
{ // imposter
  "port": <port>,
  "protocol": "http",
  "stubs": [
    { // stub
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
