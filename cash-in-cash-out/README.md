**SafiMoney Cash In Cash Out API**

------

This API is available only for Partner Wallets.

> **Cash In**

***POST*** ***https://api.safimoney.com/api/v2***

------

| Request Parameters | Description                                                  |            |
| ------------------ | ------------------------------------------------------------ | ---------- |
| debit_wallet_id    | your wallet id                                               | *required* |
| amount             | Amount you want to deposit                                   | *required* |
| amount_type        | You can choose in which language you want your user to see the redirect page. Currently we support only two languages EN(English) and FR(french) | *required* |
| debit_currency     | Your wallet's currency (ex. XAF OR EUR)                      | *required* |
| credit_currency    | Wallet's currency in which you want to deposit cash          | *required* |
| credit_wallet_id   | Wallet's ID in which you want to deposit cash                | *required* |
| type               | 4                                                            | *required* |
| purpose            | Purpose/notes attached to this transaction                   | *optional* |

**Response**

```json
{
	"status" : 200,
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
    },
    "message": "sm.transaction/cash_deposit_successfully"	
}
```



- In the Response, SafiMoney will return Transaction Detail

  

> Cash Out

- **Search Transaction** 

  ***POST*** ***https://api.safimoney.com/api/v2***

  ------

| Request Parameters | Description    |          |
| ------------------ | -------------- | -------- |
| id                 | Transaction Id | required |

**Response**

```json
{
	"status" : 200,
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
}
```



- Submit ID Proof	    

***POST*** ***https://api.safimoney.com/api/v2***

| Request Parameters | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| transaction_id     | Transaction Id                                               |
| name               | Name of ID Proof                                             |
| number             | Number on ID Proof                                           |
| expiry_date        | Expiry Date of ID Proof                                      |
| type               | Type of ID Proof e.g for Personal ID Proof set 10 for Business type set 20 |

**Response**

```json
{
	"status" : 200,
    "message": "Id Proof created successfully"
}
```



- Approve Cash Out	    

***POST*** ***https://api.safimoney.com/api/v2***

| Request Parameters | Description    |
| ------------------ | -------------- |
| id                 | Transaction Id |
| pin_number         |                |

**Response**

```json
{
	"status" : 200,
    "message": "Money Paid to customer successfully"
}
```



