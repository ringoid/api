# Actions Service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/actions``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/actions``

### Report reasons

* report_profile_button_0 = Inappropriate message
* report_profile_button_1 = Inappropriate photo
* report_profile_button_2 = Stolen photo, Copyright infringement
* report_profile_button_3 = Spam, Advertising, Commercial activity
* report_profile_button_4 = Human and sex trafficking, Criminal activity
* report_profile_button_5 = Underage user, Child exploitation
* report_profile_button_6 = Harassment or threats, Abuse

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
        "errorMessage":"",
        "lastActionTime":12345
    }
    
Possible errorCodes:

* InternalServerError
* InvalidAccessTokenClientError
* WrongRequestParamsClientError
* TooOldAppVersionClientError

## Possible ACTION_OBJECTS

Possible source feeds : new_faces, who_liked_me, matches, messages, chat

1. LIKE json with properties:
        
        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"LIKE",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "likeCount":12,
        "actionTime":12342342354 //unix time in milliseconds

2. VIEW json with properties:


        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"VIEW",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "viewCount":5,
        "viewTimeMillis":45,
        "actionTime":12342342354 //unix time in milliseconds


3. BLOCK json with properties


        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"BLOCK",
        "targetUserId":"skdfkjhkjsdhf",
        "targetPhotoId":"sldfnlskdj",
        "blockReasonNum":19,
        "actionTime":12342342354 //unix time in milliseconds

4. UNLIKE json with properties


        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"UNLIKE",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "actionTime":12342342354 //unix time in milliseconds

5. MESSAGE json with properties


        "sourceFeed":"new_faces", // who_liked_me, matches, messages
        "actionType":"MESSAGE",
        "targetPhotoId":"640x480_ksjdhfkjhhsh",
        "targetUserId":"skdfkjhkjsdhf",
        "text":"Hi",
        "actionTime":12342342354 //unix time in milliseconds

6. VIEW_CHAT json with properties

         
         "sourceFeed":"who_liked_me", // who_liked_me, matches, messages
         "actionType":"VIEW_CHAT",
         "targetPhotoId":"640x480_ksjdhfkjhhsh",
         "targetUserId":"skdfkjhkjsdhf",
         "viewTimeMillis":45,
         "actionTime":12342342354 //unix time in milliseconds
        
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

6. ACTION_USER_VIEW_CHAT

* userId - string
* sourceIp - string
* targetUserId - string
* photoId - string
* originPhotoId - string
* source - string
* viewAt - int
* viewTimeMillis - int
* unixTime - int
* eventType - string (ACTION_USER_VIEW_CHAT)
