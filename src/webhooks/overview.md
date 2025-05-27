# Webhooks

Webhooks are ways for Scalev to notify you when certain events happen. When the specified events occur, Scalev will send an HTTP POST request to the webhook URL you provided. You can use webhooks to trigger custom code or actions in your system.

Webhooks are sent as POST requests with a JSON payload in the request body. The payload contains the event type and the data associated with the event. The webhook URL must be a publicly accessible URL that can receive POST requests from Scalev.

## Verifying a Webhook Request

To authenticate webhook requests from Scalev, verify the signature included in the `X-Scalev-Hmac-Sha256` header. This signature is created using your Client Secret as the key in an HMAC-SHA256 algorithm. To validate each request:

1. Extract the signature from the `X-Scalev-Hmac-Sha256` header
2. Calculate your own HMAC-SHA256 digest using your Client Secret
3. Compare your calculated digest with the received signature

If the signatures match, you can trust that the webhook came from Scalev and wasn't tampered with.

Here are code examples to help you validate the webhook:

### Node.js

```javascript
// Using crypto-js dependency
const HMACSHA256 = require("crypto-js/hmac-sha256");
const BASE64 = require("crypto-js/enc-base64");
const calculatedHmac = BASE64.stringify(
  HMACSHA256("JSON-BODY-HERE", "YOUR-CLIENT-SECRET-HERE"),
);
console.log(calculatedHmac);
```

### Python

```python
import hmac
import base64
json_body = 'JSON-BODY-HERE'.encode('utf-8')
client_secret = 'YOUR-CLIENT-SECRET-HERE'.encode('utf-8')
calculated_hmac = base64.b64encode(
   hmac.new(client_secret, json_body, 'sha256').digest()
).decode('utf-8')
print(calculated_hmac)
```

## Available Events

Scalev currently supports the following webhook events:

- `order.created`: Triggered when a new order is created. [Payload example](./order-created-example.md)
- `order.updated`: Triggered when an existing order is updated. [Payload example](./order-updated-example.md)
- `order.deleted`: Triggered when an order is deleted. [Payload example](./order-deleted-example.md)
- `order.status_changed`: Triggered when the status of an order changes. [Payload example](./order-status-changed-example.md)
- `order.payment_status_changed`: Triggered when the payment status of an order changes. [Payload example](./order-payment-status-changed-example.md)
- `order.spam_created`: Triggered when a spam order is created. [Payload example](./order-spam-created-example.md)
