# Withdrawal

1. [Create withdrawal](#create-withdrawal)
    * [Request example](#request-example)
    * [Withdrawal methods](#withdrawal-methods)
1. [Create withdrawal bulk](./bulk.md)
1. [Withdrawal payment methods](./paymentMethods.md)
1. [Withdrawal transactions list](./getWithdrawals.md)

----
**Note:** This URL require [authentication](../authentication.md).

----

## Create withdrawal

### URL for requests

```http request
Content-Type: application/json`
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjE...`
```

```http request
POST https://paydo.com/v1/withdrawals/create
```

**Parameters**

Parameter                           |        Type      |                 Description                                                                              |  Required |
------------------------------------|------------------|----------------------------------------------------------------------------------------------------------|-----------| 
method                              | numeric          | [Withdrawal method](#withdrawal-methods)                                                                 |     *     |
type                                | numeric          | Commission type: **1** - take commission from wallet; **2** - take commission from money                 |     *     |
amount                              | numeric          | Requested amount                                                                                         |     *     |
currency                            | string           | Currency                                                                                                 |     *     |
direction                           | string           | Direction                                                                                                |     *     |
metadata                            | **JSON object**  | Arbitrary structure object to store any additional data. Result JSON should be less than 800 kB          |     *     |
extra fields for withdrawal method  |                  | fields in accordance with different values of the method field                                           |     *     |


## Withdrawal methods

* **1** - [Bank transfer](#bank-transfer)
* **2** - [International Cards](#international-cards)

### Bank transfer

**Parameters**

Parameter                                       |        Type      |                 Description              |  Required |
------------------------------------------------|------------------|------------------------------------------|-----------|
**beneficiary**                                 | **JSON object**  | Beneficiary info                         |     *     |
&emsp;beneficiary.account                       | string[34        | Bank account number or IBAN              |     *     |
&emsp;beneficiary.name                          | string[34        | Beneficiary name                         |     *     |
&emsp;beneficiary.country                       | string[2]        | Beneficiary registration country code    |     *     |
&emsp;beneficiary.city                          | string[34]       | Beneficiary registration city            |     *     |
&emsp;beneficiary.address                       | string[34]       | Beneficiary address                      |     *     |
&emsp;beneficiary.registrationNumber            | string[34]       | Beneficiary registration number          |     [*]   |
**beneficiaryBank**                             | **JSON object**  | Beneficiary bank info                    |     *     |
&emsp;beneficiaryBank.name                      | string[34        | Bank name                                |     *     |
&emsp;beneficiaryBank.country                   | string[2]        | Bank country code                        |     *     |
&emsp;beneficiaryBank.city                      | string[34]       | Bank city                                |     *     |
&emsp;beneficiaryBank.address                   | string[34]       | Bank address                             |     *     |
&emsp;beneficiaryBank.bic                       | string           | Bank BIC/SWIFT code                      |     *     |
afsk                                            | string           | AFSK code. Required for Indian payments  |     [*]   |
routingNumber                                   | string           | Required for USA payments                |     [*]   |

### International Cards

**Parameters**

Parameter                                       |        Type      |                 Description  |  Required |
------------------------------------------------|------------------|------------------------------|-----------|
**card**                                        | **JSON object**  | Card info                    |     *     |
&emsp;card.cardNumber                           | string           | Card number                  |     *     |
&emsp;card.expirationDate                       | string           | Card expiration date name    |     *     |
&emsp;card.cardHolderName                       | string           | Cardholder Name              |     *     |
&emsp;card.cardHolderBirthDate                  | string           | Cardholder birth date        |     *     |
**address**                                     | **JSON object**  | Cardholder address           |     *     |
&emsp;address.country                           | string           | Country code                 |     *     |
&emsp;address.city                              | string           | City                         |     *     |
&emsp;beneficiaryBank.firstAddressLine          | string[250]      | Address                      |     *     |
&emsp;beneficiaryBank.secondAddressLine         | string[250]      | Address                      |           |
&emsp;beneficiaryBank.zipCode                   | string[20]       | Zip code                     |     *     |


## Request example

```shell script
curl -X POST \
  https://paydo.com/v1/withdrawals/create \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjE' \
  -d '{
          "method": "1",
          "type": "1",
          "amount": "11",
          "currency": "USD",
          "direction": "why not?",
          "metadata": {"myInternalId": "54FB-HY"},
          "additionalData": {
              "beneficiary": {
                  "account": "GB80HBUK44830812341234",
                  "name": "John Galt",
                  "city": "BIRMINGHAM",
                  "address": "1 CENTENARY SQUARE",
                  "country": "GB",
                  "registrationNumber": "4848343"
              },
              "beneficiaryBank": {
                  "name": "HSBC UK BANK PLC",
                  "city": "London",
                  "address": "London DSC 62-76 Park St Southwark",
                  "country": "GB",
                  "bic": "HBUKGB4B"
              }
          }
      }'
```
