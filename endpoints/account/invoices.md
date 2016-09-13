# Invoices

## Get all invoices

* `GET /v1/account/invoices`
* Required scope: `invoice_history_read`

### Response
``` json
[
    {
        "id": 3,
        "transaction_id": "1234567890",
        "amount": 9.99,
        "date": "2012-09-15T17:31:27+00:00",
        "description": "Slickplan Basic Plan (example.slickplan.com), Monthly Subscription"
    },
    {
        "id": 2,
        "transaction_id": "6789012345",
        "amount": 5,
        "date": "2012-06-08T12:01:41+00:00",
        "description": "Slickplan (example.slickplan.com), One-Time Site Crawler"
    }
]
```

Possible other [responses](./../../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
id | integer | Invoice ID
transaction_id | integer | Transaction ID
amount | float | Amount in USD
date | string | Invoice date in Atom format
description | string | Transaction description

## Get single invoice

* `GET /v1/account/invoices/3`
* Required scope: `invoice_history_read`

### Response
``` json
{
    "id": 3,
    "transaction_id": "1234567890",
    "amount": 9.99,
    "date": "2012-09-15T17:31:27+00:00",
    "description": "Slickplan Basic Plan (example.slickplan.com), Monthly Subscription"
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.