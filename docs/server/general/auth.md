# Authentication

The CloudLabs server requires a JWT token for authentication. The token is provided when a user logins, or registers for an account, whereby the token 
is provided as part of the response.

The JWT token is provided in the form of a HttpOnly cookie, and it will be automatically set by the browser for future requests with the "Set-Cookie" 
header. 

Do note that, the token must not be stored in local storage, as this defeats the purpose of a HttpOnly cookie.

## Architecture

<figure markdown>
  ![Spring Security Architecture](./spring-boot-jwt-arch.png){ width="800" }
  <figcaption>CloudLabs Authentication Architecture (<a href="https://www.bezkoder.com/spring-boot-jwt-mysql-spring-security-architecture">Source</a>)</figcaption>
</figure>

The CloudLabs server authentication is based on the architecture as shown in the image above. A filter is utilized to obtain the JWT token that is
stored as a cookie in the request header. which is then passed on to continue the authentication process.
 
## API Reference

This section documents the API specifications for the CloudLabs server endpoints.

### Login
```
POST: /api/auth/login
```
> Parameters:

>| Name                  | Type         | Description                                               | Required      |
| -----------------------| -------------| --------------------------------------------------------- | ------------- |
| `email`                | string       | A user's email.                                           | Yes           |
| `password`             | string       | A user's password.                                        | Yes           |

>??? quote "Request"
    ```JSON
    {
        "email": "test2@gmail.com",
        "password": "test123"
    }
    ```
>??? quote "Response"
    ```JSON
    {
        "jwt": "eyJhbGciOiJSUzI1NiJ9.eyJyb2xlcyI6W3siaWQiOjIsIm5hbWUiOiJVU0VSIn0seyJpZCI6MywibmFtZSI6IlRVVE9SIn1dLCJmdWxsbmFtZSI6InRlc3QiLCJ1c2VybmFtZSI6InRlc3QyIiwic3ViIjoidGVzdDJAZ21haWwuY29tIiwiaWF0IjoxNjg5MzI4NDY2LCJleHAiOjE2ODkzMjg3NjZ9.gignjXSicupP0g8Fu1cK9cTwiXfPFv-XjuPOXL_fnlZgnABKzTEy4QqtF4FNeJHRA-eNWs-Nh-cANpxsB2LFUmIEA51nslwthu6bL_0D7otB5bXAnuncI6QnsVoSDN0p20jmSWr6cKkHitoimkZAQHjPDBrcFom86qSkHkddAxvCZDPAkBY4VWmG1KNHPczvCScUQ1HjxYHknEHO5TiagWSMYmyLuPhFBbCOrADu0AZQKfgYG8WX8LqT_ACeQ4kMNM-k9O8kiEHbiLVmCu_cDVGxDWzqmT00KZuHsqUi4YyVqbtxUZsa8aEkO6u4M36too0hFSqpaZCGAHcr41oxBQ"
    }
    ```

### Register
```
POST: /api/auth/register
```
> Parameters:

>| Name                  | Type         | Description                                               | Required      |
| -----------------------| -------------| --------------------------------------------------------- | ------------- |
| `fullname`             | string       | A user's fullname.                                        | Yes           |
| `username`             | string       | A user's username.                                        | Yes           |
| `email`                | string       | A user's email.                                           | Yes           |
| `password`             | string       | A user's password.                                        | Yes           |

>??? quote "Request"
    ```JSON
    {
        "fullname": "test",
        "username": "test2",
        "email": "test2@gmail.com",
        "password": "test123"
    }
    ```
>??? quote "Response"
    ```JSON
    {
        "jwt": "eyJhbGciOiJSUzI1NiJ9.eyJyb2xlcyI6W3siaWQiOjIsIm5hbWUiOiJVU0VSIn0seyJpZCI6MywibmFtZSI6IlRVVE9SIn1dLCJmdWxsbmFtZSI6InRlc3QiLCJ1c2VybmFtZSI6InRlc3QyIiwic3ViIjoidGVzdDJAZ21haWwuY29tIiwiaWF0IjoxNjg5MzI4NDY2LCJleHAiOjE2ODkzMjg3NjZ9.gignjXSicupP0g8Fu1cK9cTwiXfPFv-XjuPOXL_fnlZgnABKzTEy4QqtF4FNeJHRA-eNWs-Nh-cANpxsB2LFUmIEA51nslwthu6bL_0D7otB5bXAnuncI6QnsVoSDN0p20jmSWr6cKkHitoimkZAQHjPDBrcFom86qSkHkddAxvCZDPAkBY4VWmG1KNHPczvCScUQ1HjxYHknEHO5TiagWSMYmyLuPhFBbCOrADu0AZQKfgYG8WX8LqT_ACeQ4kMNM-k9O8kiEHbiLVmCu_cDVGxDWzqmT00KZuHsqUi4YyVqbtxUZsa8aEkO6u4M36too0hFSqpaZCGAHcr41oxBQ"
    }
    ```
