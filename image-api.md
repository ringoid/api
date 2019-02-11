# Image Service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/image``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/image``


### Get pre-signed url

* url ``https://{API ENDPOINT}/get_presigned``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "extension":"jpg",
        "clientPhotoId":"sldfjlskdfj--;lfk;lf"
    }
    
    all parameters are required
    
 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":"",
        "uri":"https://bla.com/bla",
        "originPhotoId":"sdljfhsljkdhgsdkj",
        "clientPhotoId":"sldfjlskdfj--;lfk;lf"
    }
    
Possible errorCodes:

* InternalServerError
* InvalidAccessTokenClientError
* WrongRequestParamsClientError
* TooOldAppVersionClientError

### Get user's own photos

* url ``https://{API ENDPOINT}/get_own_photos?accessToken={ACCESS TOKEN}&resolution=480x640``

GET request

Allowed Sizes:

* 480x640
* 720x960
* 1080x1440
* 1440x1920

* 750x1000
* 828x1344
* 1125x1827
* 1242x2016


Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":"",
        "photos":[
            {
                "photoId":"12dd",
                "originPhotoId":"sldkjflkjlkjlkjf",
                "photoUri":"https://bla-bla.com/sss.jpg",
                "likes":22,
                "blocked":true
            },
            {
                "photoId":"13dd",
                "originPhotoId":"mnbmvnbcxlsdfhwo",
                "photoUri":"https://bla-bla.com/sss2.jpg",
                "likes":0,
                "blocked":false
            }
        ]
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError

### Delete user's photo

* url ``https://{API ENDPOINT}/delete_photo``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "photoId":"lsdkfjlskdjf-sdflksndfl"   //it could be originPhotoId's value also 
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


## Analytics Events

1. IMAGE_USER_ASK_UPLOAD_PHOTO_LINK

* userId - string
* bucket - string
* photoKey - string
* unixTime - int
* eventType - string (IMAGE_USER_ASK_UPLOAD_PHOTO_LINK)

2. IMAGE_USER_UPLOAD_PHOTO

* userId - string
* bucket - string
* photoKey - string
* photoId - string
* photoType - string (origin in most cases)
* size - int
* unixTime - int
* eventType - string (IMAGE_USER_UPLOAD_PHOTO)

3. IMAGE_USER_DELETE_PHOTO

* userId - string
* sourceIp - string
* photoId - string
* userTakePartInReport - bool
* unixTime - int
* eventType - string (IMAGE_USER_DELETE_PHOTO)

4. IMAGE_REMOVE_TO_BIG_S3_OBJECT

* userId - string
* bucket - string
* key - string
* size - int
* unixTime - int
* eventType - string (IMAGE_REMOVE_TO_BIG_S3_OBJECT)

5. IMAGE_GET_OWN_PHOTOS

* userId - string
* sourceIp - string
* ownPhotoNum - int
* unixTime - int
* eventType - string (IMAGE_GET_OWN_PHOTOS)
