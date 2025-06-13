# List Orders and Statistics

## List Orders

**Endpoint:** `GET /v1/order`

**Scope:** `view_order`

**Description:** Retrieves a paginated list of orders with optional filtering.

**Sorting:** The data is sorted by `created_at` in descending order and cannot be changed.

**Pagination:** This endpoint returns cursor-based pagination. The response includes `has_next` to indicate if there are more pages, `last_id` to indicate the last order ID in the current page, and `page_size` to indicate the number of items per page. The default page size is 25, and the maximum is 100.

**Query Parameters:**

- `search`: Search term to filter orders by order ID, customer name, email, or phone number
- `is_probably_spam`: "true" or "false" to filter spam orders
- `business_role`: Filter by business role ("retailer" or "fulfillment_provider)
- `draft_time_until`: Filter orders by draft time until a specific time using ISO 8601 format
- `confirmed_time_since`: Filter orders by confirmed time since a specific time using ISO 8601 format
- `confirmed_time_until`: Filter orders by confirmed time until a specific time using ISO 8601 format
- `shipped_time_since`: Filter orders by shipped time since a specific time using ISO 8601 format
- `shipped_time_until`: Filter orders by shipped time until a specific time using ISO 8601 format
- `completed_time_since`: Filter orders by completed time since a specific time using ISO 8601 format
- `completed_time_until`: Filter orders by completed time until a specific time using ISO 8601 format
- `is_from_form`: "true" or "false" to filter orders created from a form
- `is_repeat`: "true" or "false" to filter repeat orders
- `tags`: Comma-separated list of tags to filter orders
- `product_id`: Filter orders containing a specific product ID
- `is_transferproof_exist`: "true" or "false" to filter orders with transfer proof
- `order_id`: Filter orders by specific order ID
- `awb_ca_status`: Filter orders by AWB status ("unavailable", "pending", "waiting", "failed", "created", "canceled")
- `status`: Filter orders by status ("draft", "pending", "confirmed", "in_process", "ready", "canceled", "shipped", "shipped_rts", "completed", "rts", "closed")
- `payment_status`: Filter orders by payment status ("paid", "unpaid", "conflict", "settled")
- `payment_method`: Filter orders by payment method ("no_payment", "bank_transfer", "marketplace", "va", "qris", "ewallet", "cod", "card", "gopay", "invoice", "alfamart", "ovo", "dana", "shopeepay", "linkaja")
- `shipment_status`: Filter orders by shipment status
- `business_id`: Filter orders by business ID
- `store_id`: Filter orders by store ID
- `warehouse_id`: Filter orders by warehouse ID
- `courier_id`: Filter orders by courier ID
- `handler_id`: Filter orders by handler ID
- `advertiser_id`: Filter orders by advertiser ID
- `platform`: Filter orders by platform ("scalev", "tiktokshop", "tokopedia", "shopee", "lazada", "blibli", "bukalapak", "orderonline", "berdu")
- `financial_entity_id`: Filter orders by financial entity ID
- `page_id`: Filter orders by page ID
- `external_id`: Filter orders by external ID
- `utm_source`: Filter orders by UTM source
- `columns`: Comma-separated list of column options to include; possible columns are:
  `secret_slug`, `final_variants`, `store`, `origin_address`, `address_location`, `handler_phone`, `order_id`, `destination_address`, `quantity`, `product_price`, `total_weight`, `courier_service`, `shipping_cost`, `payment_method`, `gross_revenue`, `shipment_receipt`, `courier_additional_info`, `payment_status`, `status`, `customer`, `draft_time`, `orderlines`, `is_dropshipping`, `dropshipper_name`, `dropshipper_phone`, `unique_code_discount`, `tags`, `awb_status`, `awb_ca_status`, `follow_up_chats`, `follow_up_chat_type`, `message_history`, `store`, `customer`, `metadata`, `notes`, `courier_aggregator_code`, `shipment_account`, `payment_account`, `financial_entity`, `payment_account_holder`, `payment_account_number`, `transferproof_url`, `transfer_time`, `product_discount`, `shipping_discount`, `other_income`, `other_income_name`, `shipment_status`, `is_repeat`, `platform`, `external_id`, `is_purchase_fb`, `is_purchase_tiktok`, `is_purchase_kwai`, `fb_pixel_ids`, `tiktok_pixel_ids`, `kwai_pixel_ids`, `pending_time`, `confirmed_time`, `shipped_time`, `completed_time`, `rts_time`, `canceled_time`, `closed_time`, `warehouse`, `page`, `channel_name`, `handler`, `advertiser`, `pg_payment_info`, `sub_payment_method`, `epayment_provider`, `invoice_url`, `pg_reference_id`, `net_revenue`, `payment_fee`, `scalev_fee`, `net_payment_revenue`, `discount_code_discount`, `discount_code_code`, `discount_code_applied_to`, `utm_source`

All query parameters are always string and optional, and can be combined for filtering.

**Example Response:**

```json
{
  "code": 200,
  "status": "Success",
  "data": {
    "has_next": true,
    "last_id": 67295,
    "page_size": 25
    "results": [
      {
        "advertiser": {
          "id": 310,
          "email": "owner.ctr21@gmail.com",
          "phone": "628118906070",
          "fullname": "Test Account",
          "avatar": "https://cdn.scalev.id/User/bb08dba70ee74da9a45897b922bc52e7.jpg"
        },
        "awb_ca_status": "unavailable",
        "awb_status": "unavailable",
        "canceled_time": null,
        "channel_name": null,
        "closed_time": null,
        "completed_time": null,
        "confirmed_time": null,
        "courier_additional_info": null,
        "courier_aggregator_code": null,
        "courier_service": {
          "id": 6,
          "name": "Standard",
          "code": "STANDARD",
          "code_co": "Standard",
          "code_ka": "STANDARD",
          "code_ro": "STANDARD",
          "code_lincah": "Standard",
          "code_mengantar": "Ninja",
          "courier": {
            "id": 2,
            "name": "Ninja Xpress",
            "code": "ninja",
            "code_ro": "ninja",
            "code_ka": null,
            "code_lincah": "ninja",
            "code_mengantar": "Ninja",
            "courier_type": "standard",
            "is_pickup": false
          }
        },
        "created_at": "2025-05-22T02:03:20Z",
        "customer": {
          "id": 21817,
          "name": "Abdurrahman Arroisi",
          "email": "aarroisi@gmail.com",
          "phone": "628118906070",
          "confirmed_at": "2025-01-15T10:09:30Z",
          "created_at": "2023-06-26T07:41:40Z",
          "last_updated_at": "2025-04-11T15:23:23Z",
          "status": "active"
        },
        "destination_address": {
          "id": 64348,
          "name": "Arman Testing",
          "phone": "628118906070",
          "location": 9104,
          "address": "bintaro",
          "subdistrict": "Pesanggrahan",
          "city": "Kota Jakarta Selatan",
          "province": "DKI Jakarta",
          "postal_code": null
        },
        "discount_code_applied_to": null,
        "discount_code_code": null,
        "discount_code_discount": 0.0,
        "draft_time": "2025-05-22T02:03:20Z",
        "dropshipper_name": null,
        "dropshipper_phone": null,
        "epayment_provider": null,
        "external_id": null,
        "fb_pixel_ids": [
          "345723411389069"
        ],
        "final_variants": {
          "multi fisik - Large": 1
        },
        "financial_entity": null,
        "follow_up_chat_type": "product",
        "follow_up_chats": [],
        "gross_revenue": 27183.0,
        "handler": {
          "id": 362,
          "email": "anto@yopmail.com",
          "phone": null,
          "fullname": "Kang Anto",
          "avatar": null
        },
        "handler_phone": "6285156627902",
        "id": 67295,
        "is_dropshipping": false,
        "is_probably_spam": false,
        "is_purchase_fb": false,
        "is_purchase_kwai": false,
        "is_purchase_tiktok": false,
        "is_repeat": true,
        "kwai_pixel_ids": [
          "214987164781",
          "259388395010611"
        ],
        "last_updated_at": "2025-05-22T02:03:20Z",
        "mark_as_spam_by": null,
        "message_history": [],
        "metadata": {
          "click_id": "12345",
          "event_source_url": "http://modelez.localhost:4000/landing-page-baru-688?click_id=12345",
          "ip": "127.0.0.1",
          "kwai_clickid": "12345",
          "origin": "http://modelez.localhost:4000",
          "referer": "http://modelez.localhost:4000/",
          "ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36 Edg/135.0.0.0"
        },
        "net_payment_revenue": "27183.00",
        "net_revenue": 19406.0,
        "notes": "",
        "order_id": "250522AYWXTJK",
        "origin_address": {
          "id": 6670,
          "warehouse": 6550,
          "location": 9104,
          "address": "bintarp",
          "subdistrict": "Pesanggrahan",
          "city": "Kota Jakarta Selatan",
          "province": "DKI Jakarta",
          "postal_code": "12330"
        },
        "other_income": 0.0,
        "other_income_name": "Biaya Lainnya",
        "page": {
          "id": 2488,
          "unique_id": "page_8AFxXRnFa6Rif3gLfICvhfKV",
          "name": "Lengkap ini",
          "slug": "landing-page-baru-688",
          "is_published": true
        },
        "payment_account_holder": null,
        "payment_account_id": null,
        "payment_account_number": null,
        "payment_fee": 0.0,
        "payment_method": "bank_transfer",
        "payment_status": "unpaid",
        "pending_time": "2025-05-22T02:03:20Z",
        "pg_payment_info": {},
        "pg_reference_id": null,
        "platform": "scalev",
        "product_discount": 0.0,
        "product_price": 2.0e4,
        "rts_time": null,
        "scalev_fee": 0.0,
        "secret_slug": "4lh1deZvDqux3HQNXuivLCYx40guWCtmSJFpRg0M",
        "shipment_receipt": null,
        "shipment_status": null,
        "shipped_time": null,
        "shipping_cost": 7777.0,
        "shipping_discount": 0.0,
        "status": "pending",
        "store": {
          "id": 5495,
          "unique_id": "store_UR0Aztt08DBoW8psT8RuwNVm",
          "uuid": "c10c0030-7944-48c1-84ed-c6608c687382",
          "name": "heheh test",
          "business": {
            "id": 1290,
            "is_banned": false,
            "unique_id": "CJBWGIUNOUYWKFAC",
            "account_holder": "PT Modelez  1",
            "email": "bisnisaneh16@yopmail.com",
            "logo": "https://cdn.scalev.id/Business/qq1IvU8opASHCSEKqPbV7gDIsUAGGN1YUFer0IV5rQM/1737458806302-6862d817-4c64-4107-8_xiAHyPI.webp",
            "username": "modelez"
          }
        },
        "sub_payment_method": null,
        "tags": [],
        "tiktok_pixel_ids": [
          "CAT9GGRC77UAKBURPDL0"
        ],
        "total_weight": 200,
        "transfer_time": null,
        "transferproof_url": null,
        "unique_code_discount": 594.0,
        "utm_source": "",
        "warehouse": {
          "id": 6550,
          "name": "Gudang Baru Test Kontak",
          "contact_name": "Kontak Baru",
          "contact_phone": "08112345678",
          "business": {
            "id": 1290,
            "is_banned": false,
            "unique_id": "CJBWGIUNOUYWKFAC",
            "account_holder": "PT Modelez  1",
            "email": "bisnisaneh16@yopmail.com",
            "logo": "https://cdn.scalev.id/Business/qq1IvU8opASHCSEKqPbV7gDIsUAGGN1YUFer0IV5rQM/1737458806302-6862d817-4c64-4107-8_xiAHyPI.webp",
            "username": "modelez"
          }
        }
      },
      ...
    ]
  }
}
```

## Order Statistics

**Endpoint:** `GET /v1/order-statistics`

**Scope:** `view_order`

**Description:** Retrieves descriptive statistics about orders, such as total orders, total revenue, and other aggregated data.

**Query Parameters:**

- `datetime_type`: Optional parameter to specify the type of datetime for statistics. If not provided, defaults to "created_at". Possible values are "draft_time", "pending_time", "confirmed_time", "in_process_time", "ready_time", "canceled_time", "shipped_time", "shipped_rts_time", "completed_time", "rts_time", "closed_time".
- `tz`: Optional timezone parameter to adjust the datetime for statistics. Defaults to "Asia/Jakarta".
- `breakdown_date`: Optional parameter to specify the date breakdown for statistics. If not provided, defaults to "off". Possible values are "off", "day", "week", "month".
- `is_breakdown_status`: Optional parameter to include breakdown by order status. Defaults to "false". Possible values are "true" or "false".
- `custom_breakdown_key`: Optional parameter to specify a custom breakdown key for statistics. If not provided, defaults to "off". Possible values are "handler_id", "advertiser_id", "page_id", "city", "province".
- `minimum_days`: Optional parameter to specify the minimum number of days for statistics. If not provided, defaults to 0.

To filter which orders to include in the statistics, you can use the same query parameters as the `/order` endpoint, such as `status`, `payment_status`, `business_id`, `store_id`, etc.

**Example Response:**

```json
{
  "code": 200,
  "status": "Success",
  "data": {
    "datetime_type": "shipped_time",
    "breakdown_date": "week",
    "tz": "Asia/Jakarta",
    "is_breakdown_status": true,
    "custom_breakdown_key": "store_id",
    "params": {
      "shipped_time_since": "2024-08-05T17:00:00.000Z",
      "shipped_time_until": "2024-10-15T17:00:00.000Z",
      "status": "confirmed,in_process,ready,shipped,completed"
    },
    "results": [
      {
        "count": 14,
        "status": "completed",
        "week": "2024-38",
        "gross_revenue": 2446004,
        "custom_breakdown_id": 5491,
        "custom_breakdown_name": "Store Test 1"
      },
      {
        "count": 2,
        "status": "completed",
        "week": "2024-42",
        "gross_revenue": 1278859,
        "custom_breakdown_id": 5491,
        "custom_breakdown_name": "Store Test 1"
      },
      {
        "count": 5,
        "status": "in_process",
        "week": "2024-33",
        "gross_revenue": 3419098,
        "custom_breakdown_id": 5491,
        "custom_breakdown_name": "Store Test 1"
      },
      {
        "count": 1,
        "status": "ready",
        "week": "2024-33",
        "gross_revenue": 140000,
        "custom_breakdown_id": 5491,
        "custom_breakdown_name": "Store Test 1"
      },
      {
        "count": 1,
        "status": "shipped",
        "week": "2024-38",
        "gross_revenue": 134610,
        "custom_breakdown_id": 5491,
        "custom_breakdown_name": "Store Test 1"
      },
      {
        "count": 1,
        "status": "completed",
        "week": "2024-40",
        "gross_revenue": 255000,
        "custom_breakdown_id": 5557,
        "custom_breakdown_name": "Store Test 2"
      },
      {
        "count": 1,
        "status": "ready",
        "week": "2024-40",
        "gross_revenue": 164703,
        "custom_breakdown_id": 5560,
        "custom_breakdown_name": "Store Test 3"
      },
      {
        "count": 1,
        "status": "shipped",
        "week": "2024-40",
        "gross_revenue": 164866,
        "custom_breakdown_id": 5560,
        "custom_breakdown_name": "Store Test 3"
      }
    ]
  }
}
```
