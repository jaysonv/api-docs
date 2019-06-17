# Order management

**API endpoint**: `/orders`

## Get user list

`GET /orders.json`

Return the list of all orders for current marketplace.

## Get specific user details

`GET /orders/{id}.json`

Return the details for a specific order.

Example response:

```json
{
    "order": {
        "id": 3,
        "psp": "Stripe Connect",
        "transaction_type": "booking",
        "order_number": "1903XCVJPWSD",
        "status_id": 5,
        "customer_id": 3,
        "supplier_id": 1,
        "listing_id": 16,
        "unit_price": 111,
        "total_qty": 1,
        "booking_period": 1,
        "total_amount": 111,
        "fees": 11.6,
        "banking_fees": 2.18,
        "created": "2019-03-21T17:22:49+00:00",
        "message": "But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the actual teachings of the great explorer of the truth, the master-builder of human happiness."
    }
}
```

## Update order data

`PUT|PATCH /orders/{id}.json`

Update the user with given `id`. 

New data passed as raw JSON body content (content-type: application/json). E.g:

Accepted fields: 

- `status_id` (integer). The status id to update the order with. List of order statuses obtained by calling `/orders/statuses.json`.  

Example request:

```json
{
    "status_id": 3 
}
```

Example response:

```json
{
    "success": true,
    "message": "Order updated"
}
```

Throws a 404 Not Found error if order or order status does not exist.
