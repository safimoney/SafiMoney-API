SafiMoney Cash In Cash Out API

------

**This API is available only for Partner Wallets.**

### <u>**Cash In**</u>



***POST*** ***https://api.safimoney.com/api/v2***

------

| Request Parameters | Description                                         |            |
| ------------------ | --------------------------------------------------- | ---------- |
| debit_wallet_id    | your wallet id                                      | *required* |
| amount             | Amount you want to deposit                          | *required* |
| amount_type        | Please see the below note                           | *required* |
| debit_currency     | Your wallet's currency (ex. XAF OR EUR)             | *required* |
| credit_currency    | Wallet's currency in which you want to deposit cash | *required* |
| credit_wallet_id   | Wallet's ID in which you want to deposit cash       | *required* |
| type               | For Cash In type is 4                               | *required* |
| purpose            | Purpose/notes attached to this transaction          | *optional* |

> Note : Amount type denotes that the Fee (if any) will be deducted from the entered amount or additionally charged on entered amount.  
> These are the values for amount type:
>
> 'debit_amount' : 'Fee (if any) will be deducted from the entered amount',
>
> 'debit_transfer_value' : 'Fee (if any) will be additionally charged on entered amount'

**Response**

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



- **Approve Cash Out**	    

***POST*** ***https://api.safimoney.com/api/v2***

| Request Parameters | Description    |
| ------------------ | -------------- |
| id                 | Transaction Id |
| pin_number         |                |

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



