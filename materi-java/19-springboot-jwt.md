---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
marp: true
---

![bg left:40% 60%](./../images/rawlabs-academy-logo.png)

# **Spring Boot Security JWT**
Rawlabs Academy

---
<style scoped>
    p {
        font-size: 0.9rem;
    }
</style>
### JSON Web Token **(JWT)**

JWT is an open standard **(RFC 7519)** that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. 

This information can be verified and trusted because it is digitally signed. 

JWTs can be signed using a secret (with the **HMAC** algorithm) or a public/private key pair using **RSA** or **ECDSA**.

More detail information please read the official documentation at [JWT.io](https://jwt.io/introduction).

---
#### Before Implement JWT
![bg center 50%](../images/materi-java/springboot-jwt/user-table.png)

---
![bg right:60% 90%](../images/materi-java/springboot-jwt/pom.png)
### Dependency
- `spring-boot-starter-security`
- `jjwt-api`
- `jjwt-impl`
- `jjwt-jackson`

---
### Project Structure
![left h:500](../images/materi-java/springboot-jwt/project-structure.png)

---
<style scoped>
    ul {
        font-size: 0.9rem;
    }
</style>
### Spring Boot Properties
![left h:250](../images/materi-java/springboot-jwt/springboot-properties.png)

- **`jwt.token.validity`** value in miliseconds
- **`jwt.signing.key`** is random string value that should be `>=` 256 bit. At least **50 characters**
- Generate random string at [Random string generator](59mNST6kvqfzu2izgFAUMUPNgbheY9PigTZB6KW5LL9XKaqKRP)

---
<!-- _class: lead -->
# Data Transfer Object
# **(DTO)**

---
\
![left h:450](../images/materi-java/springboot-jwt/login-request-dto.png) ![left h:430](../images/materi-java/springboot-jwt/login-response-dto.png)

---
![bg right:50% 90%](../images/materi-java/springboot-jwt/user-dao.png)
<style scoped>
    ul, p {
        font-size: 0.8rem;
    }
</style>
### **User DAO**
`User` class will implement methods of `UserDetail` class like :
- `getAuthorities()` set return to **null**
- `isAccountNonExpired()` set return to **true**
- `isAccountNonLocked()` set return to **true**
- `isCredentialsNonExpired()` set return to **true**
- `isEnabled()` set return to **true**

---
### User Repository
![left w:1150](../images/materi-java/springboot-jwt/user-repository.png)

---
![bg right:65% 90%](../images/materi-java/springboot-jwt/user-service.png)
<style scoped>
    p {
        font-size: 0.8rem;
    }
</style>
### User **Service**
`UserService` implemented the `UserDetailService` interface to **override** the method `loadUserByUsername()` to be used for login validation.

---
<!-- _class: lead -->
# Component
# **Package**

---
![bg right:50% 80%](../images/materi-java/springboot-jwt/token-provider.png)
<style scoped>
    p {
        font-size: 0.9rem;
    }
</style>
### Token Provider
TokenProvider is a utility class as component which can be used to generate token, validate token and get token claims

Annotation `@Value` is used to get `application.properties` value

---
### Unauthorized Entry Point
![left h:300](../images/materi-java/springboot-jwt/authorization-entry-point.png)

`UnauthorizationEntryPoint` is used for error handling when get unauthorized client.

---
<!-- _class: lead -->
# Configuration
# **Package**

---
![bg center 50%](../images/materi-java/springboot-jwt/jwt-authentication-filter.png)

---
![bg center 45%](../images/materi-java/springboot-jwt/web-security-config.png)

---
![bg right:60% 90%](../images/materi-java/springboot-jwt/login-service.png)
<style scoped>
    p {
        font-size: 0.8rem;
    }
</style>
### Login **Service**
The flow is user will be login and call method `doLogin()` and check if password has mathced from database user. 

It will returning error when password does not match.

---
### Update API Docs **Configuration**
![left h:500](../images/materi-java/springboot-jwt/open-api-configuration.png)

---
### Login **Controller**
![center h:500](../images/materi-java/springboot-jwt/login-controller.png)

---
### Update Authenticated Controller
![left h:450](../images/materi-java/springboot-jwt/book-controller.png)

---
### Testing
When everything is done, do testing with inject data to database `username` and `password` and then hit endpoint using authorization.

---
 <!-- _class: lead -->
![w:1000](./../images/thank-you.png)