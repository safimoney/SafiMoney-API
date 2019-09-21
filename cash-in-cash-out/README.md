SafiMoney Cash In Cash Out API

**This API is available only for Partner Wallets.**

Please follow the [reference guide](../reference guide) for more details of SafiMoney API.

------

```php
POST https://api.safimoney.com/api/v2
```

### Get Transaction

To get the details of a transaction

- <u>Bearer Access Token</u>

  | Bearer Header Token | Description |
  | ------------------- | ----------- |
  | namespace           | Transaction |
  | action              | get         |

  

- <u>Request Parameters</u>

  The get transaction request should include the following parameters:

  | Request Parameters | Description            | Type    |          |
  | ------------------ | ---------------------- | ------- | -------- |
  | id                 | id of your transaction | numeric | required |

  

- <u>Response</u>

  ```json
  {
      "request": {
          "id": "1000000000001357"
      },
      "status": "200",
      "data": {
          "transaction": {
              "id": "1000000000001357",
              "debit_wallet_id": "1000000000000000",
              "credit_wallet_id": "1000000000004750",
              "purpose": null,
              "debit_transfer_value": 12,
              "debit_amount": 112,
              "credit_transfer_value": 12,
              "credit_amount": 12,
              "debit_fee_amount": 100,
              "credit_fee_amount": 0,
              "partner_commission": 50,
              "debit_country": "CM",
              "debit_currency": "XAF",
              "credit_country": "CM",
              "credit_currency": "XAF",
              "exchange_rate": 1,
              "reference_id": null,
              "status": "Freeze",
              "sender_name": null,
              "receiver_name": "user-1",
              "receiver_mobile_number": "+237-666111444",
              "approved_at": null,
              "invoice_id": 62,
              "notes": null,
              "cancelled_at": null
          }
      },
      "error": null
  }
  ```

  - data

    | Parameters             | Description |
    | ---------------------- | ----------- |
    | id                     |             |
    | debit_wallet_id        |             |
    | credit_wallet_id       |             |
    | purpose                |             |
    | debit_transfer_value   |             |
    | debit_amount           |             |
    | credit_transfer_value  |             |
    | credit_amount          |             |
    | debit_fee_amount       |             |
    | credit_fee_amount      |             |
    | partner_commission     |             |
    | debit_country          |             |
    | debit_currency         |             |
    | credit_country         |             |
    | credit_currency        |             |
    | exchange_rate          |             |
    | reference_id           |             |
    | status                 |             |
    | sender_name            |             |
    | receiver_name          |             |
    | receiver_mobile_number |             |
    | approved_at            |             |
    | invoice_id             |             |
    | notes                  |             |
    | cancelled_at           |             |

    

  - error

    - Validation Error

      - *Required*

        ```json
        "error": {
            "title": "Error !",
            "message": "The id field is required.",
            "remedy": "Please Retry or Report to Support Team !",
            "validation": {
                "id": [
                	"The id field is required."
                ]
            },
            "data": null
        }
        ```

        

      - *Invalid*

        ```json
        "error": {
            "title": "Error !",
            "message": "The selected id is invalid.",
            "remedy": "Please Retry or Report to Support Team !",
            "validation": {
                "id": [
                	"The selected id is invalid."
                ]
            },
            "data": null
        }
        ```

        

### Get Transaction By Reference ID



### List of Transactions





### Cash In

The Cash In request will deposit the wallet money in the requested wallet in return of Cash. 

- <u>Bearer Access Token</u>

  To create access token for Cash In request, the namespace and action are as follows: 

  | Bearer Header Token | Description |
  | ------------------- | ----------- |
  | namespace           | Transaction |
  | action              | cashIn      |

  

- <u>Request Parameters</u>

  The Cash In Request should include the following parameters:

  | Request Parameters | Description                                              | type      |            |
  | ------------------ | -------------------------------------------------------- | --------- | ---------- |
  | reference_id       | This reference id will help you to track the transaction | string    | *optional* |
  | debit_wallet_id    | your wallet id                                           | *numeric* | *required* |
  | amount             | amount you want to deposit                               | *decimal* | *required* |
  | include_fee        | fee (if any) will be deducted from the entered amount    | *boolean* | *required* |
  | debit_currency     | your wallet's currency (ex. XAF OR EUR)                  | *string*  | *required* |
  | credit_currency    | wallet's currency in which you want to deposit           | *string*  | *required* |
  | credit_wallet_id   | wallet's ID in which you want to deposit                 | *numeric* | *required* |
  | purpose            | purpose/notes attached to this transaction               | *string*  | *optional* |

  

- <u>Response</u>

  The response consist of following details:

  - request

    

  - status

  - data

  - error

    

```json
{
	"status" : 200,
    "data": {
        "message": "Cash Deposit Successfully",
        "transaction": 
        {
            "id": "1000000000001652",
            "debit_wallet_id": "1000000000004904",
            "credit_wallet_id": "1000000000000398",
            "purpose": "Cash In",
            "debit_transfer_value": 250,
            "debit_amount": 250,
            "credit_transfer_value": 250,
            "credit_amount": 250,
            "debit_fee_amount": 0,
            "credit_fee_amount": 0,
            "partner_commission": 10,
            "debit_country": "CM",
            "debit_currency": "XAF",
            "credit_country": "CM",
            "credit_currency": "XAF",
            "exchange_rate": 1,
            "status": "Approved",
            "sender_name": null,
            "receiver_name": null,
            "receiver_mobile_number": null,
            "approved_at": "2019-09-14 05:52:26",
            "invoice_id": 94,
            "notes": null,
            "cancelled_at": null
        }
    },
    "error": null
}
```



- In the Response, SafiMoney will return Transaction Detail

  

### <u>Cash Out</u>

**Response**

```json
{
	"status" : 200,
    "data" : {
       "transaction": 
        {
            "id": "1000000000001580",
            "invoice_id": 84,
            "debit_transfer_value": 250,
            "debit_currency": "XAF",
            "credit_currency": "XAF",
            "debit_wallet_id": "1000000000004904",
            "credit_wallet_id": "1000000000004070",
            "exchange_rate": 1,
            "type": "4",
            "status": 30,
            "purpose": "Cash In",
            "receiver_name": null,
            "receiver_mobile_number": null,
            "debit_country": "CM",
            "credit_country": "CM",
            "credit_transfer_value": 250,
            "debit_fee_amount": 0,
            "credit_fee_amount": 0,
            "debit_amount": 250,
            "credit_amount": 250,
            "approved_at": "2019-09-13 05:21:46",   
        }
    },
    "error": null
}
```



- **Submit ID Proof**	    

***POST*** ***https://api.safimoney.com/api/v2***

| Bearer Header Token | Description   |
| ------------------- | ------------- |
| namespace           | IdentityProof |
| action              | save          |



| Request Parameters | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| transaction_id     | Transaction Id*                                              |
| name               | Name of ID Proof                                             |
| number             | Number on ID Proof                                           |
| expiry_date        | Expiry Date of ID Proof                                      |
| type               | Type of ID Proof e.g for Personal ID Proof set 10 for Business type set 20 |

[^transaction_id]: do not include SM-, transaction id are purely numerical

**Response**

```json
{
	"status" : 200,
    "message": "Id Proof created successfully"
}
```



- **Approve Cash Out**	    

***POST*** ***https://api.safimoney.com/api/v2***

------

| Bearer Header Token | Description              |
| ------------------- | ------------------------ |
| namespace           | Transaction              |
| action              | approveWithdrawByPartner |



| Request Parameters | Description    |
| ------------------ | -------------- |
| id                 | Transaction Id |
| pin_number         | Withdrawl code |

[^id]: do not include SM-, transaction id are purely numerical



**Response**

```json
{
    "status": "200",
    "data": {
        "message": "Money Paid to customer successfully",
        "transaction": {
            "id": "1000000000001397",
            "debit_wallet_id": "1000000000000000",
            "credit_wallet_id": "1000000000004904",
            "purpose": null,
            "debit_transfer_value": 51.22,
            "debit_amount": 151.22,
            "credit_transfer_value": 51.22,
            "credit_amount": 51.22,
            "debit_fee_amount": 100,
            "credit_fee_amount": 0,
            "partner_commission": 50,
            "debit_country": "CM",
            "debit_currency": "XAF",
            "credit_country": "CM",
            "credit_currency": "XAF",
            "exchange_rate": 1,
            "status": "Approved",
            "sender_name": null,
            "receiver_name": "user-1",
            "receiver_mobile_number": "+237-666111444",
            "approved_at": "2019-09-14 10:44:06",
            "invoice_id": 66,
            "notes": null,
            "cancelled_at": null
        }
    },
    "error": null
}
```



