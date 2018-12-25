# Actions Service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/actions``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/actions``


### Action url

* url ``https://{API ENDPOINT}/actions``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "accessToken":"adfsdfsdfsdfsdfs",
        "actions":[ACTION_OBJECT, ACTION_OBJECT]
    }
    
    all parameters are required
    
 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":""
    }
    
Possible errorCodes:

* InternalServerError
* InvalidAccessTokenClientError
* WrongRequestParamsClientError
* TooOldAppVersionClientError

## Possible ACTION_OBJECTS

1. LIKE json with properties:
        
        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"LIKE",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "likeCount":12,
        "actionTime":12342342354 //unix time

2. VIEW json with properties:


        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"VIEW",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "viewCount":5,
        "viewTimeSec":45,
        "actionTime":12342342354 //unix time


3. BLOCK json with properties


        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"BLOCK",
        "targetUserId":"skdfkjhkjsdhf",
        "targetPhotoId":"sldfnlskdj",
        "blockReasonNum":19,
        "actionTime":12342342354 //unix time

4. UNLIKE json with properties


        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"UNLIKE",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "actionTime":12342342354 //unix time

5. MESSAGE json with properties


        "sourceFeed":"who_liked_me", // who_liked_me, matches, messages
        "actionType":"MESSAGE",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "text":"Hi",
        "actionTime":12342342354 //unix time

6. OPEN_CHAT json with properties

         
         "sourceFeed":"who_liked_me", // who_liked_me, matches, messages
         "actionType":"OPEN_CHAT",
         "targetPhotoId":"640x480_ksjdhfkjhhsh",
         "targetUserId":"skdfkjhkjsdhf",
         "openChatCount":1,
         "openChatTimeSec":23,
         "actionTime":12342342354 //unix time
        
## Analytics Events

1. ACTION_USER_LIKE_PHOTO

* userId - string
* sourceIp - string
* photoId - string
* originPhotoId - string
* targetUserId - string
* likeCount - int
* likedAt - int
* source - string
* unixTime - int
* eventType - string (ACTION_USER_LIKE_PHOTO)
* internalServiceSource - string

2. ACTION_USER_VIEW_PHOTO

* userId - string
* sourceIp - string
* photoId - string
* originPhotoId - string
* targetUserId - string
* viewCount - int
* viewTimeSec - int
* viewAt - int
* source - string
* unixTime - int
* eventType - string (ACTION_USER_VIEW_PHOTO)
* internalServiceSource - string

3. ACTION_USER_BLOCK_OTHER

* userId - string
* sourceIp - string
* targetUserId - string
* targetPhotoId - string
* blockedAt - int
* blockReasonNum - int
* source - string
* unixTime - int
* eventType - string (ACTION_USER_BLOCK_OTHER)
* internalServiceSource - string

4. ACTION_USER_UNLIKE_PHOTO

* userId - string
* sourceIp - string
* photoId - string
* originPhotoId - string
* targetUserId - string
* unLikedAt - int
* source - string
* unixTime - int
* eventType - string (ACTION_USER_UNLIKE_PHOTO)
* internalServiceSource - string

5. ACTION_USER_MESSAGE

* userId - string
* sourceIp - string
* targetUserId - string
* photoId - string
* originPhotoId - string
* text - string (always empty)
* source - string
* messageAt - int
* unixTime - int
* eventType - string (ACTION_USER_MESSAGE)

6. ACTION_USER_OPEN_CHAT

* userId - string
* sourceIp - string
* targetUserId - string
* photoId - string
* originPhotoId - string
* source - string
* openChatCount - int
* openChatAt - int
* openChatTimeSec - int
* unixTime - int
* eventType - string (ACTION_USER_OPEN_CHAT)
