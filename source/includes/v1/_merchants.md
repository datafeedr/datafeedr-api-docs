# Merchants


The `merchants` endpoint returns [`Merchant`](#merchant-properties) related data.


## Merchant Properties

The `Merchant` Object contains information about a single merchant.


Property | Type | Description
---|---|---
`_id` | integer | Merchant ID.
`name` | string | Merchant name.
`source` | string | Affiliate network name.
`source_id` | integer | Affiliate network ID.
`product_count`  | integer | Total number of records for this merchant.




## Get all merchants

> Example Merchant Request

```shell
curl --request POST \
  --url https://api.datafeedr.com/merchants \
  --data '{
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY"
}'
```

```php
<?php

$url = "https://api.datafeedr.com/merchants";

$data = json_encode([
    'aid'  => 'ACCESS_ID',
    'akey' => 'ACCESS_KEY'
]);

$ch = curl_init($url);
curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => 1,
    CURLOPT_HTTPHEADER     => ['Content-Type: application/json'],
    CURLOPT_POSTFIELDS     => $data
]);

$response = curl_exec($ch);
curl_close($ch);

print_r(json_decode($response));
```

```python
import requests

url = "https://api.datafeedr.com/merchants"

data = {
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY"
}

response = requests.post(url, json=data)
print(response.json())
```

```javascript
var axios = require('axios');

var url = "https://api.datafeedr.com/merchants";

var data = {
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY"
};

axios.post(url, data).then(function (response) {
    console.log(response.data)
});
```


> Example Merchant Response

```json
{
    "status": {
        "network_count": 173,
        "plan_id": 10300,
        "user_id": 190,
        "max_total": 10000,
        "merchant_count": 57971,
        "max_requests": 100000,
        "bill_day": 16,
        "request_count": 4367,
        "product_count": 456469693,
        "max_length": 100
    },
    "merchants": [
        {
            "source_id": 8,
            "source": "ShareASale Coupons/Deals",
            "product_count": 1,
            "_id": 51862,
            "name": "'corePHP'"
        },
        {
            "source_id": 120,
            "source": "Commission Junction Coupons/Deals",
            "product_count": 0,
            "_id": 62415,
            "name": "(eUK) eUKhost Ltd"
        },
        {
            "source_id": 3,
            "source": "Commission Junction",
            "product_count": 4,
            "_id": 52287,
            "name": "(s) Strikingly"
        },
        {
            "source_id": 120,
            "source": "Commission Junction Coupons/Deals",
            "product_count": 0,
            "_id": 62490,
            "name": "(WHUK) WebHosting UK COM Ltd."
        },
        {
            "source_id": 123,
            "source": "Avangate",
            "product_count": 0,
            "_id": 19580,
            "name": "++Technologies"
        },

 		// ...

        {
            "source_id": 700,
            "source": "Shopello Sweden",
            "product_count": 0,
            "_id": 64937,
            "name": "ÖVERLEVNADSBUTIKEN"
        },
        {
            "source_id": 15,
            "source": "Partner-ads",
            "product_count": 11445,
            "_id": 61983,
            "name": "Økologisk Supermarked"
        },
        {
            "source_id": 701,
            "source": "Shopello Denmark",
            "product_count": 0,
            "_id": 66150,
            "name": "Økologisk-Supermarked"
        },
        {
            "source_id": 15,
            "source": "Partner-ads",
            "product_count": 0,
            "_id": 52617,
            "name": "Økoshoppen.dk"
        },
        {
            "source_id": 26,
            "source": "Webgains Denmark",
            "product_count": 0,
            "_id": 32591,
            "name": "Økozonen"
        }
    ],
    "version": "0.2",
    "length": 57971,
    "time": 10
}
```

`POST https://api.datafeedr.com/merchants`

Get all merchants.

<aside class="notice">
<strong>WARNING:</strong> A Request to this endpoint without any filters in place will take a long time and return over 50,000 results. This is NOT RECOMMENDED.
</aside>


### Request Properties

There are no additional properties required for this Request.


### Response Properties

Property | Type | Description
---|---|---
`merchants` | array | Array of [`Merchant`](#merchant-properties) Objects.
`length` | integer | Number of merchants returned.
`status` | object | [`Status`](#status-properties) Object.
`time` | integer | Time spent processing the API request (in milliseconds).
`version` | string | The current version of the API.












## Get merchants by network

> Example Merchant Request

```shell
curl --request POST \
  --url https://api.datafeedr.com/merchants \
  --data '{
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY",
    "fields": ["name", "product_count", "source"],
    "source_ids": [6, 126]
}'
```

```php
<?php

$url = "https://api.datafeedr.com/merchants";

$data = json_encode([
    'aid'        => 'ACCESS_ID',
    'akey'       => 'ACCESS_KEY',
    'fields'     => [
        'name',
        'product_count',
        'source'
    ],
    'source_ids' => [6, 126]
]);

$ch = curl_init($url);
curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => 1,
    CURLOPT_HTTPHEADER     => ['Content-Type: application/json'],
    CURLOPT_POSTFIELDS     => $data
]);

$response = curl_exec($ch);
curl_close($ch);

print_r(json_decode($response));
```

```python
import requests

url = "https://api.datafeedr.com/merchants"

data = {
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY",
    "fields": ["name", "product_count", "source"],
    "source_ids": [6, 126]
}

response = requests.post(url, json=data)
print(response.json())
```

```javascript
var axios = require('axios');

var url = "https://api.datafeedr.com/merchants";

var data = {
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY",
    "fields": ["name", "product_count", "source"],
    "source_ids": [6, 126]
};

axios.post(url, data).then(function (response) {
    console.log(response.data)
});
```


> Example Merchant Response

```json
{
    "status": {
        "network_count": 173,
        "plan_id": 10300,
        "user_id": 190,
        "max_total": 10000,
        "merchant_count": 57971,
        "max_requests": 100000,
        "bill_day": 16,
        "request_count": 4366,
        "product_count": 456469693,
        "max_length": 100
    },
    "merchants": [
        {
            "product_count": 0,
            "source": "ShareASale",
            "_id": 32023,
            "name": "1 Louder Inc"
        },
        {
            "product_count": 0,
            "source": "AvantLink US",
            "_id": 40527,
            "name": "100 Percent Pure"
        },
        {
            "product_count": 6919,
            "source": "ShareASale",
            "_id": 1269,
            "name": "123 REFILLS"
        },
        {
            "product_count": 0,
            "source": "AvantLink US",
            "_id": 80554,
            "name": "123 Refills"
        },
        {
            "product_count": 1288,
            "source": "ShareASale",
            "_id": 1282,
            "name": "123Posters.com, Inc."
        },

        // ...

        {
            "product_count": 0,
            "source": "ShareASale",
            "_id": 17583,
            "name": "zorem corp"
        },
        {
            "product_count": 0,
            "source": "AvantLink US",
            "_id": 48637,
            "name": "ZOZI"
        },
        {
            "product_count": 0,
            "source": "ShareASale",
            "_id": 96436,
            "name": "Zulily"
        },
        {
            "product_count": 0,
            "source": "ShareASale",
            "_id": 75932,
            "name": "zulily"
        },
        {
            "product_count": 0,
            "source": "AvantLink US",
            "_id": 23729,
            "name": "Zupplements"
        }
    ],
    "version": "0.2",
    "length": 2110,
    "time": 23
}
```

`POST https://api.datafeedr.com/merchants`

Get merchants of specific networks and limit the fields returned for each merchant.



### Request Properties

Property | Value | Type | Required
---|---|---|---|---
`fields` | Array of `Merchant` properties to include in the results. | `["name","source","..."]` | No
`source_ids` | Array of network IDs to filter results by. | `[4,6,9,...]` | No


### Response Properties

Property | Type | Description
---|---|---
`merchants` | array | Array of [`Merchant`](#merchant-properties) Objects.
`length` | integer | Number of merchants returned.
`status` | object | [`Status`](#status-properties) Object.
`time` | integer | Time spent processing the API request (in milliseconds).
`version` | string | The current version of the API.









