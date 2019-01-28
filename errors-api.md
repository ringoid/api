# Errors Service

### STAGE API ENDPOINT IS ``https://stage.ringoidapp.com/errors``


### Timeout url

* url ``https://{API ENDPOINT}/timeout``

POST request

Headers:

* Content-Type : application/json

### InvalidToken url

* url ``https://{API ENDPOINT}/invalidtoken``

POST request

Headers:

* Content-Type : application/json

Possible errorCodes:

* InvalidAccessTokenClientError


### Non ok url

* url ``https://{API ENDPOINT}/nonok``

POST request

Headers:

* Content-Type : application/json

Returns 503

### TooOldAppVersionClientError url

* url ``https://{API ENDPOINT}/old_version``

POST request

Headers:

* Content-Type : application/json

Possible errorCodes:

* TooOldAppVersionClientError

### InternalServerError url

* url ``https://{API ENDPOINT}/internalerror``

POST request

Headers:

* Content-Type : application/json

Possible errorCodes:

* InternalServerError

