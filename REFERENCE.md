**SafiMoney API Reference Guide**

------

SafiMoney APIs 

**API Endpoint**

The URL of all our APIs are: https://api.safimoney.com/api/v2

**Authentication**

To use SafiMoney APIs, you can generate API credentials from your Wallet Dashboard.

> **Note**:
> After generating the keys from the Dashboard, you must download and save
> them securely.If you lose access to your key secret, you can generate a new key from your 
> dashboard and update all your integrations.

An API credential consists of a Key and a Secret.

> **Note**:
> The API Key is used to initiate payments, and can be exposed publicly. The API Key Secret is like your password, and should not be exposed.

SafiMoney APIs use basic access authentication to authenticate all server-side requests. You need to send authentication header in Post Request

```json
headers:
{
 	Authorization: Bearer {
         "namespace":"", // namespace are added in the respective API section 
         "action":"", 	// action performs on entity
         "key":"", 		// your api key
         "timestamp": "",  // Timestamp*
         "hash": SHA256(namespace+action+key+timestamp+api_secret) // hash 
    }
}
```



> Timestamp must be UTC timestamp and it should be incremental. The timestamp is valid for only 60 seconds.

In case you use [SafiMoney SDK](https://github.com/safimoney/safimoney-sdk-php) then you don't need to create header, SDK will do that itself.



![](images/api_credentials.gif)   





**Errors**

SafiMoney API all responses are returned with HTTP Status code 200. 

If  Error is from SafiMoney end, you need to check the error object in the response, the code will remain 200. 

```
 response:{
 	"error": 
         {
                "title": "Error !", // title of the error
                "message": "", // message of the error 
                "remedy": "",
                "validation": [],
                "data": null,
        }      
 }
 
```

