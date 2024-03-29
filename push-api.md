# push service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/push``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/push``

### Push Messages

1. Notification message (once a day) [docs](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications)

        {
            "message":{
                "token":"bk3RNwTe3H0:CI2k_HHwgIpoDKCIZvvDMExUdFQ3P1...",
                "notification":{
                "title":"",
                "body":"Check out new users"
                }
            }
        }

2. New like notification messages with optional data payload [docs](https://firebase.google.com/docs/cloud-messaging/concept-options#notification-messages-with-optional-data-payload)

        {
            "message":{
            "token":"bk3RNwTe3H0:CI2k_HHwgIpoDKCIZvvDMExUdFQ3P1...",
            "notification":{
            "title":"",
            "body":"You have new like!"
            },
            
            "data" : {
            "type" : "NEW_LIKE_PUSH_TYPE",
            "oppositeUserId":"sldkfjjj939i4",
            "name" : "Alexandra", //could be `unknown`
            "thumbnails": "https://cdn.net/bla.jpg", // or could be "https://cdn.net/bla.jpg;https://cdn.net/bla_1.jpg",
            "ts" : "1233455667" //unix time in millis (when message was received by server)
            }
            }
        }

3. New match notification messages with optional data payload [docs](https://firebase.google.com/docs/cloud-messaging/concept-options#notification-messages-with-optional-data-payload)

        {
            "message":{
            "token":"bk3RNwTe3H0:CI2k_HHwgIpoDKCIZvvDMExUdFQ3P1...",
            "notification":{
            "title":"",
            "body":"You have new match!"
            },
            
            "data" : {
            "type" : "NEW_MATCH_PUSH_TYPE",
            "oppositeUserId":"sldkfjjj939i4",
            "name" : "Alexandra", //could be `unknown`
            "thumbnails": "https://cdn.net/bla.jpg;https://cdn.net/bla_1.jpg",
            "ts" : "1233455667" //unix time in millis (when message was received by server)
            }
            }
        }

4. New message notification messages with optional data payload [docs](https://firebase.google.com/docs/cloud-messaging/concept-options#notification-messages-with-optional-data-payload)

        {
            "message":{
            "token":"bk3RNwTe3H0:CI2k_HHwgIpoDKCIZvvDMExUdFQ3P1...",
            "notification":{
            "title":"",
            "body":"You have new message!"
            },
            
            "data" : {
            "type" : "NEW_MESSAGE_PUSH_TYPE",
            "oppositeUserId":"sldkfjjj939i4",
            "text" : "Hi",
            "name" : "Alexandra", //could be `unknown`
            "thumbnails": "https://cdn.net/bla.jpg;https://cdn.net/bla_1.jpg",
            "ts" : "1233455667" //unix time in millis (when message was received by server)
            }
            }
        }
    
    
### Register device token

!!! DEPRECATED METHOD
* url ``https://{API ENDPOINT}/update_token``

!!! VALID METHOD
* url ``https://{API ENDPOINT}/update_fcm_token``

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
* EmailNotVerifiedClientError

## Analytics Events

1. PUSH_REGISTER_DEVICE_TOKEN

* userId - string
* deviceToken - string
* isItAndroid - bool
* sourceIp - string
* unixTime - int
* eventType - string (PUSH_REGISTER_DEVICE_TOKEN)

2. PUSH_WAS_SENT

* userId - string
* pushType - string (base/)
* unixTime - int
* eventType - string (PUSH_WAS_SENT)

3. DATA_PUSH_WAS_SENT

* userId - string
* pushType - string (base/)
* unixTime - int
* eventType - string (DATA_PUSH_WAS_SENT)
