# auth service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/auth``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/auth``

### Login

* url ``https://{API ENDPOINT}/login_with_email``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "locale":"ru",
        "email":"vova@mail.ru"
    }
    
    parameter is required
    
 Response Body:
 
    {
        "authSessionId":"adasdasd-fadfs-sdffd",
        "errorCode":"",
        "errorMessage":""
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* TooOldAppVersionClientError
* EmailNotVerifiedClientError

### Verify email

* url ``https://{API ENDPOINT}/verify_email``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "authSessionId":"adasdasd-fadfs-sdffd",
        "email":"vova@mail.ru",
        "pinCode":"12345"
    }
    
    all parameters are required
    
 Response Body:
 
    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "errorCode":"",
        "errorMessage":""
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* TooOldAppVersionClientError
* EmailInvalidVerificationClientError
* WrongPinCodeClientError

### Change email

* url ``https://{API ENDPOINT}/change_email``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "newEmail":"sasha@gmail.com"
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
* InvalidAccessTokenClientError
* EmailAlreadyInUseClientError

### Create user profile

* url ``https://{API ENDPOINT}/create_profile``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {   
        "authSessionId":"adasdasd-fadfs-sdffd",
        "email":"slava@mail.ru",
        "yearOfBirth":1982,
        "sex":"male" // possible values are **male** or **female**,
        "dtTC":1535120929, //unix time when Terms and Conditions were accepted
        "dtLA":1535120929, //unix time when Legal age was confirmed
        "dtPN":1535120929, //unix time when Privacy Notes were accepted
        "deviceModel":"device model info",
        "osVersion":"version of os",
        "referralId":"masha123",
        "privateKey":"ksjdhf9-lsdf-223jd"
        "settings":{
                    "locale":"en",
                    "push":true,
                    "pushNewLike":true,
                    "pushNewMessage":true,
                    "pushNewMatch":true,
                    "timeZone":3
                   }
    }
    
    all parameters except referralId, privateKey and settings are required
    
 Response Body:
 
    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "customerId":"ksjdhfha-asff",
        "errorCode":"",
        "errorMessage":""
    }
    
Possible errorCodes:

* InternalServerError
* WrongYearOfBirthClientError
* WrongSexClientError
* WrongRequestParamsClientError
* TooOldAppVersionClientError
* EmailConcurrentUsageClientError

### Get user's profile

* url ``https://{API ENDPOINT}/get_profile?accessToken={ACCESS TOKEN}``

GET request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":"",
        
        "customerId":"ksjdhfha-asff",
        
        "lastOnlineText":"online",
        "lastOnlineFlag":"online",
        "distanceText":"<1km", //<1км
                
        "yearOfBirth":1982,
        "sex":"female",
                
        "property":0,
        "transport":10,
        "income":20,
        "height":150,
        "educationLevel":10,
        "hairColor":0,
        "children":0,
        "name":"Mikhail",
        "jobTitle":"Developer",
        "company":"Ringoid",
        "education":"BGTU Voenmeh",
        "about":"Nice person",
        "instagram":"unknown",
        "tikTok":"unknown",
        "whereLive":"St.Petersburg",
        "whereFrom":"Leningrad",
        "statusText":"Hi all!"
    }

Possible values for `lastOnlineText`, `distanceText`, `name`, `jobTitle`, `company`, 
`education`, `about`, `instagram`, `tikTok`, `whereLive`, `whereFrom`, `statusText` :

* any text (include empty string)
* `unknown`

Possible values for `lastOnlineFlag`

* `online`
* `away`
* `offline`
* `unknown`

Possible values for `sex`

* `male`
* `female`
* `unknown`

Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError
* EmailNotVerifiedClientError


### Update user's settings

* url ``https://{API ENDPOINT}/update_settings``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "locale":"en",
        "push":true,
        "pushNewLike":true,
        "pushNewMessage":true,
        "pushNewMatch":true,
        "timeZone":3
    }
    
    accessToken is required
    
 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":""
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError
* EmailNotVerifiedClientError

### Delete user's account

* url ``https://{API ENDPOINT}/delete``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body

    {
        "accessToken":"adasdasd-fadfs-sdffd"
    }

    
    accessToken is required param
    
 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":""
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError
* EmailNotVerifiedClientError

### Claim referral code

* url ``https://{API ENDPOINT}/claim``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body

    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "referralId":"masha2001"
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
* InvalidAccessTokenClientError
* TooOldAppVersionClientError
* EmailNotVerifiedClientError

### Update profile's info

* url ``https://{API ENDPOINT}/update_profile``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body

    {
        "accessToken":"adasdasd-fadfs-sdffd",
        "property":0,
        "transport":10,
        "income":20,
        "height":150,
        "educationLevel":10,
        "hairColor":0,
        "children":0
        "name":"Mikhail",
        "jobTitle":"Developer",
        "company":"Ringoid",
        "education":"BGTU Voenmeh",
        "about":"Nice person",
        "instagram":"",
        "tikTok":"",
        "whereLive":"St.Petersburg",
        "whereFrom":"Leningrad",
        "statusText":"Hi all!"
    }

    
    all parameters are required, possible values (here)[https://docs.google.com/spreadsheets/d/1S7k_VQ6mBXTJjvZoPuqiyamrhZWquT3LnPHwV2Z-gDE/edit#gid=0]
    
 Response Body:
 
    {
        "errorCode":"",
        "errorMessage":""
    }
    
Possible errorCodes:

* InternalServerError
* WrongRequestParamsClientError
* InvalidAccessTokenClientError
* TooOldAppVersionClientError
* EmailNotVerifiedClientError

## Analytics Events

1. AUTH_USER_ACCEPT_TERMS

* userId - string
* sourceIp - string
* unixTime - int
* dtTC - date and time when Terms and conditions were accepted
* dtPN - date and time when Privacy Notes were accepted
* dtLA - date and time when Legal age was confirmed
* androidDeviceModel - string (model of the device (Build.MODEL + "," + Build.MANUFACTURER + "," + Build.PRODUCT))
* androidOsVersion - string
* iOsDeviceModel - string (model of the device (Build.MODEL + "," + Build.MANUFACTURER + "," + Build.PRODUCT))
* iOsVersion - string
* eventType - string (AUTH_USER_ACCEPT_TERMS)


2. AUTH_USER_PROFILE_CREATED

* userId - string
* email - string
* sourceIp - string
* sex - string
* yearOfBirth - int
* unixTime - int
* referralId - string
* privateKey - string
* eventType - string (AUTH_USER_PROFILE_CREATED)

3. AUTH_USER_SETTINGS_UPDATED

* userId - string
* sourceIp - string
* locale - string
* wasLocaleChanged - bool
* push - bool
* pushNewLike - bool
* pushNewMatch - bool
* pushNewMessage - bool
* wasPushChanged - bool
* wasPushNewLikeChanged - bool
* wasPushNewMatchChanged - bool
* wasPushNewMessageChanged - bool
* timeZone - int
* wasTimeZoneChanged - bool
* unixTime - int
* eventType - string (AUTH_USER_SETTINGS_UPDATED)

4. AUTH_GET_USER_SETTINGS

* userId - string
* sourceIp - string
* unixTime - int
* eventType - string (AUTH_GET_USER_SETTINGS)


5. AUTH_USER_CALL_DELETE_HIMSELF

* userId - string
* sourceIp - string
* userReportStatus - string (REPORTED || REPORT_INITIATOR)
* unixTime - int
* eventType - string (AUTH_USER_CALL_DELETE_HIMSELF)

6. AUTH_USER_CLAIM_REFERRAL_CODE

* userId - string
* sourceIp - string
* referralId - string
* unixTime - int
* eventType - string (AUTH_USER_CLAIM_REFERRAL_CODE)

7. AUTH_USER_UPDATE_PROFILE

* userId - string
* sourceIp - string
* property - int
* transport - int
* income - int
* height - int
* hairColor - int
* children - int
* educationLevel - int
* name - string,
* jobTitle - string,
* company - string,
* education - string,
* about - string,
* instagram - string,
* tikTok - string,
* whereLive - string,
* whereFrom - string,
* statusText - string,
* unixTime - int
* eventType - string (AUTH_USER_UPDATE_PROFILE)

8. AUTH_USER_CHANGE_EMAIL

* userId - string
* sourceIp - string
* oldEmail - string
* newEmail - string
* unixTime - int
* eventType - string (AUTH_USER_CHANGE_EMAIL)
