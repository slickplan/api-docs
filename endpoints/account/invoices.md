# Invoices

## Get all invoices

* `GET /v1/account/invoices`
* Required scope: `invoice_history_read`

### Response
``` json
[
    {
        "id": 3,
        "transaction_id": 1234567890,
        "amount": 9.99,
        "date": "2012-09-15T17:31:27-04:00"
    },
    {
        "id": 2,
        "transaction_id": 6789012345,
        "amount": 3.99,
        "date": "2012-06-08T12:01:41-04:00"
    }
]
```
Key | Type | Description
--- | --- | ---
id | integer | Invoice ID.
transaction_id | integer | Transaction ID.
amount | float | Amount in USD.
date | string | Invoice date in ISO 8601 format.

## Get single invoice

* `GET /v1/account/invoices/2`
* Required scope: `invoice_history_read`

### Response
``` json
{
    "id": 2,
    "transaction_id": 6789012345,
    "amount": 3.99,
    "date": "2012-06-08T12:01:41-04:00"
}
```