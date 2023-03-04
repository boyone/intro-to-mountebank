# Create API Submit Order

## API Submit Order Spec

- port: `8000`
- request

  - method: `POST`
  - url: `/api/v1/order`
  - header: `Content-Types: application/json`
  - body:

    ```json
    {
      "cart": [
        {
          "product_id": 2,
          "quantity": 1
        }
      ],
      "shipping_method": "Kerry",
      "shipping_address": "405/37 ถ.มหิดล",
      "shipping_sub_district": "ท่าศาลา",
      "shipping_district": "เมือง",
      "shipping_province": "เชียงใหม่",
      "shipping_zip_code": "50000",
      "recipient_name": "ณัฐญา ชุติบุตร",
      "recipient_phone_number": "0970809292"
    }
    ```

- response

  - status code: `200`
  - header: `Content-Types: application/json`
  - body:

    ```json
    {
      "order_id": 8004359122,
      "total_price": 14.95
    }
    ```

## Example

Add api-submit-order stub to shopping-cart.json

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
    },
    {
        "predicates": [
          { "equals": { "method": "POST" } },
          { "equals": { "path": "/api/v1/order" } },
          {
            "equals": {
              "headers": {
                "Content-Type": "application/json"
              }
            }
          },
          {
            "jsonpath": { "selector": "$.cart[0].product_id" },
            "caseSensitive": true,
            "equals": { "body": "2" }
          }
        ],
        "responses": [
          {
            "is": {
              "statusCode": 200,
              "headers": { "Content-Type": "application/json" },
              "body": {
                "order_id": 8004359122,
                "total_price": 14.95
              }
            }
          }
        ]
    }
  ]
}
```
