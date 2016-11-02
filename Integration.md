![Lastwall Logo](lw-logo.jpg) 


# Integration Steps

The minimal steps needed to integrate with the LastWall API are illustrated below.

## Add script to your login page

The recommended mode of integration is via server-side calls to the API. The data collected by the script can be sent to the LastWall API via appropriate server side modules.


## Server side integration - Recommended

Depending on your server-side stack - setup a module to connect to the LastWall API via HTTPS.

### HMAC authentication

Lastwall API calls using HMAC authentication must be sent using a secret shared on Sign up with Lastwall    

For more information on HMAC Authentication, see [HMAC Authentication](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)

## API Return Values

All Lastwall API calls will return one of the following status codes:

- **200** - OK: the API call was successful
- **400** - Error: the API call failed due to invalid input or caller error
- **401** - Authorization Error: the API call failed due to an API key authentication failure
- **500** - Fatal: the API call failed due to an internal Lastwall system error (not your fault)

For all successful API calls (code 200), the relevant response data will be returned as JSON in the message body. If there is no data to return, the result will be:

`{ "status": "OK" }`

For all failed API calls (codes 400, 401, or 500), the result will be:

`{ "status": "Error", "error": "(specific error message)" }`


# ![Lastwall Logo](lw-logo.jpg) RISC API Calls

The API call available for a standard RISC service.


---------------------------------------

## POST - /authenticate


Authenticates a user based on a RISC payload. Returns a trust score indicating the level of RISK associated with the user.


#### Required Parameters

- **authreq** - JSON payload of data collected by "script"


#### Return Values

- **status** - String 'OK' or 'Error'. If it's an error, the specific message is included in the 'error' return value.
- **error** - Undefined or specific error message.


### Examples

**Request:** `curl -X POST -H "(headers)" "https://risc.lastwall.com/api/authenticate" -d '{"authreq":"(jsonvals_riscdata)"}'"`    

**Response:** `HTTP/1.1 200 OK`    `{ "status": "OK" , "trust" : "HIGH" , "score" : "0.87538745"}`

---------------------------------------
