
# Integration Loyalty Service & Payment
## Author - Alexander Adu-SAarkodie

```

1. Create Voucher

Example request

url -X POST \
  -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
  -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c" \
  -H "Content-Type: application/json" \
  -d '{
    "category": "New Customers",
    "type": "DISCOUNT_VOUCHER",
    "discount": {
        "percent_off": 10.0,
        "type": "PERCENT"
    },
    "start_date": "2016-01-01T00:00:00Z",
    "expiration_date": "2016-12-31T23:59:59Z",
    "redemption": {
        "quantity": 1 
    },
    "code_config": {
        "pattern": "PROMO-#####"
    },
    "metadata": {
      "test": true,
      "locale": "de-en"
    }
  }' \
  https://api.XXXX.io/v1/vouchers/



Example response

{
  "code": "PROMO-BVodE",
  "campaign": null,
  "category": "New Customers",
  "type": "DISCOUNT_VOUCHER",
  "discount": {
    "type": "PERCENT",
    "percent_off": 10
  },
  "gift": null,
  "start_date": "2016-01-01T00:00:00Z",
  "expiration_date": "2016-12-31T23:59:59Z",
  "publish": {
    "object": "list",
    "count": 0,
    "url": "/v1/vouchers/PROMO-BVodE/publications?page=1&limit=10"
  },
  "redemption": {
    "object": "list",
    "quantity": 1,
    "redeemed_quantity": 0,
    "url": "/v1/vouchers/PROMO-BVodE/redemptions?page=1&limit=10"
  },
  "active": true,
  "additional_info": null,
  "metadata": {
    "test": true,
    "locale": "de-en"
  }
}


2. Get Voucher


Example request 

curl -X GET \
  -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
  -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c" \
  -H "Content-Type: application/json" \
  https://api.xxxxx.io/v1/vouchers/Testing7fjWdr


Example response
 {
  "code": "Testing7fjWdr",
  "campaign": null,
  "category": "test",
  "type": "DISCOUNT_VOUCHER",
  "discount": {
    "type": "AMOUNT",
    "amount_off": 1000
  },
  "gift": null,
  "start_date": null,
  "expiration_date": null,
  "publish": {
    "object": "list",
    "count": 0,
    "data_ref": "entries",
    "entries": [],
    "total": 0,
    "url": "/v1/xxxxx/Testing7fjWdr/publications?page=1&limit=10"
  },
  "redemption": {
    "object": "list",
    "total": 2,
    "data_ref": "redemption_entries",
    "quantity": null,
    "redeemed_quantity": 2,
    "redeemed_amount": 20050,
    "url": "/v1/xxxxx/Testing7fjWdr/redemptions?page=1&limit=10",
    "redemption_entries": [
      {
        "id": "r_XbytKOFW8wnheSScssMgRNMm",
        "object": "redemption",
        "date": "2016-11-17T10:22:46Z",
        "customer_id": "cust_ztSxSmEZr8a4rop60yzjVZIq",
        "tracking_id": "track_+EUcXP8WDKXGf3mYmWxbJvEosmKXi3Aw",
        "amount": 20050,
        "order": {
          "amount": 20050,
          "items": [
            {
              "product_id": "prod_anJ03RZZq74z4v",
              "sku_id": null,
              "quantity": 2
            },
            {
              "product_id": null,
              "sku_id": "sku_0KtP4rvwEECQ2U",
              "quantity": 1
            }
          ]
        },
        "result": "SUCCESS"
      },
      {
        "id": "r_zCNrR5UdWHTFa7ABQtqH36Yb",
        "object": "redemption",
        "date": "2016-11-17T12:05:54Z",
        "customer_id": "cust_ztSxSmEZr8a4rop60yzjVZIq",
        "tracking_id": "track_+EUcXP8WDKXGf3mYmWxbJvEosmKXi3Aw",
        "order": {
          "amount": null,
          "items": []
        },
        "result": "SUCCESS"
      }
    ]
  },
  "active": true,
  "additional_info": null,
  "metadata": null,
  "assets": {
    "qr": {
      "id": "U2FsdGVkX1+VOQlTlRoSKfY7mISP6o/vtc76wyxwGpIuzVAboyfg9Z+yAd0uW79KTuoZDBPrNPRgaGFtF/+fW/8JbbdNiIyYdtK9KCEf2XdLwXkkxWwp4YlL1xp71WD96NH+L68Nj3GUpEU55CoZhQ==",
      "url": "https://dl.voucherify.io/api/v1/assets/qr/U2FsdGVkX1%2BVOQlTlRoSKfY7mISP6o%2Fvtc76wyxwGpIuzVAboyfg9Z%2ByAd0uW79KTuoZDBPrNPRgaGFtF%2F%2BfW%2F8JbbdNiIyYdtK9KCEf2XdLwXkkxWwp4YlL1xp71WD96NH%2BL68Nj3GUpEU55CoZhQ%3D%3D"
    }
  }
}


3.  Validation Voucher

Example request

curl -X POST \
  -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
  -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c" \
  -H "Content-Type: application/json" \
  -d '{
    "customer" : {
      "id" : "cust_07sVjVsr71Ewot9lVZSrIVLH",
      "source_id" : "john@lemon.com",
      "name": "John Lemon"
    },
    "order" : {
      "amount" : 1000,
      "items": [
        { "product_id": "prod_anJ03RZZq74z4v", "quantity": "1" },
        { "sku_id": "sku_dSbRQfbyUMyHnt", "quantity": "1" },
        { "sku_id": "sku_0KtP4rvwEECQ2U", "quantity": "1" }
      ]
    },
    "metadata": {
      "locale": "en-GB"
    }
  }' \
  https://api.XXXX.io/v1/vouchers/Testing7fjWdr/validate

  Example response

  {
  "code": "Testing7fjWdr",
  "valid": true,
  "discount": {
    "amount_off": 1000,
    "type": "AMOUNT"
  },
  "tracking_id": "track_uP6K80aZLxpKYZWvVIVW4A=="
}


4. Customers API


Example GET customer

curl -X GET \
  -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
  -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c" \
  -H "Content-Type: application/json" \
  https://api.voucherify.io/v1/customers/cust_lYv4yFtT7SGzx81oYpzCntIi

Ressponse

{  
  "id":"cust_lYv4yFtT7SGzx81oYpzCntIi",
  "source_id":"your-tracking-id",
  "name":"John Doe",
  "email":"email@example.com",
  "address": {
    "city": null,
    "country": null,
    "line_1": null,
    "line_2": null,
    "postal_code": null,
    "state": null
  },
  "summary": {
    "redemptions": {
      "total_redeemed": 0,
      "total_failed": 0,
      "total_succeeded": 0,
      "total_rolled_back": 0,
      "total_rollback_failed": 0,
      "total_rollback_succeeded": 0,
      "gift": {
        "redeemed_amount": 0,
        "amount_to_go": 0
      }
    },
    "orders": {
      "total_amount": 0,
      "total_count": 0,
      "average_amount": 0,
      "last_order_amount": 0,
      "last_order_date": null
    }
  },
  "loyalty": {
    "points": 0,
    "referred_customers": 0
  },
  "description":"Premium user, ACME Inc.",
  "metadata":{  
    "lang":"en"
  },
  "created_at":"2016-11-17T15:23:15Z",
  "object":"customer"
}

```
