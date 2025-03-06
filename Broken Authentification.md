**Broken Authentification**

## Intro

API2:2023 Broken authentication refers to any weakness within the API authentication process. All APIs that contain sensitive information should have some mechanism to authenticate users. Authentication is the process that is used to verify the identity of an API user, whether that user is a person, device, or system. In other words, authentication is the process of verifying that an entity is who that entity claims to be. This verification process is normally done with the use of a username and password, token, and/or multi-factor authentication.

Authentication-related vulnerabilities typically occur when an API provider either doesn’t implement a strong authentication mechanism or implements an authentication process incorrectly.

## [OWASP Attack Vector Description](https://owasp.org/API-Security/editions/2023/en/0xa2-broken-authentication/)

_The authentication mechanism is an easy target for attackers since it's exposed to everyone. Although more advanced technical skills may be required to exploit some authentication issues, exploitation tools are generally available._

## [OWASP Security Weakness Description](https://owasp.org/API-Security/editions/2023/en/0xa2-broken-authentication/)

_Software and security engineers’ misconceptions regarding authentication boundaries and inherent implementation complexity make authentication issues prevalent. Methodologies of detecting broken authentication are available and easy to create._

## [OWASP Impacts Description](https://owasp.org/API-Security/editions/2023/en/0xa2-broken-authentication/)

_Attackers can gain complete control of other users’ accounts in the system, read their personal data, and perform sensitive actions on their behalf. Systems are unlikely to be able to distinguish attackers’ actions from legitimate user ones._

## Summary

Broken Authentication continues to be a significant security issue due to poor password policies, weak authentication mechanisms, and misconfigurations. API authentication is a complex process that is commonly found with most APIs and is necessarily exposed. The impact of broken authentication can lead to an attacker taking control of user accounts, compromising personal data, and conducting sensitive actions like editing healthcare data. The authentication process is often one of the first lines of defense for APIs and when this mechanism is vulnerable, it can lead to a data breach.


**Weak Password Policy**

A weak password policy does not sufficiently protect user accounts by enforcing strong password creation and management.

- Allows users to create simple passwords
- Allows brute force attempts against user accounts
- Allows users to change their password without asking for password confirmation
- Allows users to change their account email without asking for password confirmation
- Discloses token or password in the URL
- GraphQL queries allow for many authentication attempts in a single request
- Lacking authentication for sensitive requests

**Credential Stuffing**

Credential stuffing is a type of attack against authentication where a large number of username and password combinations are attempted. Credentials used in these types of attacks are typically collected from data breaches. 

-  Allows users to brute force many username and password combinations

**Predictable Tokens**

Predictable tokens refer to any token obtained through a weak token generation authentication process. Weak tokens can easily be guessed, deduced, or calculated by an attacker.

- Using incremental or guessable token IDs

**Misconfigured JSON Web Tokens**

JSON Web Tokens (JWTs) are commonly used for API authentication and authorization processes. JWTs provide developers with the flexibility to customize which algorithm is used for signing the token, the key/secret that is used, and the information used in the payload. This customization allows for plenty of room for security misconfigurations to occur.

- API provider accepts unsigned JWT tokens
- API provider does not check JWT expiration
- API provider discloses sensitive information within the encoded JWT payload
- JWT is signed with a weak key