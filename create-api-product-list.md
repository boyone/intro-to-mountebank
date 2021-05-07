# Create API Product List

## API Product List Spec

- port: `8000`
- request
  - method: `GET`
  - url: `/api/v1/product`
- response

  - status code: `200`
  - header: `Content-Types: application/json`
  - body:

    ```json
    {
      "total": 2,
      "products": [
        {
          "id": 1,
          "product_name": "Balance Training Bicycle",
          "product_price": 119.95,
          "product_image": "/Balance_Training_Bicycle.png"
        },
        {
          "id": 2,
          "product_name": "43 Piece dinner Set",
          "product_price": 12.95,
          "product_image": "/43_Piece_dinner_Set.png"
        }
      ]
    }
    ```

## Example

Create file call shopping-cart.json and paste the content below.

```json
{
  "port": 8000,
  "protocol": "http",
  "stubs": [
    {
      "predicates": [
        { "equals": { "method": "GET" } },
        { "equals": { "path": "/api/v1/product" } }
      ],
      "responses": [
        {
          "is": {
            "statusCode": 200,
            "headers": { "Content-Types": "application/json" },
            "body": {
              "total": 2,
              "products": [
                {
                  "id": 1,
                  "product_name": "Balance Training Bicycle",
                  "product_price": 119.95,
                  "product_image": "/Balance_Training_Bicycle.png"
                },
                {
                  "id": 2,
                  "product_name": "43 Piece dinner Set",
                  "product_price": 12.95,
                  "product_image": "/43_Piece_dinner_Set.png"
                }
              ]
            }
          }
        }
      ]
    }
  ]
}
```

## Start Mountebank with imposter file

```sh
mb start --configfile shopping-cart.json
```
