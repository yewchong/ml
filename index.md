---
title: BTSE Spot API
language_tabs:
  - shell: Shell
  - java: Java
  - python: Python
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v3.6.6 -->

<section>
<h1 id="btse-spot-api">BTSE Spot API v3.0.1</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

# Overview
## Generating API Key
You will need to create an API key on the BTSE platform before you can use authenticated APIs. To create API keys, you can follow the steps below:
1. Login with your username / email and password into the BTSE website
2. Click on “Account” on the top right hand corner
3. Select the API tab
4. Click on “New API” button to create an API key and passphrase. (Note: the passphrase will only appear once)
5. Use your API key and passphrase to construct a signature.

Base URLs:

* undefined - <a href="//api.btse.com/">//api.btse.com/</a>

 License: btse.com
</section>

<section>

# Authentication

* API Key (btse-api)
    - Parameter Name: **btse-api**, in: header. 

* API Key (btse-nonce)
    - Parameter Name: **btse-nonce**, in: header. 

* API Key (btse-sign)
    - Parameter Name: **btse-sign**, in: header. 

</section>

<section>
<h1 id="btse-spot-api-authenticated-endpoints">Authenticated Endpoints</h1>

Support for the Authenticated API.

<section>

## getAllOpenOrders

<a id="opIdgetAllOpenOrdersUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/open_orders?symbol=string \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/open_orders?symbol=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/open_orders', params={
  'symbol': 'string'
}, headers = headers)

print r.json()

```

`GET /spot/api/v3/open_orders`

<section>
<h3 id="getallopenorders-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|true|symbol|

</section>

> Example responses

> 200 Response

```json
{
  "cancelDuration": 0,
  "filledSize": 3,
  "orderID": "string",
  "orderType": 0,
  "orderValue": 20.625,
  "pegPriceDeviation": 3,
  "pegPriceMax": 0,
  "pegPriceMin": 0,
  "price": 6875,
  "side": "BUY",
  "size": 4,
  "symbol": "string",
  "timestamp": 0,
  "trailValue": 0,
  "triggerOrder": false,
  "triggerOrderType": 1001,
  "triggerOriginalPrice": 0,
  "triggerPrice": 0,
  "triggerStopPrice": 0,
  "triggerTrailingStopDeviation": 0,
  "triggered": true
}
```

<section>
<h3 id="getallopenorders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Get all of the pending order.|[OpenOrderMdl](#schemaopenordermdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## placeOrder

<a id="opIdplaceOrderUsingPOST"></a>

> Code samples

```shell
# You can also use wget
curl -X POST /api.btse.com/spot/api/v3/order \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/order");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.post('/api.btse.com/spot/api/v3/order', params={

}, headers = headers)

print r.json()

```

`POST /spot/api/v3/order`

> Body parameter

```json
{
  "postOnly": false,
  "price": 7010,
  "side": "BUY",
  "size": 1,
  "stopPrice": 0,
  "symbol": "BTC-USD",
  "time_in_force": "GTC",
  "trailValue": 0,
  "triggerPrice": 0,
  "txType": "LIMIT",
  "type": "LIMIT"
}
```

<section>
<h3 id="placeorder-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[OrderRequest](#schemaorderrequest)|true|Support for Limit order, Market order, OCO order.|

</section>

> Example responses

> 200 Response

```json
{
  "message": "string",
  "orderID": "string",
  "orderType": 76,
  "price": 0,
  "side": "BUY",
  "size": 4,
  "status": 0,
  "stopPrice": 8300,
  "symbol": "BTC-USD",
  "timestamp": 1576812000872,
  "trigger": true,
  "triggerPrice": 8300
}
```

<section>
<h3 id="placeorder-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Create an limit order.|[OrderResp](#schemaorderresp)|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## cancelOrder

<a id="opIdcancelOrderUsingDELETE"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE /api.btse.com/spot/api/v3/order?symbol=string \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/order?symbol=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.delete('/api.btse.com/spot/api/v3/order', params={
  'symbol': 'string'
}, headers = headers)

print r.json()

```

`DELETE /spot/api/v3/order`

<section>
<h3 id="cancelorder-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|true|symbol|
|orderID|query|string|false|orderID|

</section>

> Example responses

> 200 Response

```json
[
  {
    "message": "string",
    "orderID": "string",
    "orderType": 76,
    "price": 0,
    "side": "BUY",
    "size": 4,
    "status": 0,
    "stopPrice": 8300,
    "symbol": "BTC-USD",
    "timestamp": 1576812000872,
    "trigger": true,
    "triggerPrice": 8300
  }
]
```

<section>
<h3 id="cancelorder-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Delete an pending order.|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

<h3 id="cancelorder-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrderResp](#schemaorderresp)]|false|none|[/api/v3/order/limit]|
|» OrderResp|[OrderResp](#schemaorderresp)|false|none|/api/v3/order/limit|
|»» message|string|true|none|The order response message.|
|»» orderID|string|true|none|The order id .|
|»» orderType|integer(int32)|true|none|76: limit order, 77: market order|
|»» price|number(double)|true|none|order price|
|»» side|string|true|none|Original order size|
|»» size|number(double)|true|none|Original order size|
|»» status|integer(int32)|true|none|2:ORDER_INSERTED = 2, 6: Order cancelled|
|»» stopPrice|number(double)|true|none|The Stop price.|
|»» symbol|string|true|none|symbol , ex:BTC-USD, ETH-USD|
|»» timestamp|integer(int64)|true|none|The order timestamp .|
|»» trigger|boolean|true|none|The trigger or not.|
|»» triggerPrice|number(double)|true|none|The trigger price.|

#### Enumerated Values

|Property|Value|
|---|---|
|side|BUY/SELL|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getFees

<a id="opIdgetFeesUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/user/fees \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/user/fees");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/user/fees', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/user/fees`

<section>
<h3 id="getfees-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|false|symbol|

</section>

> Example responses

> 200 Response

```json
{
  "makerFee": 0,
  "symbol": "BTC-USD",
  "takerFee": 0
}
```

<section>
<h3 id="getfees-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of most user fees|[FeesMdl](#schemafeesmdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getUserAllOpenOrders

<a id="opIdgetUserAllOpenOrdersUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/user/open_orders?symbol=string \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/user/open_orders?symbol=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/user/open_orders', params={
  'symbol': 'string'
}, headers = headers)

print r.json()

```

`GET /spot/api/v3/user/open_orders`

<section>
<h3 id="getuserallopenorders-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|true|symbol|

</section>

> Example responses

> 200 Response

```json
{
  "cancelDuration": 0,
  "filledSize": 3,
  "orderID": "string",
  "orderType": 0,
  "orderValue": 20.625,
  "pegPriceDeviation": 3,
  "pegPriceMax": 0,
  "pegPriceMin": 0,
  "price": 6875,
  "side": "BUY",
  "size": 4,
  "symbol": "string",
  "timestamp": 0,
  "trailValue": 0,
  "triggerOrder": false,
  "triggerOrderType": 1001,
  "triggerOriginalPrice": 0,
  "triggerPrice": 0,
  "triggerStopPrice": 0,
  "triggerTrailingStopDeviation": 0,
  "triggered": true
}
```

<section>
<h3 id="getuserallopenorders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Get all of the pending order.|[OpenOrderMdl](#schemaopenordermdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getTradeHistory

<a id="opIdgetTradeHistoryUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/user/trade_history \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/user/trade_history");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/user/trade_history', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/user/trade_history`

<section>
<h3 id="gettradehistory-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|false|symbol|
|startTime|query|integer(int64)|false|startTime|
|endTime|query|integer(int64)|false|endTime|
|beforeSerialId|query|integer(int64)|false|beforeSerialId|
|afterSerialId|query|integer(int64)|false|afterSerialId|
|count|query|integer(int32)|false|count|
|includeOld|query|boolean|false|includeOld|

</section>

> Example responses

> 200 Response

```json
{
  "price": 0,
  "serialId": 0,
  "side": "string",
  "size": 0,
  "symbol": "string",
  "timestamp": 0
}
```

<section>
<h3 id="gettradehistory-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Get the trades with user.|[RecentTradeMd](#schemarecenttrademd)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getWallets

<a id="opIdgetWalletsUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/user/wallet \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/user/wallet");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/user/wallet', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/user/wallet`

> Example responses

> 200 Response

```json
{
  "available": 520.52,
  "currency": "USD",
  "total": 5566.5566
}
```

<section>
<h3 id="getwallets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Get the wallet info with user.|[FiatMdl](#schemafiatmdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getWalletHistory

<a id="opIdgetWalletHistoryUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/user/wallet_history \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/user/wallet_history");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/user/wallet_history', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/user/wallet_history`

<section>
<h3 id="getwallethistory-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|startTime|query|integer(int64)|false|startTime|
|endTime|query|integer(int64)|false|endTime|
|count|query|integer(int32)|false|count|
|currency|query|string|false|currency|

</section>

> Example responses

> 200 Response

```json
{
  "amount": 21.35823825,
  "currency": "USD",
  "description": "string",
  "fees": 0.06,
  "orderId": 20181213000239,
  "status": 10,
  "timestamp": 1571630174639,
  "type": 1,
  "username": "btseUser",
  "wallet": "SPOT@"
}
```

<section>
<h3 id="getwallethistory-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Get the wallet history with user.|[WalletHistoryMdl](#schemawallethistorymdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

</section>

<section>
<h1 id="btse-spot-api-public-endpoints">Public Endpoints</h1>

Support for the public API.

<section>

## getPublicMarketSummary

<a id="opIdgetPublicMarketSummaryUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/market_summary?symbol=string \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/market_summary?symbol=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/market_summary', params={
  'symbol': 'string'
}, headers = headers)

print r.json()

```

`GET /spot/api/v3/market_summary`

<section>
<h3 id="getpublicmarketsummary-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|true|symbol|

</section>

> Example responses

> 200 Response

```json
{
  "active": false,
  "availableSettlement": [
    "string"
  ],
  "base": "USD",
  "closeTime": 0,
  "contractEnd": 0,
  "contractSize": 0,
  "contractStart": 0,
  "fundingRate": 0,
  "futures": true,
  "high24Hr": 7396.5,
  "highestBid": 7252.5,
  "inactiveTime": 0,
  "last": 7077.5,
  "low24Hr": 7171,
  "lowestAsk": 7254.5,
  "maxOrderSize": 0,
  "maxPosition": 0,
  "maxRiskLimit": 0,
  "minOrderSize": 0,
  "minPriceIncrement": 0,
  "minRiskLimit": 0,
  "minSizeIncrement": 0,
  "minValidPrice": 0,
  "openInterest": 0,
  "openInterestUSD": 0,
  "openTime": 0,
  "percentageChange": 1.5809,
  "quote": "BTC",
  "size": 0.001,
  "startMatching": 0,
  "symbol": "BTC-USD",
  "timeBasedContract": false,
  "volume": 16442583.015
}
```

<section>
<h3 id="getpublicmarketsummary-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of most market summary|[MarketSummaryMdl](#schemamarketsummarymdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getOhlcv

<a id="opIdgetOhlcvUsingGET_1"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/ohlcv?symbol=string \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/ohlcv?symbol=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/ohlcv', params={
  'symbol': 'string'
}, headers = headers)

print r.json()

```

`GET /spot/api/v3/ohlcv`

<section>
<h3 id="getohlcv-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|true|symbol|
|start|query|integer(int64)|false|start|
|end|query|integer(int64)|false|end|
|resolution|query|integer(int32)|false|resolution|

</section>

> Example responses

> 200 Response

```json
[
  {}
]
```

<section>
<h3 id="getohlcv-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ohlcv|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

<h3 id="getohlcv-responseschema">Response Schema</h3>

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getOrderbookInfor

<a id="opIdgetOrderbookInforUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/orderbook \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/orderbook");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/orderbook', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/orderbook`

<section>
<h3 id="getorderbookinfor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|false|symbol|
|group|query|integer(int32)|false|group|
|limit_bids|query|integer(int32)|false|limit_bids|
|limit_asks|query|integer(int32)|false|limit_asks|

</section>

> Example responses

> 200 Response

```json
{
  "buyQuote": [],
  "sellQuote": [],
  "symbol": "BTC-USD",
  "timestamp": 1575952670089
}
```

<section>
<h3 id="getorderbookinfor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|"List of OrderBook|[OrderbookMdl](#schemaorderbookmdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getOrderbookL2Infor

<a id="opIdgetOrderbookL2InforUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/orderbook/L2 \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/orderbook/L2");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/orderbook/L2', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/orderbook/L2`

<section>
<h3 id="getorderbookl2infor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|false|symbol|
|depth|query|integer(int32)|false|depth|

</section>

> Example responses

> 200 Response

```json
{
  "buyQuote": [],
  "sellQuote": [],
  "symbol": "BTC-USD",
  "timestamp": 1575952670089
}
```

<section>
<h3 id="getorderbookl2infor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|"List of OrderBook|[OrderbookMdl](#schemaorderbookmdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getPrice

<a id="opIdgetPriceUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/price \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/price");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/price', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/price`

<section>
<h3 id="getprice-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|false|symbol|

</section>

> Example responses

> 200 Response

```json
{
  "indexPrice": 7217.1109184696,
  "lastPrice": 7215.1109184696,
  "markPrice": 7216.1109184696,
  "symbol": "BTC-USD"
}
```

<section>
<h3 id="getprice-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of most price|[PriceMdl](#schemapricemdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getTime

<a id="opIdgetTimeUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/time \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/time");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/time', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/time`

> Example responses

> 200 Response

```json
{
  "epoch": 1578295405,
  "iso": "2020-01-06T07:23:25.719Z"
}
```

<section>
<h3 id="gettime-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Get the system time.|[TimeMdl](#schematimemdl)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

<section>

## getTrades

<a id="opIdgetTradesUsingGET"></a>

> Code samples

```shell
# You can also use wget
curl -X GET /api.btse.com/spot/api/v3/trades \
  -H 'Accept: application/json;charset=UTF-8'

```

```java
URL obj = new URL("/api.btse.com/spot/api/v3/trades");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```python
import requests
headers = {
  'Accept': 'application/json;charset=UTF-8'
}

r = requests.get('/api.btse.com/spot/api/v3/trades', params={

}, headers = headers)

print r.json()

```

`GET /spot/api/v3/trades`

<section>
<h3 id="gettrades-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|false|symbol|
|startTime|query|integer(int64)|false|startTime|
|endTime|query|integer(int64)|false|endTime|
|beforeSerialId|query|integer(int64)|false|beforeSerialId|
|afterSerialId|query|integer(int64)|false|afterSerialId|
|count|query|integer(int32)|false|count|
|includeOld|query|boolean|false|includeOld|

</section>

> Example responses

> 200 Response

```json
{
  "price": 0,
  "serialId": 0,
  "side": "string",
  "size": 0,
  "symbol": "string",
  "timestamp": 0
}
```

<section>
<h3 id="gettrades-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Get the trades without user.|[RecentTradeMd](#schemarecenttrademd)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[AppExceptionMdl](#schemaappexceptionmdl)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[AppExceptionMdl](#schemaappexceptionmdl)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|[AppExceptionMdl](#schemaappexceptionmdl)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[AppExceptionMdl](#schemaappexceptionmdl)|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[AppExceptionMdl](#schemaappexceptionmdl)|

</section>

<aside class="success">
This operation does not require authentication
</aside>

</section>

</section>

<section>

# Schemas

<section>
<h2 id="tocS_AppExceptionMdl">AppExceptionMdl</h2>
<!-- backwards compatibility -->
<a id="schemaappexceptionmdl"></a>
<a id="schema_AppExceptionMdl"></a>
<a id="tocSappexceptionmdl"></a>
<a id="tocsappexceptionmdl"></a>

```json
{
  "errorCode": -1,
  "message": "string",
  "status": 0
}

```

AppExceptionMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errorCode|integer(int32)|false|none|error code.|
|message|string|false|none|Error message.|
|status|integer(int32)|false|none|404:BAD REQUEST.|

</section>
</section>

<section>
<h2 id="tocS_CustomQuote">CustomQuote</h2>
<!-- backwards compatibility -->
<a id="schemacustomquote"></a>
<a id="schema_CustomQuote"></a>
<a id="tocScustomquote"></a>
<a id="tocscustomquote"></a>

```json
{
  "culmulativeTotal": "string",
  "price": "string",
  "size": "string"
}

```

CustomQuote

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|culmulativeTotal|string|false|none|none|
|price|string|false|none|none|
|size|string|false|none|none|

</section>
</section>

<section>
<h2 id="tocS_CustomResponse">CustomResponse</h2>
<!-- backwards compatibility -->
<a id="schemacustomresponse"></a>
<a id="schema_CustomResponse"></a>
<a id="tocScustomresponse"></a>
<a id="tocscustomresponse"></a>

```json
{
  "buyQuote": [
    {
      "culmulativeTotal": "string",
      "price": "string",
      "size": "string"
    }
  ],
  "currency": "string",
  "gain": 0,
  "gainVal": 0,
  "lastPrice": "string",
  "lastSize": 0,
  "name": "string",
  "pegIndexPrice": "string",
  "sellQuote": [
    {
      "culmulativeTotal": "string",
      "price": "string",
      "size": "string"
    }
  ],
  "symbol": "string",
  "timestamp": 0,
  "totalVolume": 0
}

```

CustomResponse

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|buyQuote|[[CustomQuote](#schemacustomquote)]|false|none|none|
|currency|string|false|none|none|
|gain|integer(int32)|false|none|none|
|gainVal|number(double)|false|none|none|
|lastPrice|string|false|none|none|
|lastSize|number(double)|false|none|none|
|name|string|false|none|none|
|pegIndexPrice|string|false|none|none|
|sellQuote|[[CustomQuote](#schemacustomquote)]|false|none|none|
|symbol|string|false|none|none|
|timestamp|integer(int64)|false|none|none|
|totalVolume|number(double)|false|none|none|

</section>
</section>

<section>
<h2 id="tocS_FeesMdl">FeesMdl</h2>
<!-- backwards compatibility -->
<a id="schemafeesmdl"></a>
<a id="schema_FeesMdl"></a>
<a id="tocSfeesmdl"></a>
<a id="tocsfeesmdl"></a>

```json
{
  "makerFee": 0,
  "symbol": "BTC-USD",
  "takerFee": 0
}

```

FeesMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|makerFee|number(double)|true|none|Maker fee percentage/$USD (scale: 10)|
|symbol|string|true|none|symbol|
|takerFee|number(double)|true|none|Taker fee percentage/$USD (scale: 10)|

</section>
</section>

<section>
<h2 id="tocS_FiatMdl">FiatMdl</h2>
<!-- backwards compatibility -->
<a id="schemafiatmdl"></a>
<a id="schema_FiatMdl"></a>
<a id="tocSfiatmdl"></a>
<a id="tocsfiatmdl"></a>

```json
{
  "available": 520.52,
  "currency": "USD",
  "total": 5566.5566
}

```

FiatMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|available|number(double)|true|none|currency short available|
|currency|string|true|none|currency currency|
|total|number(double)|true|none|currency short total|

</section>
</section>

<section>
<h2 id="tocS_MarketSummaryMdl">MarketSummaryMdl</h2>
<!-- backwards compatibility -->
<a id="schemamarketsummarymdl"></a>
<a id="schema_MarketSummaryMdl"></a>
<a id="tocSmarketsummarymdl"></a>
<a id="tocsmarketsummarymdl"></a>

```json
{
  "active": false,
  "availableSettlement": [
    "string"
  ],
  "base": "USD",
  "closeTime": 0,
  "contractEnd": 0,
  "contractSize": 0,
  "contractStart": 0,
  "fundingRate": 0,
  "futures": true,
  "high24Hr": 7396.5,
  "highestBid": 7252.5,
  "inactiveTime": 0,
  "last": 7077.5,
  "low24Hr": 7171,
  "lowestAsk": 7254.5,
  "maxOrderSize": 0,
  "maxPosition": 0,
  "maxRiskLimit": 0,
  "minOrderSize": 0,
  "minPriceIncrement": 0,
  "minRiskLimit": 0,
  "minSizeIncrement": 0,
  "minValidPrice": 0,
  "openInterest": 0,
  "openInterestUSD": 0,
  "openTime": 0,
  "percentageChange": 1.5809,
  "quote": "BTC",
  "size": 0.001,
  "startMatching": 0,
  "symbol": "BTC-USD",
  "timeBasedContract": false,
  "volume": 16442583.015
}

```

MarketSummaryMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|active|boolean|true|none|ex: BTC, ETH, USDT, etc.|
|availableSettlement|[string]|false|none|available settlement|
|base|string|true|none|symbol|
|closeTime|integer(int64)|false|none|close time|
|contractEnd|integer(int64)|false|none|contract end|
|contractSize|number(double)|false|none|contract size|
|contractStart|integer(int64)|false|none|contract start|
|fundingRate|number(double)|false|none|funding rate|
|futures|boolean|false|none|none|
|high24Hr|number(double)|true|none|The higher price in 24Hr|
|highestBid|number(double)|true|none|highest bid price.|
|inactiveTime|integer(int64)|false|none|inactive time|
|last|number(double)|true|none|last price.|
|low24Hr|number(double)|true|none|The lower price in 24Hr|
|lowestAsk|number(double)|true|none|lowest bid price.|
|maxOrderSize|number(double)|true|none|maximum order size|
|maxPosition|integer(int64)|false|none|max position|
|maxRiskLimit|integer(int32)|false|none|max risk limit|
|minOrderSize|number(double)|true|none|minimum order size|
|minPriceIncrement|number(double)|true|none|minimum price increment|
|minRiskLimit|integer(int32)|false|none|min risk limit|
|minSizeIncrement|number(double)|true|none|minimum size increment|
|minValidPrice|number(double)|true|none|minimum valid price|
|openInterest|number(double)|false|none|open interest|
|openInterestUSD|number(double)|false|none|open interest USD|
|openTime|integer(int64)|false|none|open time|
|percentageChange|number(double)|true|none|The order percentageChange.|
|quote|string|true|none|Support for USD.|
|size|number(double)|true|none|size = 0.001 means when you buy 1 unit contract, it actually equals 1 * 0.001 size in that market .|
|startMatching|integer(int64)|false|none|start matching|
|symbol|string|true|none|symbol.|
|timeBasedContract|boolean|false|none|timeBased contract|
|volume|number(double)|true|none|The order volume.|

</section>
</section>

<section>
<h2 id="tocS_OpenOrderMdl">OpenOrderMdl</h2>
<!-- backwards compatibility -->
<a id="schemaopenordermdl"></a>
<a id="schema_OpenOrderMdl"></a>
<a id="tocSopenordermdl"></a>
<a id="tocsopenordermdl"></a>

```json
{
  "cancelDuration": 0,
  "filledSize": 3,
  "orderID": "string",
  "orderType": 0,
  "orderValue": 20.625,
  "pegPriceDeviation": 3,
  "pegPriceMax": 0,
  "pegPriceMin": 0,
  "price": 6875,
  "side": "BUY",
  "size": 4,
  "symbol": "string",
  "timestamp": 0,
  "trailValue": 0,
  "triggerOrder": false,
  "triggerOrderType": 1001,
  "triggerOriginalPrice": 0,
  "triggerPrice": 0,
  "triggerStopPrice": 0,
  "triggerTrailingStopDeviation": 0,
  "triggered": true
}

```

OpenOrderMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|cancelDuration|integer(int64)|true|none|0: GTC, .|
|filledSize|number(double)|true|none|Filled order size.|
|orderID|string|true|none|The order id .|
|orderType|integer(int32)|true|none|76: limit order, 77: market order|
|orderValue|number(double)|true|none|Original order value(USD).|
|pegPriceDeviation|number(double)|true|none|Peg price deviation.|
|pegPriceMax|number(double)|true|none|Peg price max.|
|pegPriceMin|number(double)|true|none|Peg price min.|
|price|number(double)|true|none|The order price.|
|side|string|true|none|Original order size|
|size|number(double)|true|none|Original order size|
|symbol|string|true|none|The order symbol|
|timestamp|integer(int64)|true|none|The order timestamp .|
|trailValue|number(double)|true|none|The order trail value|
|triggerOrder|boolean|true|none|If trigger order didn't trigger yet, it return true.|
|triggerOrderType|integer(int32)|true|none|1001: Trigger stop loss, 1002: Trigger take profit.|
|triggerOriginalPrice|number(double)|true|none|The trigger original price .|
|triggerPrice|number(double)|true|none|The trigger price .|
|triggerStopPrice|number(double)|true|none|trigger stop price|
|triggerTrailingStopDeviation|number(double)|true|none|trigger trailing stop deviation|
|triggered|boolean|false|none|none|

<section>

#### Enumerated Values

|Property|Value|
|---|---|
|side|BUY/SELL|

</section>

</section>
</section>

<section>
<h2 id="tocS_OrderRequest">OrderRequest</h2>
<!-- backwards compatibility -->
<a id="schemaorderrequest"></a>
<a id="schema_OrderRequest"></a>
<a id="tocSorderrequest"></a>
<a id="tocsorderrequest"></a>

```json
{
  "postOnly": false,
  "price": 7010,
  "side": "BUY",
  "size": 1,
  "stopPrice": 0,
  "symbol": "BTC-USD",
  "time_in_force": "GTC",
  "trailValue": 0,
  "triggerPrice": 0,
  "txType": "LIMIT",
  "type": "LIMIT"
}

```

OrderRequest

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|postOnly|boolean|false|none|postOnly|
|price|number|false|none|The order price.|
|side|string|true|none|Original order size|
|size|number|true|none|The order size.|
|stopPrice|number|false|none|When using type: OCO, this parameter can not be null|
|symbol|string|false|none|none|
|time_in_force|string|false|none|GTC, IOC, FIVEMIN, HOUR, TWELVEHOUR, DAY, WEEK, MONTH|
|trailValue|number(double)|false|none|trail value|
|triggerPrice|number|false|none|When using type: OCO, this parameter can not be null|
|txType|string|false|none|LIMIT, STOP, TRIGGER|
|type|string|false|none|LIMIT, MARKET, OCO|

<section>

#### Enumerated Values

|Property|Value|
|---|---|
|side|BUY/SELL|
|time_in_force|IOC|
|time_in_force|GTC|
|time_in_force|FIVEMIN|
|time_in_force|HOUR|
|time_in_force|TWELVEHOUR|
|time_in_force|DAY|
|time_in_force|WEEK|
|time_in_force|MONTH|
|txType|LIMIT|
|txType|STOP|
|txType|TRIGGER|
|txType|OCO|
|txType|Limit|
|txType|Stop|
|txType|Trigger|
|txType|Oco|
|txType|limit|
|txType|stop|
|txType|trigger|
|txType|oco|
|type|LIMIT/MARKET/OCO|

</section>

</section>
</section>

<section>
<h2 id="tocS_OrderResp">OrderResp</h2>
<!-- backwards compatibility -->
<a id="schemaorderresp"></a>
<a id="schema_OrderResp"></a>
<a id="tocSorderresp"></a>
<a id="tocsorderresp"></a>

```json
{
  "message": "string",
  "orderID": "string",
  "orderType": 76,
  "price": 0,
  "side": "BUY",
  "size": 4,
  "status": 0,
  "stopPrice": 8300,
  "symbol": "BTC-USD",
  "timestamp": 1576812000872,
  "trigger": true,
  "triggerPrice": 8300
}

```

OrderResp

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message|string|true|none|The order response message.|
|orderID|string|true|none|The order id .|
|orderType|integer(int32)|true|none|76: limit order, 77: market order|
|price|number(double)|true|none|order price|
|side|string|true|none|Original order size|
|size|number(double)|true|none|Original order size|
|status|integer(int32)|true|none|2:ORDER_INSERTED = 2, 6: Order cancelled|
|stopPrice|number(double)|true|none|The Stop price.|
|symbol|string|true|none|symbol , ex:BTC-USD, ETH-USD|
|timestamp|integer(int64)|true|none|The order timestamp .|
|trigger|boolean|true|none|The trigger or not.|
|triggerPrice|number(double)|true|none|The trigger price.|

<section>

#### Enumerated Values

|Property|Value|
|---|---|
|side|BUY/SELL|

</section>

</section>
</section>

<section>
<h2 id="tocS_OrderbookMdl">OrderbookMdl</h2>
<!-- backwards compatibility -->
<a id="schemaorderbookmdl"></a>
<a id="schema_OrderbookMdl"></a>
<a id="tocSorderbookmdl"></a>
<a id="tocsorderbookmdl"></a>

```json
{
  "buyQuote": [],
  "sellQuote": [],
  "symbol": "BTC-USD",
  "timestamp": 1575952670089
}

```

OrderbookMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|buyQuote|[[PriceQuote](#schemapricequote)]|true|none|orderbook buy list .|
|sellQuote|[[PriceQuote](#schemapricequote)]|true|none|orderbook sell list .|
|symbol|string|true|none|symbol.|
|timestamp|integer(int64)|true|none|timestamp.|

</section>
</section>

<section>
<h2 id="tocS_PriceMdl">PriceMdl</h2>
<!-- backwards compatibility -->
<a id="schemapricemdl"></a>
<a id="schema_PriceMdl"></a>
<a id="tocSpricemdl"></a>
<a id="tocspricemdl"></a>

```json
{
  "indexPrice": 7217.1109184696,
  "lastPrice": 7215.1109184696,
  "markPrice": 7216.1109184696,
  "symbol": "BTC-USD"
}

```

PriceMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|indexPrice|number(double)|true|none|index price.|
|lastPrice|number(double)|true|none|lase price.|
|markPrice|number(double)|true|none|market price.|
|symbol|string|true|none|symbol.|

</section>
</section>

<section>
<h2 id="tocS_PriceQuote">PriceQuote</h2>
<!-- backwards compatibility -->
<a id="schemapricequote"></a>
<a id="schema_PriceQuote"></a>
<a id="tocSpricequote"></a>
<a id="tocspricequote"></a>

```json
{
  "culmulativeTotal": 0,
  "id": "string",
  "mode": "string",
  "parametersMap": {
    "property1": {},
    "property2": {}
  },
  "price": 0,
  "size": 0,
  "timestamp": 0
}

```

PriceQuote

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|culmulativeTotal|number(double)|false|none|none|
|id|string|false|none|none|
|mode|string|false|none|none|
|parametersMap|object|false|none|none|
|» **additionalProperties**|object|false|none|none|
|price|number(double)|false|none|none|
|size|number(double)|false|none|none|
|timestamp|integer(int64)|false|none|none|

</section>
</section>

<section>
<h2 id="tocS_RecentTradeMd">RecentTradeMd</h2>
<!-- backwards compatibility -->
<a id="schemarecenttrademd"></a>
<a id="schema_RecentTradeMd"></a>
<a id="tocSrecenttrademd"></a>
<a id="tocsrecenttrademd"></a>

```json
{
  "price": 0,
  "serialId": 0,
  "side": "string",
  "size": 0,
  "symbol": "string",
  "timestamp": 0
}

```

RecentTradeMd

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|price|number(double)|false|none|none|
|serialId|integer(int64)|false|none|none|
|side|string|false|none|none|
|size|number(double)|false|none|none|
|symbol|string|false|none|none|
|timestamp|integer(int64)|false|none|none|

</section>
</section>

<section>
<h2 id="tocS_TimeMdl">TimeMdl</h2>
<!-- backwards compatibility -->
<a id="schematimemdl"></a>
<a id="schema_TimeMdl"></a>
<a id="tocStimemdl"></a>
<a id="tocstimemdl"></a>

```json
{
  "epoch": 1578295405,
  "iso": "2020-01-06T07:23:25.719Z"
}

```

TimeMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|epoch|integer(int64)|true|none|The current system epoch time.|
|iso|string|true|none|ISO timestamp.|

</section>
</section>

<section>
<h2 id="tocS_WalletHistoryMdl">WalletHistoryMdl</h2>
<!-- backwards compatibility -->
<a id="schemawallethistorymdl"></a>
<a id="schema_WalletHistoryMdl"></a>
<a id="tocSwallethistorymdl"></a>
<a id="tocswallethistorymdl"></a>

```json
{
  "amount": 21.35823825,
  "currency": "USD",
  "description": "string",
  "fees": 0.06,
  "orderId": 20181213000239,
  "status": 10,
  "timestamp": 1571630174639,
  "type": 1,
  "username": "btseUser",
  "wallet": "SPOT@"
}

```

WalletHistoryMdl

<section>

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|amount|number(double)|true|none|amount|
|currency|string|true|none|currency|
|description|string|true|none|description|
|fees|number(double)|true|none|fees|
|orderId|string|true|none|orderId|
|status|string|true|none|USERCANCELED, COMPLETED, CANCELED, PENDING, PROCESSING, EXPIRED,CONTACT CS|
|timestamp|integer(int64)|true|none|timestamp|
|type|string|true|none|DEPOSIT, WITHDRAW, TRANSFER_IN ,TRANSFER_OUT,REFERRALEARNING|
|username|string|true|none|username|
|wallet|string|true|none|wallet|

</section>
</section>


