# Bulk withdrawal requests

----
**Note:** This URL require [authentication](../authentication.md).

----

You can create multiple withdrawal requests at the same time.
The procedure is very similar to the single request.
 You should use a slightly different endpoint and put several data sets to create queries in one array.


### URL for requests

```http request
Content-Type: application/json`
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjE...`
```

```http request
POST https://paydo.com/v1/withdrawals/create-mass
```

### Request example

```shell script
curl -X GET \
  https://paydo.com/v1/withdrawals/create-mass \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV...' \
  -d '[
        {
              "method": "1",
              "type": "1",
              "amount": "110",
              "currency": "EUR",
              "direction": "transfer to my client #544",
              "metadata": {"myInternalId": "54FB-HY"},
              ...
        },
        {
              "method": "2",
              "type": "1",
              "amount": "150",
              "currency": "USD",
              "direction": "transfer to my client #252",
              "metadata": {"myInternalId": "55FB-HY"},
              ...
        },
        {
              "method": "1",
              "type": "1",
              "amount": "250",
              "currency": "USD",
              "direction": "transfer to my client #1",
              "metadata": {"myInternalId": "32DE-NM"},
              ...
        }
  ]'
```
