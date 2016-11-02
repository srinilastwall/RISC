![Lastwall Logo](lw-logo.jpg) 


# Integration Steps

The minimal steps needed to integrate with the LastWall API are illustrated below.

## Add script to your login page

The recommended mode of integration is via server-side calls to the API. The data collected by the script can be sent to the LastWall API via appropriate server side modules.


## Server side integration - Recommended

Depending on your server-side stack - setup a module to connect to the LastWall API via HTTPS.

### HTTP Basic Authentication

Lastwall API calls using basic authentication must be sent with the following request header:    

- **X-LW-Authorization** - a standard HTTP Basic Authentication header  
- **X-LW-Token** - a standard HTTP Basic Authentication header    

For more information on HTTP Basic Authentication, see [Basic Authentication](http://www.httpwatch.com/httpgallery/authentication/)

This mode of authentication is to be used in conjunction with HTTPS only.

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

## POST - /auth


Authenticates a user based on a RISC payload. Returns a trust score indicating the level of RISK associated with the user.


#### Required Parameters

- **riscdata** - JSON payload of data collected by "script"


#### Return Values

- **status** - String 'LW_Success' or 'LW_Failure'. If it's an LW_Failure, the specific message is included in the 'error' return value.


### Examples

**Request:** `curl -X POST -H "(headers)" "https://risc.lastwall.com/api/auth" -d '{"riscdata":"(jsonvals_riscdata)"}'"`    

**Response:** `HTTP/1.1 200 OK`    `{ "status": "LW_Success" , "trust" : "HIGH" , "score" : "0.87538745"}`

---------------------------------------

## POST - /account


Based on a RISC payload. Returns a trust score indicating the level of RISK associated with the new Sign Up.


#### Required Parameters

- **riscdata** - JSON payload of data collected by "script"


#### Return Values

- **status** - String 'LW_Success' or 'LW_Failure'. If it's an LW_Failure, the specific message is included in the 'error' return value.


### Examples

**Request:** `curl -X POST -H "(headers)" "https://risc.lastwall.com/api/account" -d '{"riscdata":"(jsonvals_riscdata)"}'"`    

**Response:** `HTTP/1.1 200 OK`    `{ "status": "LW_Success" , "trust" : "HIGH" , "score" : "0.87538745"}`

---------------------------------------
