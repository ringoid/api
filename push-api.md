# push service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/push``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/push``

### Push message payload

    {
     "id":"skjdfhhksk-sdlf",
     "type":"system|deeplink|message",
     "targetUrl":"https://...",   (for 'deeplink' only)
     "text":"some text"
    }

### Register device token

* url ``https://{API ENDPOINT}/update_token``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "accessToken":"kjsdfhkjh-asldnl",
        "deviceToken":"adasldm;alsk--sad"
    }
    
    all parameters are required
    
 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":""
    }

    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* TooOldAppVersionClientError

## Analytics Events

1. PUSH_REGISTER_DEVICE_TOKEN

* userId - string
* deviceToken - string
* isItAndroid - bool
* sourceIp - string
* unixTime - int
* eventType - string (PUSH_REGISTER_DEVICE_TOKEN)
