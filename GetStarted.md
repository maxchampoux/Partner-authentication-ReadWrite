# Partner ReadWrite Authentication process #  

## Process step-by-step ##

#### 1. Retrieve user authentication data from user token ####

Please use the following service to retrieve user authentication data from the user token you have in you possession:
[`GET /APIHelpers/Auth/WithToken/{token}/`](#get_userAuthenticationData)

#### 2. Authenticate as a third-party partner ####

At this step, we have provided you with a partner token that you must use in the "X-WSSE" HTTP header;
The partner token is 16-character hexadecimal string, it is mandatory for any request made on behalf of your customers.

Please authenticate adding your partner token in the "X-WSSE-Requested-By" HTTP header.
```
X-WSSE-REQUESTED-BY: c6da61fcff03c20b
X-WSSE: UsernameToken
	Username="customer001",
	PasswordDigest="+QpstwYoZeToelOvVaObTdRdEZs=",
	Nonce="d36e3162829ed4c89851497a717f",
	Created="2014-03-20T12:51:45Z"

```
#### XX. More information on security and authentication method ####

Place have a look to our API documentation : http://api.ibanfirst.com/APIDocumentation/IbanfirstAPI/Security/
You can find examples of code for computing the password digest and the whole X-WSSE header.

</br>

## Route ##

| Route | Description |
|-------|-------------|
| [`GET /APIHelpers/Auth/WithToken/{token}/`](#get_userAuthenticationData) | Retrieve user authentication data from user token |

## Details ##

### <a id="get_userAuthenticationData"></a> Get user authentication data from user token ###

With the token provided to you by the user, you can gather all information you need to authenticate the user against the API.
This request allows you to get authentication data to execute requests on the API on behalf of an IbanFirst User.

```
Method: 	GET
URL: 		/APIHelpers/Auth/WithToken/{token}/
```

**Parameters:**

| Field | In | Type | Required | Description |
|-------|--|------|----------|-------------|
| token | Route | String(16) | Required | The token of the user you want to authenticate |

Note: Data provided by this request may change as the user change its authentication information on the iBanFirst platform. So, you should execute it every time you will execute some requests, or consecutive requests for the user.

**Example:**
```js
TBD
```

**Returns:**

| Field | Type | Description |
|-------|------|-------------|
| username | String(5) | The userID given to the user by iBanFirst. |
| pass | String | A passphrase identifying the user. |

**Example:**
```js
{
  "username": "im0009",
  "pass": "TBD",
  "civility": "M",
  "firstName": "John",
  "lastName": "Doe",
  "entityName": "Rocket Company",
  "roles": [
    "superadmin",
  ]
}    
```

<hr />






