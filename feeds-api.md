# Feeds Service


### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/feeds``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/feeds``

### Get new faces

* url ``https://{API ENDPOINT}/get_new_faces?accessToken={ACCESS TOKEN}&resolution=480x640&lastActionTime=123345&limit={LIMIT}``

GET request

Allowed Sizes:

* 480x640
* 720x960
* 1080x1440
* 1440x1920

* 640x852
* 750x1000
* 828x1104
* 1125x1500
* 1242x1656

LIMIT max value is 100, default value is 5

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":"",
        "repeatRequestAfter":0,
        "profiles":[
            {
                "userId":"9091127b2a88b002fad4ef55beb0264222c1ebb7",
                "defaultSortingOrderPosition":0,
                "photos": [
                        {
                          "photoId": "480x640_sfsdfsdfsdf",
                          "photoUri": "https://bla-bla.jpg"
                        },
                        {
                          "photoId": "480x640_gfgsdfsdf",
                          "photoUri": "https://bla-bla.jpg"
                        },
                        {
                          "photoId": "480x640_gfdsfsdfsdf",
                          "photoUri": "https://bla-bla.jpg"
                        }
                ]
            },
            ...
        ]
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError

### Get LMM

* url ``https://{API ENDPOINT}/get_lmm?accessToken={ACCESS TOKEN}&resolution=480x640&lastActionTime=123345``

GET request

Allowed Sizes:

* 480x640
* 720x960
* 1080x1440
* 1440x1920

* 640x852
* 750x1000
* 828x1104
* 1125x1500
* 1242x1656


Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":"",
        "repeatRequestAfter":0,
        
        "likesYou": [
            {
              "userId": "fdsdfsdfsdfsdfsdf",
              "defaultSortingOrderPosition": 0,
              "notSeen": true,
              "messages" : [], //ALWAYS EMPTY
              "photos": [
                {
                  "photoId": "480x640_52e08292d10cacf2f40abe5542513187270bb182",
                  "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/52e08292d10cacf2f40abe5542513187270bb182_480x640.jpg"
                },
                ....
              ]
            },
            {
              "userId": "fsdfsdfsdfsdfsdf",
              "defaultSortingOrderPosition": 1,
              "notSeen": false,
              "photos": [
                {
                  "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                  "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg"
                },
                ....
              ]
            }
        ],
        
        "matches": [
            {
               "userId": "fsdfsdfsdfsdfsdf",
               "defaultSortingOrderPosition": 0,
               "notSeen": true,
               "messages" : [], //ALWAYS EMPTY
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg"
                 },
                 ...
        ],
        
        "messages": [
            {
               "userId": "fsdfsdfsdfsdfsdf",
               "defaultSortingOrderPosition": 0,
               "notSeen": false, //ALWAYS false in this feed. The client determines read/unread profile indicator based on change in the total count of messages for each profile. If the count has changed from the value stored in the local cache then you can assume there are new messages and the app should display unread icon, otherwise read icon.
               "messages" : [
                    {"wasYouSender":false,"text":"Hi"}, {"wasYouSender":true,"text":"Hi"}
               ],
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg"
                 },
                 ...
        ]
        
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError

## Analytics Events

1. FEEDS_NEW_FACES_SEEN_PROFILES

* userId - string
* sourceIp - string
* targetUserIds - []string
* newFaceProfilesNum - int
* repeatRequestAfter - int
* unixTime - int
* eventType - string (FEEDS_NEW_FACES_SEEN_PROFILES)

2. FEEDS_LLM_PROFILES

* userId - string
* sourceIp - string
* likeYouProfilesNum - int
* matchProfilesNum - int
* messageProfilesNum - int
* repeatRequestAfter - int
* unixTime - int
* eventType - string (FEEDS_LLM_PROFILES)

