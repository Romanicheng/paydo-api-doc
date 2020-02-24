# Merchants withdrawals transactions


### URL for requests

```http request
Content-Type: application/json`
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjE...`
```

```http request
POST https://paydo.com/v1/withdrawals/user-withdrawals
```

### Request example

```shell script
curl -X GET \
  https://paydo.com/v1/withdrawals/user-withdrawals \
    -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV...
```


### Successful response example

```json
{
    "data": [
        {
            "identifier": "d2bdfd96-e070-44e3-9c7b-775b25a6f1d1",
            "groupIdentifier": null,
            "userIdentifier": "28",
            "type": 1,
            "currency": "USD",
            "amount": "11.0000",
            "transactionIdentifier": "36a48ac0-ff73-4681-9f25-7abf803d2e7f",
            "status": 1,
            "method": 1,
            "direction": "why not?",
            "metadata": {
                "myInternalId": "55FB-HY"
            },
            "createdAt": 1582545960,
            "updatedAt": null,
            "beneficiary": {
                "account": "GB80HBUK44830812341234",
                "name": "John Galt",
                "country": "GB",
                "city": "BIRMINGHAM",
                "address": "1 CENTENARY SQUARE",
                "registrationNumber": ""
            },
            "beneficiaryBank": {
                "name": "HSBC UK BANK PLC",
                "bic": "HBUKGB4B",
                "country": "GB",
                "city": "London",
                "address": "London DSC 62-76 Park St Southwark"
            },
            "routingNumber": null,
            "afsk": null
        }
    ],
    "status": 1
}
```
