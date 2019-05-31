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

                "lastOnlineText":"online",
                "lastOnlineFlag":"online",
                "distanceText":"<1km", //<1км
                "age":37,
                
                "property":0,
                "transport":10,
                "income":20,
                "height":150,

                "photos": [
                        {
                          "photoId": "480x640_sfsdfsdfsdf",
                          "photoUri": "https://bla-bla.jpg",
                          "thumbnailPhotoUri":"https://bla.jpg"
                        },
                        {
                          "photoId": "480x640_gfgsdfsdf",
                          "photoUri": "https://bla-bla.jpg",
                          "thumbnailPhotoUri":"https://bla.jpg"
                        },
                        {
                          "photoId": "480x640_gfdsfsdfsdf",
                          "photoUri": "https://bla-bla.jpg",
                          "thumbnailPhotoUri":"https://bla.jpg"
                        }
                ]
            },
            ...
        ]
    }

Possible values for `lastOnlineText`

* any text (include empty string)
* `unknown`

Possible values for `lastOnlineFlag`

* `online`
* `away`
* `offline`
* `unknown`

Possible values for `distanceText`

* any text (include empty string)
* `unknown`

Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError

### Get LMM

* url ``https://{API ENDPOINT}/get_lmm?accessToken={ACCESS TOKEN}&resolution=480x640&source=matches&lastActionTime=123345``

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

Allowed Values for source:

* new_faces
* who_liked_me
* matches
* messages
* chat
* profile

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

              "lastOnlineText":"online",
              "lastOnlineFlag":"online",
              "distanceText":"<1km", //<1км
              "age":37,
              
              "property":0,
              "transport":10,
              "income":20,
              "height":150,
                              
              "notSeen": true,
              "messages" : [], //!!!COULD BE NOT EMPTY
              "photos": [
                {
                  "photoId": "480x640_52e08292d10cacf2f40abe5542513187270bb182",
                  "photoUri": "https://bla-bla.jpg",
                  "thumbnailPhotoUri":"https://bla.jpg"
                },
                ....
              ]
            },
            {
              "userId": "fsdfsdfsdfsdfsdf",
              "defaultSortingOrderPosition": 1,

              "lastOnlineText":"online",
              "lastOnlineFlag":"online",
              "distanceText":"<1km", //<1км
              "age":37,
              
              "property":0,
              "transport":10,
              "income":20,
              "height":150,
                            
              "notSeen": false,
              "photos": [
                {
                  "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                  "photoUri": "https://bla-bla.jpg",
                  "thumbnailPhotoUri":"https://bla.jpg"
                },
                ....
              ]
            }
        ],
        
        "matches": [
            {
               "userId": "fsdfsdfsdfsdfsdf",
               "defaultSortingOrderPosition": 0,

               "lastOnlineText":"online",
               "lastOnlineFlag":"online",
               "distanceText":"<1km", //<1км
               "age":37,
               
               "property":0,
               "transport":10,
               "income":20,
               "height":150,
                             
               "notSeen": true,
               "messages" : [], //ALWAYS EMPTY
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://bla-bla.jpg",
                    "thumbnailPhotoUri":"https://bla.jpg"
                 },
                 ...
        ],
        
        "messages": [
            {
               "userId": "fsdfsdfsdfsdfsdf",
               "defaultSortingOrderPosition": 0,

               "lastOnlineText":"online",
               "lastOnlineFlag":"online",
               "distanceText":"<1km", //<1км
               "age":37,
               
               "property":0,
               "transport":10,
               "income":20,
               "height":150,
                             
               "notSeen": false, //ALWAYS false in this feed. The client determines read/unread profile indicator based on change in the total count of messages for each profile. If the count has changed from the value stored in the local cache then you can assume there are new messages and the app should display unread icon, otherwise read icon.
               "messages" : [
                    {"wasYouSender":false,"text":"Hi"}, {"wasYouSender":true,"text":"Hi"}
               ],
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg",
                    "thumbnailPhotoUri":"https://bla.jpg"
                 },
                 ...
        ]
        
    }
    
Possible values for `lastOnlineText`

* any text (include empty string)
* `unknown`

Possible values for `lastOnlineFlag`

* `online`
* `away`
* `offline`
* `unknown`

Possible values for `distanceText`

* any text (include empty string)
* `unknown`
 
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError

### Get LMHIS

* url ``https://{API ENDPOINT}/get_lmhis?accessToken={ACCESS TOKEN}&resolution=480x640&source=matches&lastActionTime=123345``

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

Allowed Values for source:

* new_faces
* who_liked_me
* matches
* messages
* chat
* profile
* hellos
* inbox
* sent

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
              "lastOnlineText":"online",
              "lastOnlineFlag":"online",
              "distanceText":"<1km", //<1км
              "age":37,
              
              "property":0,
              "transport":10,
              "income":20,
              "height":150,
                            
              "notSeen": true,
              "messages" : [], //!!!COULD BE NOT EMPTY
              "photos": [
                {
                  "photoId": "480x640_52e08292d10cacf2f40abe5542513187270bb182",
                  "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/52e08292d10cacf2f40abe5542513187270bb182_480x640.jpg",
                  "thumbnailPhotoUri":"https://bla.jpg"
                },
                ....
              ]
            },
            {
              "userId": "fsdfsdfsdfsdfsdf",
              "defaultSortingOrderPosition": 1,
              "notSeen": false,
              "lastOnlineText":"online",
              "lastOnlineFlag":"online",
              "distanceText":"<1km", //<1км
              "age":37,
              
              "property":0,
              "transport":10,
              "income":20,
              "height":150,
              
              "photos": [
                {
                  "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                  "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg",
                  "thumbnailPhotoUri":"https://bla.jpg"
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
               "lastOnlineText":"online",
               "lastOnlineFlag":"online",
               "distanceText":"<1km", //<1км
               "age":37,
               
               "property":0,
               "transport":10,
               "income":20,
               "height":150,
                             
               "messages" : [], //ALWAYS EMPTY
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg",
                    "thumbnailPhotoUri":"https://bla.jpg"
                 },
                 ...
        ],
        
        
        "hellos": [
            {
               "userId": "fsdfsdfsdfsdfsdf",
               "defaultSortingOrderPosition": 0,
               "lastOnlineText":"online",
               "lastOnlineFlag":"online",
               "distanceText":"<1km", //<1км
               "age":37,
               
               "property":0,
               "transport":10,
               "income":20,
               "height":150,
                             
               "notSeen": false,
               "messages" : [
                    {"wasYouSender":false,"text":"Hi"}, {"wasYouSender":false,"text":"Hi"}
               ],
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg",
                    "thumbnailPhotoUri":"https://bla.jpg"
                 },
                 ...
        ],
        "inbox": [
            {
               "userId": "fsdfsdfsdfsdfsdf",
               "defaultSortingOrderPosition": 0,
               "lastOnlineText":"online",
               "lastOnlineFlag":"online",
               "distanceText":"<1km", //<1км
               "age":37,
               
               "property":0,
               "transport":10,
               "income":20,
               "height":150,
                             
               "notSeen": true, 
               "messages" : [
                    {"wasYouSender":false,"text":"Hi"}, {"wasYouSender":false,"text":"Hi"}
               ],
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg",
                    "thumbnailPhotoUri":"https://bla.jpg"
                 },
                 ...
        ],
        "sent": [
            {
               "userId": "fsdfsdfsdfsdfsdf",
               "defaultSortingOrderPosition": 0,
               "lastOnlineText":"online",
               "lastOnlineFlag":"online",
               "distanceText":"<1km", //<1км
               "age":37,
               
               "property":0,
               "transport":10,
               "income":20,
               "height":150,
                             
               "notSeen": true,
               "messages" : [
                    {"wasYouSender":false,"text":"Hi"}, {"wasYouSender":true,"text":"Hi"}
               ],
               "photos": [
                 {
                    "photoId": "480x640_a196717eab427bd6c0a0128d0f213d4857ad5c3d",
                    "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/a196717eab427bd6c0a0128d0f213d4857ad5c3d_480x640.jpg",
                    "thumbnailPhotoUri":"https://bla.jpg"
                 },
                 ...
        ]
        
    }

Possible values for `lastOnlineText`

* any text (include empty string)
* `unknown`

Possible values for `lastOnlineFlag`

* `online`
* `away`
* `offline`
* `unknown`

Possible values for `distanceText`

* any text (include empty string)
* `unknown`

Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError

### Get Chat

* url ``https://{API ENDPOINT}/chat?accessToken={ACCESS TOKEN}&resolution=480x640&lastActionTime=123345&userId=kjdshfhhfj1``

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
        "chatExists": true,
        "pullAgainAfter": 3000
       
        "chat": {
            "userId": "5bdc880d91d60b28b17ab2e58bf4a7c6ab83091e",
            "defaultSortingOrderPosition": 0,
            "lastOnlineText": "18мин назад",
            "lastOnlineFlag": "online",
            "distanceText": "unknown",
            "notSeen": false,
            "photos": [
              {
                "photoId": "480x640_f34fe06440021c07b4dd3ad77e12475a0cb3640f",
                "photoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/f34fe06440021c07b4dd3ad77e12475a0cb3640f_480x640.jpg",
                "thumbnailPhotoUri": "https://s3-eu-west-1.amazonaws.com/test-ringoid-public-photo/f34fe06440021c07b4dd3ad77e12475a0cb3640f_thumbnail.jpg"
              }
            ],
            "messages": [
              {
                "wasYouSender": false,
                "text": "Hello!"
              }
            ],
            "age": 37,
            "property": 0,
            "transport": 0,
            "income": 0,
            "height": 0
        }
    }
    
Possible values for `lastOnlineText`

* any text (include empty string)
* `unknown`

Possible values for `lastOnlineFlag`

* `online`
* `away`
* `offline`
* `unknown`

Possible values for `distanceText`

* any text (include empty string)
* `unknown`
 
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
* source - string (feed from which lmm was requested)
* likeYouProfilesNum - int
* matchProfilesNum - int
* messageProfilesNum - int
* repeatRequestAfter - int
* unixTime - int
* eventType - string (FEEDS_LLM_PROFILES)

3. FEEDS_LMHIS_PROFILES

* userId - string
* sourceIp - string
* source - string (feed from which lmm was requested)
* likeYouProfilesNum - int
* matchProfilesNum - int
* hellosProfilesNum - int
* inboxProfilesNum - int
* sentProfilesNum - int
* repeatRequestAfter - int
* unixTime - int
* eventType - string (FEEDS_LMHIS_PROFILES)

3. FEEDS_CHAT_WAS_RETURNED

* userId - string
* sourceIp - string
* oppositeUserId - string
* messageNum - int
* repeatRequestAfter - int
* pullAgainAfter - int
* unixTime - int
* eventType - string (FEEDS_CHAT_WAS_RETURNED)

