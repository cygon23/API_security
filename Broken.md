## [OWASP Attack Vector Description](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)

_Attackers can exploit API endpoints that are vulnerable to broken object-level authorization by manipulating the ID of an object that is sent within the request. Object IDs can be anything from sequential integers, UUIDs, or generic strings. Regardless of the data type, they are easy to identify in the request target (path or query string parameters), request headers, or even as part of the request payload._

## [OWASP Security Weakness Description](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)

_This has been the most common and impactful attack on APIs. Authorization and access control mechanisms in modern applications are complex and widespread. Even if the application implements a proper infrastructure for authorization checks, developers might forget to use these checks before accessing a sensitive object. Access control detection is not typically amenable to automated static or dynamic testing._

## [OWASP Impacts Description](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)

_Unauthorized access can result in data disclosure to unauthorized parties, data loss, or data manipulation. Unauthorized access to objects can also lead to full account takeover.


## Summary

If an API endpoint does not have sufficient access controls, it will not perform checks to make sure users can only access their own resources. When these controls are missing, User A will be able to obtain User B’s resources via API requests.

APIs use some sort of value, like names or numbers, to identify various objects. When an attacker discovers an API's resource IDs, they will attempt to obtain the resources when unauthenticated or authenticated as a different user. For instance, imagine that an authenticated user, Bruce, sends a GET request to [https://herohospital.com/api/v3/users?id=2727](https://herohospital.com/api/v3/users?id=2727) and receives the following response:

`{`

`"id": "2727",`

`"fname": "Bruce",`

`"lname": "Wayne",`

 `"dob": "1975-02-19",`

`"username": "bman",`

`"diagnosis": "Depression",`

`}`

This poses no problem; Bruce should be able to access Bruce's own information. However, if Bruce is able to access another user’s information then a BOLA vulnerability would be present. A weakness can be tested by using other resource IDs in place of 2727. Say Bruce is able to obtain information about another user by sending a request for [https://herohospital.com/api/v3/users?id=2728](https://herohospital.com/api/v3/users?id=2728) and receives the following response:

`{`

`"id": "2728",`

`"fname": "Harvey",`

`"lname": "Dent",`

 `"dob": "1979-03-30",`

`"username": "twoface",`

`"diagnosis": "Dissociative Identity Disorder",`

`}`

