
### How to handle errors that a service returns

* **InternalServerError** - something went wrong inside the service (this is not OK and not planned). If you want to execute the request again, please pause between requests (i.e. introduce a delay to avoid overloading services and incurring extra charges if other apps are receiving that error too). If you still get this error after 3 attemps, display "Oops! Something went wrong" message box that also includes a text downloaded from http://ringoid.com/status.html

* **InvalidAccessTokenClientError** - you will get that when your accessToken is not valid any longer and you can not use it to access services. You need to clear app's cache and return to the first screen (when user can enter their year of birth and sex, and tap Continue button to register).

* **TooOldAppVersionClientError** - that means that your app's buildNum is too old, your app is outdated and services won't allow you to access API anymore. You need to display a special screen asking an user to do a forceful update of the app from the Apple iTunes app store or Google Play store. Don't try 

* **?ClientError** - you will get (WrongSexClientError || WrongRequestParamsClientError ..) when you passed wrong parameters. There is no need to repeat such requests unless you fix parameters.
