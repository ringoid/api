# auth service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/auth``
### PROD API ENDPOINT IS ``https://prod.ringoidapp.com/auth``


### Create user profile

* url ``https://{API ENDPOINT}/create_profile``

POST request

Headers:

* x-ringoid-android-buildnum : 1       //int, x-ringoid-ios-buildnum in case of iOS
* Content-Type : application/json

Body:

    {
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

    
    all aprameters are required
    
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
* wasPushChanged - bool
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
