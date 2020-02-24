# List of payment methods available for withdrawal

----
**Note:** This URL require [authentication](../authentication.md).

----

### URL for requests

```http request
Content-Type: application/json`
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjE...`
```

```http request
POST https://paydo.com/v1/instrument-settings/payment-methods/available-withdrawal-for-user
```
    
### Request example

```shell script
curl -X GET \
    https://paydo.com/v1/instrument-settings/payment-methods/available-withdrawal-for-user \
    -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer eyJ0eXAiOiJKV...
```    

### Successful response example

```json
{
    "data": [
        {
            "identifier": 1000005,
            "type": 1,
            "name": "manual_bank_transfer",
            "title": "Bank Transfer",
            "currencies": [
                "EUR",
                "GBP",
                "USD"
            ]
        },
        {
            "identifier": 1000006,
            "type": 2,
            "name": "manual_international_card",
            "title": "Cards International",
            "currencies": [
                "EUR"
            ]
        }
    ],
    "status": 1
}
```
