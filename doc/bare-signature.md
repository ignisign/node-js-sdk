


# Bare Signature

## Flow Summary


## Ignisign version and account creation.

As a first step, you need to create an account on the Ignisign platform that is compatible with the Bare Signature feature.

The Bare Signature feature is available from the `version 4` of the Ignisign platform.

to create an account that with this version, you need to create it on the console v4 of the Ignisign platform.
The URL of the console v4 is : https://console.v4.ignisign.io

## SDK and Example

In the following documentation, we will describe 2 ways to implement the Bare Signature with IgniSign: Directly by API, or with the NodeJS SDK. 
Regarding showcase of the implemtation with the IgniSign NodeJS SDK, We will use Example Data structure and init initialization.

Below, the different element that we will be use to shocase the implementation of the Bare Signature with IgniSign NodeJS SDK:

### Example Data Structure:

The following data structure is an example of the data structure that we will use to showcase the implementation of the Bare Signature with IgniSign NodeJS SDK.

```javascript
type BareSignatureDocument = {
  fileB64      : string;
  fileName     : string;
  mimeType     : string;
  documentHash : string;
}

enum BARE_SIGNATURE_STATUS {
  INIT       = 'INIT',
  IN_PROGESS = 'IN_PROGESS',
  SIGNED     = 'SIGNED',
}

type ExampleBareSignature = {
  _id              ?: string;
  title             : string;
  document          : BareSignatureDocument;
  status            : BARE_SIGNATURE_STATUS;
  codeVerifier      : string;
  accessToken      ?: string;
}
```

## Detailled Flow

### Preliminary Steps

The bare signature is a mechanism that has be made to be intergrated into a higher level signature process.


### Create The autorization Url 

to redirect the user to the Ignisign platform for initiating the Signature session.

#### Create the Autorization URL by youself:

- **base URL** : https://sign.v4.ignisign.io/v4/envs/:appEnv/oauth2/authorize

URL Parameters:

- **appEnv** : `string` : The environment of the application.
DEVELOPMENT | STAGING | PRODUCTION

Query Parameters
- **client_id** : `string` : The client ID of the application. this is the appId of the associated application in the Ignisign platform.

- **redirect_uri** : `string` : The URL to redirect to after the user authorizes the application. You must confugurate authorized redirect URIs in the Ignisign platform.

- **response_type** : `string` : The type of response Ignisign should return. Only the `code` value is supported.

- **code_challenge_method**: `string` : The method used to encode the code challenge. Only the `S256` value is supported.

- **code_challenge**: `string` : The code challenge generated by the application (you). Helper are available in the Ignisign SDK inside the `IgnisignSdkUtilsService` to manage code challenge mechanism.

- **state** : `string` : The state of the access request. 

This is the place where you can specify elements to initialize the signature request.

This object must be a `stringify JSON object` that contains the following elements:

```javascript
{
  // The title of the signature request - 
  // Optional - if not provided a default value will be used.
  title   ?: "string";

  // Hashes as SHA256 Base64 of the document to sign - Required
  hashes  : string[];

  // nonce - Required - a uuid v4 value
  // can be used only use once
  nonce   : "string";

  // externalId - Optional - a unique identifier of the signature request
  externalId ?: "string";

  // language - Optional - the language that will be used  during the end user signature process
  // available EN | FR | DE;
  language   ?: "string";
  
}
``` 


### Use the SDK to create the Autorization URL:
```javascript



```

