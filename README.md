# JSON Web Token in JavaScript

![Logo](https://curity.io/images/resources/architect/api-security/jwt.jpg)

I challenged myself during last weeks to implement an authentication on a freshly created API. After digging around, I found that one of the best solution would be JSON Web Tokens. As understanding a concept passes by experimenting it, here is a post describing how to forge such a token in JavaScript.

## What is JSON Web Token (JWT)?

JSON Web Token (JWT) is an easy way to secure an API. When a user authenticates first on a server, using for instance a standard login form, the server creates a token. This token includes some personal data, such as username or email address. Then, this token is signed server-side (to prevent token integrity), and sent back to the user. Within each next request, user sends the token to establish emitter identity.

<img src="https://blog.openreplay.com/static/eae220053d72e95dbe803496c8aac458/d2d42/s_1048F41B3AC814B927887FF3C86602B940107555916A37D85A0BACB9135A34EA_1606545347515_jwt.png" alt="" width="100%" />

   ### JSON Web Token is composed of three main parts:
   
   - Header: normalized structure specifying how token is signed (generally using HMAC SHA-256 algorithm)
   - Free set of claims embedding whatever you want: username, email, roles, expiration date, etc.
   - Signature ensuring data integrity

   ## Creating a JSON Web Token in JavaScript
  
  JSON Web Tokens may be resumed by the following equations:
  
  ```javascript
   unsignedToken = base64url(header) + "." + base64url(data)
   JWT = unsignedToken + "." + base64url(HMAC256(unsignedToken, secret))
   ```
