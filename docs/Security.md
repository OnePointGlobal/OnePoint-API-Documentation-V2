# Security

> For more information visit the [main page](../README.md)

It is possible to secure all your access to the API and the use of [callbacks](Callbacks.md).

## Keys
Rather than use the standard Authentication process as defined in the [Account Section](Account.md) the OnePoint Global Platform offers [HMAC Authentication](https://en.wikipedia.org/wiki/HMAC). HMAC Authentication is a mechanism for calculating a message authentication code using a hash function in combination with a shared secret key between the two parties involved in sending and receiving the data (Front-end client and Back-end HTTP service).

In your OnePoint Global Account you can set up a key which consists of the following attributes:

Attribute | Description
--------- | -----------
AppId | The application Id to use in the encryption/decryption process.
Secret | The secret that should be used by the client.
Expiry Date | In line with secure processes the key will be made available for a maximum of 1 year.

### Encryption Process
It is important to distinguish between this approach and the approach defined through the [Account API Process](Account.md). With this process there is no need to login or logout. In addition the [Callback Process] will automatically have this built in allowing you to choose to implement it.

#### Step 1
When a client makes a call to the OnePoint Global Platform the Client should build a string by combining all the data that will be sent, this string contains the following parameters (AppId, HTTP method, request URI, request time stamp, nonce, and Base 64 string representation of the request pay load).

> Note: Request time stamp is calculated using UNIX time (number of seconds since Jan. 1st 1970) to overcome any issues related to a different timezone between client and server. Nonce: is an arbitrary number/string used only once.

#### Step 2
Client will hash this large string built in the first step using a hash algorithm such as (SHA-1) and the API Key assigned to it, the result for this hash is a unique signature for this request.

#### Step 3
The signature will be sent in the Authorization header using the custom scheme such `X-OPG-Signature`. The data in the Authorization header will contain the AppId, request time stamp, and nonce separated by colon ‘:’. The format for the Authorization header will be like: `[Authorization: X-OPG-Signature APPId:Signature:Nonce:Timestamp]`.

#### Step 4
Client sends the request as usual along with the data generated in step 3 in the Authorization header.

### Decryption Process

#### Step 1
Server receives all the data included in the request along with the Authorization header.
Server extracts the values (APP Id, Signature, Nonce and Request Time stamp) from the Authorization header.

#### Step 2
Servers looks for the APP Id in a certain secure repository (DB, Configuration file, etc…) to get the API Key for this client.

#### Step 3
Assuming the OnePoint Global Platform was able to look up this APP Id from the repository, it will be responsible to validate if this request is a replay request and reject it, so it will prevent the API from any replay attacks. This is why we’ve used a request time stamp along with nonce generated at the client, and both values have been included into HMAC signature generation. The server will depend on the nonce to check if it was used before within certain acceptable bounds, i.e. 5 minutes. More about this later.

> If the client is receiving a [callback](Callbacks.md) request then the time stamp and nonce checks will not be valid.

#### Step 4
Server will rebuild a string containing the same data received in the request by adhering to the same parameters orders and encoding followed in the client application, usually this agreement is done up front between the client application and the back-end service and shared using proper documentation.

#### Step 5
Server will hash the string generated in previous step using the same hashing algorithm used by the client (SHA-1) and the same API Key obtained from the secure repository for this client.
The result of this hash function (signature) generated at the server will be compared to the signature sent by the client, if they are equal then server will consider this call authentic and process the request, otherwise the server will reject the request and returns HTTP status code 401 unauthorized.
