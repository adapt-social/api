#Authentication and JWTokens

https://jwt.io/introduction


https://medium.com/@vndpal/how-to-implement-jwt-token-authentication-in-net-core-6-ab7f48470f5c


https://auth0.com/docs/secure/tokens/access-tokens




### What are tokens and what do we need for them?
    - way for securely transmitting information between parties as a JSON object
    - JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.


### What is an OAuth token?
    - OAuth 2.0 uses Access Tokens. An Access Token is a piece of data that represents the authorization to access resources on behalf of the end-user. OAuth 2.0 doesn't define a specific format for Access Tokens. However, in some contexts, the JSON Web Token (JWT) format is often used.


### How do we add it to our project?
    - Create a .NET Core 6 Web API Project
    - Install Required NuGet Packages
    - Configure JWT Authentication
        - In appsettings.json add JWT token details.
        - In your Program.cs file, configure JWT authentication
    - Generate JWT Tokens
    - Protect API Endpoints


### Which alternatives are out there for us?
    - 4 main schemes:
        - Local Authentication
        - Token Based Authentication
        - API Key Based Authentication
        - OAuth (Open Authorization)


### How does JWT works?
    - Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.


### What info is in that token?
    - In its compact form, JSON Web Tokens consist of three parts separated by dots, which are: Header, payload, signature
    - usually it looks like the following: xxxxx.yyyyy.zzzzz
    - Header:
        - *typically* consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.
        - example:
        {
        "alg": "HS256",
        "typ": "JWT"
        }
    - Payload:
        - The second part of the token is the payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: *registered*, *public*, and *private* claims.
        - Example:
        {
        "sub": "1234567890",
        "name": "John Doe",
        "admin": true
        }
    - Signature:
        - To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.
        - Example:   
            HMACSHA256(
            base64UrlEncode(header) + "." +
            base64UrlEncode(payload),
            secret)

### What is access token/refresh token?

- **Access token**
    - used in token-based authentication to allow an application to access an API
    - application receives an access token after a user successfully authenticates and authorizes
    - then passes the access token as a credential when it calls the target API
    - passed token informs the API that the bearer of the token has been authorized to access the API
- **JWT access token**
    - contain information about an entity in the form of claims
    - are self-contained therefore it is not necessary for the recipient to call a server to validate the token
- **Refresh token**
    - A refresh token is a special token that is used to obtain more access tokens
    - request a refresh token alongside the access and/or ID tokens
    - part of a user's initial authentication and authorization flow
    - persistent refresh tokens help improve a user's authentication experience
    - the same refresh token is returned each time the client makes a request to exchange a refresh token for a new access token until the      
      refresh token lifetime expires
    - browser-based applications have a higher risk of a refresh token being compromised when a persistent refresh token is used
    - with single-page applications (SPAs), long-lived refresh tokens aren't suitable,

### Where is it stored?

- The access token is stored in your browser
- To keep them secure, you should always store JWTs inside an HttpOnly cookie