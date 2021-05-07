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
      // api product list
    },
    {
      "predicates": [
        { "equals": { "method": "POST" } },
        { "equals": { "path": "/api/v1/order" } },
        {
          "equals": {
            "headers": {
              "Content-Types": "application/json"
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
            "headers": { "Content-Types": "application/json" },
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
