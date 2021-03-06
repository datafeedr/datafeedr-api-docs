# Requests

When making Requests to the Datafeedr API please ensure your Request meets these requirements:

1. **HTTPS Only** - The Datafeedr API will only respond to secured communication over HTTPS. HTTP Requests will be sent a Response containing a `400` HTTP status code.

1. **POST Only** - All Requests to the API should be `POST` Requests.

1. **JSON Only** - All Request parameters should be in [JSON](https://en.wikipedia.org/wiki/JSON) format.

1. **Body Only** - All Request parameters should be sent in the `body` of the `POST`.


## Request Properties

All Requests require an **ACCESS ID** and an **ACCESS KEY**. See [Requirements](#requirements).

Property | Type | Description
---|---|---
`aid` | string | Datafeedr API ACCESS ID.
`akey` | string | Datafeedr API ACCESS KEY.

## Request Example

```shell
curl --request POST \
	--url https://api.datafeedr.com/search \
	--data '{
	"aid": "ACCESS_ID",
	"akey": "ACCESS_KEY",
	"query": [
		"name LIKE rock climbing harness"
	]
}'
```

```php
<?php

$url = "https://api.datafeedr.com/search";

$data = json_encode([
    'aid'   => 'ACCESS_ID',
    'akey'  => 'ACCESS_KEY',
    'query' => [
        'name LIKE rock climbing harness'
    ]
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

url = "https://api.datafeedr.com/search"

data = {
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY",
    "query": [
        "name LIKE rock climbing harness"
    ]
}

response = requests.post(url, json=data)
print(response.json())
```

```javascript
var axios = require('axios');

var url = "https://api.datafeedr.com/search";

var data = {
    "aid": "ACCESS_ID",
    "akey": "ACCESS_KEY",
    "query": [
        "name LIKE rock climbing harness"
    ]
};

axios.post(url, data).then(function (response) {
    console.log(response.data)
});
```

Here is an example of a simple product search Request which includes an **ACCESS ID** and an **ACCESS KEY** and a [`Query`](#query-object) Object containing one [Condition](#conditions).
