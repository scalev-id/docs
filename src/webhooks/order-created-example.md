# Order Created Event Example Payload

```json
{
  "event": "order.spam_created",
  "unique_id": "event_I7fkiBF4YksYDsKbVe5ZOEyZ",
  "timestamp": "2025-01-29T20:28:25.046183Z",
  "data": {
    "order_id": "250130JQHFZG",
    "secret_slug": "WjCc_Jk-EK2F8xLCseNKfjFIaESbm9-W2RZvRaas",
    "status": "pending",
    "is_probably_spam": true,
    "mark_as_spam_by": "ai",
    "draft_time": "2025-01-29T20:28:08Z",
    "pending_time": "2025-01-29T20:28:08Z",
    "confirmed_time": null,
    "in_process_time": null,
    "ready_time": null,
    "shipped_time": null,
    "completed_time": null,
    "rts_time": null,
    "canceled_time": null,
    "closed_time": null,
    "payment_status": "unpaid",
    "unpaid_time": "2025-01-29T20:28:08Z",
    "paid_time": null,
    "conflict_time": null,
    "settled_time": null,
    "business": {
      "username": "username",
      "client_id": "41750fd8-e7e2-4887-b348-04c01a547ae0"
    },
    "store": {
      "name": "Example Store"
    },
    "epayment_provider": null,
    "payment_method": "bank_transfer",
    "sub_payment_method": null,
    "financial_entity": {
      "code": "bni",
      "name": "Bank Negara Indonesia"
    },
    "payment_account_holder": "Unreal Person",
    "payment_account_number": "1234567812345678",
    "transferproof_url": "https://cdn.scalev.com/Image/dGONXQPPK_hDCrEL3lfEnOQoPOBwuRUZUUyjxreQCzQ/1738182480347-milkbox.webp",
    "transfer_time": null,
    "final_variants": {
      "Amazing Product": 1
    },
    "total_quantity": 1,
    "gross_revenue": "168724.00",
    "unique_code_discount": "276.00",
    "discount_code_discount": "0.00",
    "net_revenue": "149724.00",
    "product_price": "150000.00",
    "product_discount": "0.00",
    "other_income_name": "Biaya Lainnya",
    "other_income": "0.00",
    "discount_rate": "0.00",
    "cogs": "45095.00",
    "shipping_cost": "19000.00",
    "shipping_discount": "0.00",
    "payment_fee": "0.00",
    "customer_id": 28024,
    "destination_address": {
      "name": "Example Person",
      "phone": "628112345678",
      "email": "testing@example.com",
      "address": "This is not a real address.",
      "subdistrict": "Gayungan",
      "city": "Kota Surabaya",
      "province": "Jawa Timur",
      "postal_code": null,
      "notes": ""
    },
    "origin_address": {
      "address": "This is not a real address.",
      "subdistrict": "Gunung Jati (Cirebon Utara)",
      "city": "Kabupaten Cirebon",
      "province": "Jawa Barat",
      "postal_code": "45151"
    },
    "warehouse": {
      "name": "Example Warehouse",
      "unique_id": "warehouse_FN9odhpi1VOF7FLxMhtiWdJo"
    },
    "product_weight": 500,
    "weight_bump": 0,
    "total_weight": 500,
    "courier_service": {
      "courier": {
        "name": "Ninja Xpress",
        "code": "ninja"
      },
      "name": "Standard",
      "code": "STANDARD"
    },
    "courier_aggregator_code": null,
    "rtsproof_url": null,
    "shipment_receipt": null,
    "shipment_status": null,
    "awb_status": "unavailable",
    "awb_ca_status": "unavailable",
    "notes": "Example notes.",
    "tags": [],
    "orderlines": [
      {
        "quantity": 1,
        "is_inventory": false,
        "weight": 500,
        "product_name": "Amazing Product",
        "variant_unique_id": "variant_Wifko5BIJbnQoo9LPAiJ63Kv",
        "variant_sku": "BCF009",
        "variant_price": "150000.00",
        "variant_cogs": "45095.00",
        "product_price": "150000.00",
        "discount": "0.00",
        "discount_code_discount": "0.00",
        "cogs": "45095.00"
      }
    ],
    "created_at": "2025-01-29T20:28:08Z",
    "last_updated_at": "2025-01-29T20:28:08Z"
  }
}
```
