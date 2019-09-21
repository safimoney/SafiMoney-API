## **SafiMoney API Reference Guide**

SafiMoney is the the easiest way to accept, process and disburse  payments. SafiMoney APIs are completely Non-RESTful and all our responses are returned in JSON.

SafiMoney APIs are opened only for **Business and Partner Wallets.**

### API Endpoint

The URL of all our APIs are: https://api.safimoney.com/api/v2.

------

### Get credentials

To use SafiMoney API, you can generate API credentials from your Wallet Dashboard.

1. Login into your [SafiMoney Account](https://app.safimoney.com.), if you don't  have an account you can click on the register option.
2. In [Wallet tab](https://app.safimoney.com/wallet), click on the [API Credentials](https://app.safimoney.com/wallet/api-credentials) link.
3. On [API Credentials Page](https://app.safimoney.com/wallet/api-credentials), click on Create New Access Keys button to generate API Credentials.
4. After generating the keys from the Dashboard, you must download and save them **securely**. If you lose access to your key secret, you can generate a new API credential from your dashboard and update all your integration.

![](images/api_credentials.gif)



An API credential consists of a Key and a Secret.

> **Note**:
> The API Key is used to initiate payments, and can be exposed publicly. 
>
> The API Key Secret is like your password, and should not be exposed.

------

### 	Get an access token

- SafiMoney use **Bearer authentication** (also called **token authentication**) to authenticate all server-side requests. You must send this token in the `Authorization` header when making requests.

```cURL
Authorization: Bearer <token>
```

- To create token you need to use these Parameters:

```cURL
Authorization: Bearer {
    "namespace":"transaction", 
    "action":"get",
    "key":"32129790-db73-11e9-9ffa-4731a16a8d7f",
    "timestamp":1568971542018,
    "hash":"79c1fea765a4e21f5b8948c9ba2866e81f30dc8eed80baedc9a133cd5079a7d6"
}
```

| Bearer Token Parameters | Description                                                  |                                                              |
| :---------------------- | :----------------------------------------------------------- | ------------------------------------------------------------ |
| namespace               | namespace will represent the entity in which we want to perform | *namespace is case sensitive*                                |
| action                  | The action you want to perform e.g cashIn, cashOut           | *action is case sensitive*                                   |
| key                     | Your API Key                                                 |                                                              |
| timestamp               | Timestamp must be UTC timestamp and it should be incremental.              The timestamp is valid for only 60 seconds. |                                                              |
| hash                    | To create hash follow the next point                         | *[SHA256](https://en.wikipedia.org/wiki/SHA-2) is used to create hash* |



- A hash is made up out of an encrypted JSON object, consisting of a `namespace`, `action`, `key`, `timestamp` and `api_secret` .

  - plain hash = add namespace + action + api_key + timestamp + api_secret.

  - encrypt plain hash with SHA25 .

  - add encrypted hash in bearer token. 

    

​         ![](/home/yasmin/Downloads/so5LnYIY2Cu2JOP2h9WXmag.png) 



------

### 	Make API calls

- The all API calls are post request and will be done on https://api.safimoney.com/api/v2.
- Also, include your access token to prove your identity and access protected resources.

- A sample example of API Call which include a *bearer token* in the `Authorization` request header.

- Other request parameters, can be send in form-data content type. 

  - **Java**

    ```java
    OkHttpClient client = new OkHttpClient();
    
    MediaType mediaType = MediaType.parse("multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW");
    RequestBody body = RequestBody.create(mediaType, "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"id\"\r\n\r\n1000000000001357\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--");
    Request request = new Request.Builder()
      .url("https://api.safimoney.com/api/v2")
      .post(body)
      .addHeader("content-type", "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW")
      .addHeader("Authorization", "Bearer {"namespace":"transaction","action":"get","key":"32129790-db73-11e9-9ffa-4731a16a8d7f","timestamp":1568971542018,"hash":"79c1fea765a4e21f5b8948c9ba2866e81f30dc8eed80baedc9a133cd5079a7d6"}")
      .addHeader("User-Agent", "PostmanRuntime/7.16.3")
      .addHeader("Accept", "*/*")
      .addHeader("Cache-Control", "no-cache")
      .addHeader("Postman-Token", "2a9e477b-bb12-4c2e-9c05-a41a86c2ad85,0361ba63-9997-438b-bd07-d82a37defec2")
      .addHeader("Host", "api.safimoney.com")
      .addHeader("Content-Type", "multipart/form-data; boundary=--------------------------654348294703965233088224")
      .addHeader("Accept-Encoding", "gzip, deflate")
      .addHeader("Content-Length", "173")
      .addHeader("Connection", "keep-alive")
      .addHeader("cache-control", "no-cache")
      .build();
    
    Response response = client.newCall(request).execute();
    ```

    

  - **cURL**

    ```php
    <?php
    
    $curl = curl_init();
    
    curl_setopt_array($curl, array(
      CURLOPT_URL => "https://api.safimoney.com/api/v2",
      CURLOPT_RETURNTRANSFER => true,
      CURLOPT_ENCODING => "",
      CURLOPT_MAXREDIRS => 10,
      CURLOPT_TIMEOUT => 30,
      CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
      CURLOPT_CUSTOMREQUEST => "POST",
      CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"id\"\r\n\r\n1000000000001357\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
      CURLOPT_HTTPHEADER => array(
        "Accept: */*",
        "Accept-Encoding: gzip, deflate",
        "Authorization: Bearer {"namespace":"transaction","action":"get","key":"32129790-db73-11e9-9ffa-4731a16a8d7f","timestamp":1568971542018,"hash":"79c1fea765a4e21f5b8948c9ba2866e81f30dc8eed80baedc9a133cd5079a7d6"}",
        "Cache-Control: no-cache",
        "Connection: keep-alive",
        "Content-Length: 173",
        "Content-Type: multipart/form-data; boundary=--------------------------654348294703965233088224",
        "Host: api.safimoney.com",
        "Postman-Token: 2a9e477b-bb12-4c2e-9c05-a41a86c2ad85,9577c06f-b6fd-473f-88d6-3b888e448738",
        "User-Agent: PostmanRuntime/7.16.3",
        "cache-control: no-cache",
        "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
      ),
    ));
    
    $response = curl_exec($curl);
    $err = curl_error($curl);
    
    curl_close($curl);
    
    if ($err) {
      echo "cURL Error #:" . $err;
    } else {
      echo $response;
    }
    ```

    

  - **JavaScript**

    ```javascript, php
    var form = new FormData();
    form.append("id", "1000000000001357");
    
    var settings = {
      "async": true,
      "crossDomain": true,
      "url": "https://api.safimoney.com/api/v2",
      "method": "POST",
      "headers": {
        "Authorization": "Bearer {\"namespace\":\"transaction\",\"action\":\"get\",\"key\":\"32129790-db73-11e9-9ffa-4731a16a8d7f\",\"timestamp\":1568971542018,\"hash\":\"79c1fea765a4e21f5b8948c9ba2866e81f30dc8eed80baedc9a133cd5079a7d6\"}",
        "User-Agent": "PostmanRuntime/7.16.3",
        "Accept": "*/*",
        "Cache-Control": "no-cache",
        "Postman-Token": "2a9e477b-bb12-4c2e-9c05-a41a86c2ad85,03659b3a-f6ff-4b54-9252-ba421b1d2b8c",
        "Host": "api.safimoney.com",
        "Content-Type": "multipart/form-data; boundary=--------------------------654348294703965233088224",
        "Accept-Encoding": "gzip, deflate",
        "Content-Length": "173",
        "Connection": "keep-alive",
        "cache-control": "no-cache"
      },
      "processData": false,
      "contentType": false,
      "mimeType": "multipart/form-data",
      "data": form
    }
    
    $.ajax(settings).done(function (response) {
      console.log(response);
    });
    ```


------

### 	API Response

```json
{
    "request": {},
    "status": "200",
    "data": null,
    "error": null
}			
```

SafiMoney API response will be in JSON format. The response shows the below details:

| Response | Description                                                  |
| -------- | ------------------------------------------------------------ |
| request  | all the parameters submitted by you in the request will be there. |
| status   | status of response.                                          |
| data     | data of response, its **default value is null.**             |
| error    | error of response, its **default value is null.**            |



- The response from SafiMoney will contain both data and error object.

- First you need to check Error object, if its empty then go with Data object.

  ------

  #### Errors

  - For error detail, check error object from the response.

  - ```json
    {
        "request": {
            "id": "100000000000135"
        },
        "status": 0,   
        "data": null,
        "error": {
            "title": "Error !",
            "message": "No transaction found",
            "remedy": "Please Retry or Report to Support Team !",
            "validation": [],
            "data": null
        }
    }
    ```

  - The error Response contains following parameters :

    | Error Response | Description              |
    | -------------- | ------------------------ |
    | title          | Title of the error       |
    | message        | Message of the error     |
    | remedy         | Remedy of the error      |
    | validation     | Validation related error |
    | data           | any error related data   |

    

  - Validation Error (e.g., a required parameter was omitted or have invalid values etc.) will be available on validation object.

  - The validation error will contain the object which will have field name as key and error as value.

    ```json
    {
        "request": {
            "id" : null
        },
        "status": 400,
        "data": null,
        "error": {
            "title": "Error !",
            "message": "The id field is required.",
            "remedy": "Please Retry or Report to Support Team !",
            "validation": {
                "id": [
                    "The id field is required."
                ]
            },
            "data": null
        }
    }
    ```

    

  

