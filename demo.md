# Overview
___
Welcome to our V5 API documentation. OKX provides REST and WebSocket APIs to suit your trading needs.

- For users who complete registration on my.okx.com, please visit https://my.okx.com/docs-v5/en/ for the V5 API documentation.
- For users who complete registration on app.okx.com, please visit https://app.okx.com/docs-v5/en/ for the V5 API documentation.
<br>
<br>
<br>
## API Resources and Support
<br>
<br>

### Tutorials
- Learn how to trade with V5 API: [Best practice to OKX’s v5 API]()
- Learn python spot trading step by step: [Python Spot Trading Tutorial]()
- Learn python derivatives trading step by step: [Python Derivatives Trading Tutorial]()
<br>
<br>
<br>

### Python libraries
- Use Python SDK for easier integration: [Python SDK]()
- Get access to our market maker python sample code [Python market maker sample]()
<br>
<br>
<br>

### Customer service
- Please take 1 minute to help us improve: V5 API Satisfaction Survey
- If you have any questions, please consult online customer service
  <br>
  <br>
  <br>

### V5 API Key Creation
Please refer to [my api page](https://www.okx.com/en-sg/account/login?forward=%2Fen-sg%2Faccount%2Fmy-api) regarding V5 API Key creation.

#### Generating an API Key
Create an API Key on the website before signing any requests. After creating an APIKey, keep the following information safe:

- APIKey
- SecretKey
- Passphrase

The system returns randomly-generated APIKeys and SecretKeys. You will need to provide the Passphrase to access the API. We store the salted hash of your Passphrase for authentication. We cannot recover the Passphrase if you have lost it. You will need to create a new set of APIKey.

There are three permissions below that can be associated with an API key. One or more permission can be assigned to any key.

- Read : Can request and view account info such as bills and order history which need read permission
- Trade : Can place and cancel orders, funding transfer, make settings which need write permission
- Withdraw : Can make withdrawals
Each APIKey can be linked with up to 20 IP addresses.
API keys with trading or withdrawal permissions that are not bound to IPs will expire after 14 days of inactivity. (API keys in demo trading will not be deleted.)

#### Making Requests
All private REST requests must contain the following headers:

- `OK-ACCESS-KEY` The API Key as a String.
- `OK-ACCESS-SIGN` The Base64-encoded signature (see Signing Messages subsection for details).
- `OK-ACCESS-TIMESTAMP` The UTC timestamp of your request .e.g : 2020-12-08T09:08:57.715Z
- `OK-ACCESS-PASSPHRASE` The passphrase you specified when creating the APIKey.

Request bodies should have content type `application/json` and be in valid JSON format.

### Login
#### Request Example

| Parameter | Type             | Required             | Description                          |
|:----------------|:-----------------|:---------------------|:-------------------------------------|
| op             | String           | Yes                  | Operation          <br/> `login`       |
| args           | Array of objects | Yes                  | List of account to login             |
| > apiKey       | String           | Yes                  | API Key                              |
| > passphrase   | String           | Yes                  | API Key password                     |
| > timestamp    | String           | Yes                  | Unix Epoch time, the unit is seconds |
| > sign         | String           | Yes	| Signature string                     |

