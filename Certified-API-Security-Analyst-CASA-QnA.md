# Certified API Security Analyst (CASA) — Study Guide & Exam Q&A

> 📚 A complete question-and-answer reference for the **Certified API Security Analyst (CASA)** certification exam.  
> This guide covers OWASP API Security Top 10 (2019 & 2023), real-world breach examples, vulnerability identification, and mitigation strategies.

---

## Table of Contents

- [OWASP Foundations](#owasp-foundations)
- [Broken Object Level Authorization (BOLA)](#broken-object-level-authorization-bola)
- [Broken Authentication](#broken-authentication)
- [Broken Object Property Level Authorization (BOPLA)](#broken-object-property-level-authorization-bopla)
- [Unrestricted Resource Consumption](#unrestricted-resource-consumption)
- [Broken Function Level Authorization (BFLA)](#broken-function-level-authorization-bfla)
- [Unrestricted Access to Sensitive Business Flows](#unrestricted-access-to-sensitive-business-flows)
- [Server Side Request Forgery (SSRF)](#server-side-request-forgery-ssrf)
- [Security Misconfiguration](#security-misconfiguration)
- [Improper Inventory Management](#improper-inventory-management)
- [Unsafe Consumption of APIs](#unsafe-consumption-of-apis)
- [Beyond the Top 10](#beyond-the-top-10)
- [Real-World Breach Examples](#real-world-breach-examples)
- [Vulnerability Identification by Request](#vulnerability-identification-by-request)

---

## OWASP Foundations

**Q1. What is the classic equation for risk?**  
**A:** Likelihood multiplied by impact.

---

**Q2. What is the purpose of mapping the OWASP API Security Top 10 risks to external sources like CWE and NIST?**  
**A:** To provide additional insight and depth into the identified risks.

---

**Q3. Which OWASP security project list was recommended for use by OWASP leadership to hack or protect an API developed in 2018?**  
**A:** OWASP API Security Top Ten (2019).

---

**Q4. Which two risk categories previously on the OWASP API Security Top Ten (2019) were removed from the 2023 list?**  
**A:** Injection AND Insufficient Logging and Monitoring.

---

**Q5. Which risk category was a completely new addition to the OWASP API Security Top Ten (2023)?**  
**A:** Unrestricted Access to Sensitive Business Flows.

---

**Q6. Broken Object Property Level Authorization is a combination of which two OWASP API Security Top Ten (2019) risk categories?**  
**A:** Excessive Data Exposure and Mass Assignment.

---

**Q7. What is one common cause of business logic vulnerabilities?**  
**A:** Assumptions that API consumers will follow directions and be trustworthy.

---

**Q8. Which OWASP API Security Top Ten (2023) vulnerability is most likely to be detected by an automated vulnerability scanner?**  
**A:** Security Misconfiguration.

---

## Broken Object Level Authorization (BOLA)

**Q9. What is a Broken Object Level Authorization vulnerability?**  
**A:** A situation where an API does not have sufficient controls to enforce authorization, allowing an attacker to access sensitive data of other users by manipulating object IDs.

---

**Q10. Which of the following statements is true about Broken Object Level Authorization?**  
**A:** BOLA vulnerabilities are common, easily exploitable, and often require minimal technical skills to discover.

---

**Q11. What makes an API vulnerable to a Broken Object Level Authorization attack?**  
**A:** If an API does not have sufficient access controls and does not perform checks to ensure that users can only access their own resources.

---

**Q12. Which of the following is a recommended measure to prevent a Broken Object Level Authorization attack?**  
**A:** Implement a proper authorization mechanism that relies on the user policies and hierarchy.

---

**Q13. Which vulnerability is present if UserA is able to receive healthcare information of other users from the following requests?**
```
POST /api/v1/user/healthdata/
Token: UserA_Token
{"account": "UserB"}
```
**A:** Broken Object Level Authorization.

---

**Q14. Which of the following risk categories is present if an attacker is able to gain unauthorized access to the sensitive data of other users?**  
**A:** Broken Object Level Authorization.

---

**Q15. Which of the following Attack Vector Descriptions describes BOLA?**  
> "Attackers can exploit API endpoints that are vulnerable to broken object-level authorization by manipulating the ID of an object that is sent within the request."

**A:** Broken Object Level Authorization.

---

## Broken Authentication

**Q16. What does Broken Authentication refer to in the context of API security?**  
**A:** It pertains to any weakness within the API authentication process that allows unauthorized access.

---

**Q17. Which of the following is an example of broken authentication?**  
**A:** An API allowing users to create simple passwords and allowing brute force attempts against user accounts.

---

**Q18. An API that leverages a JSON Web Token with a weak key is affected by which vulnerability?**  
**A:** Broken Authentication.

---

**Q19. An attacker being able to create and sign their own JSON Web Tokens is most associated with which vulnerability?**  
**A:** Broken Authentication.

---

**Q20. Which of the following increases the likelihood of Broken Authentication?**  
**A:** Creating a positive user experience by allowing users the freedom to use any password.

---

**Q21. Which of the following decreases the likelihood of Broken Authentication?**  
**A:** Requiring re-authentication for sensitive operations.

---

**Q22. If the following GraphQL request batching attack was successful, which vulnerability would be present?**
```json
POST /graphql
[
  {"query":"mutation{login(email:'user@email.com', password:'654321'){token}}"},
  {"query":"mutation{login(email:'user@email.com', password:'monkey'){token}}"},
  ...
]
```
**A:** Broken Authentication (brute force via GraphQL batching).

---

**Q23. Which OWASP API Security Top Ten (2019) risk category represents the inability of an organization to review the requests an attacker used to breach their data?**  
**A:** Insufficient Logging and Monitoring.

---

## Broken Object Property Level Authorization (BOPLA)

**Q24. Which vulnerability is present if an API endpoint exposes properties of an object that are considered sensitive and should not be read by the user?**  
**A:** Broken Object Property Level Authorization.

---

**Q25. Which vulnerability is present if an API endpoint allows a user to change, add/or delete the value of a sensitive object's property which the user should not be able to access?**  
**A:** Broken Object Property Level Authorization.

---

**Q26. Which of the following statements is true about Broken Object Property Level Authorization (BOPLA)?**  
**A:** It is related to the security weakness of "Excessive Data Exposure" and "Mass Assignment."

---

**Q27. What does the term "Excessive Data Exposure" refer to in the context of API security?**  
**A:** It refers to sending more data than is required to the client through the API response.

---

**Q28. What is the potential security threat of "Mass Assignment" in API security?**  
**A:** It could allow a user to alter sensitive object properties that they should not have access to.

---

**Q29. Which vulnerability is present in the following response?**
```json
{
  "userid": "1111",
  "uname": "thomthetank",
  "email": "thomas@tank.com",
  "administrator": {
    "name": "Diesel",
    "privilege": "administrator"
  }
}
```
**A:** Broken Object Property Level Authorization (exposes admin object properties to a non-admin user).

---

**Q30. Which of the following risk categories is present if an attacker is able to gain unauthorized access to private object properties that disclose sensitive data?**  
**A:** Broken Object Property Level Authorization.

---

## Unrestricted Resource Consumption

**Q31. Which of the following risk categories is most associated with being vulnerable to a denial of service attack?**  
**A:** Unrestricted Resource Consumption.

---

**Q32. According to OWASP, what is the primary consequence of not implementing API rate limiting?**  
**A:** Denial of service due to resource starvation or a negative impact on the service provider's billing.

---

**Q33. What is the primary risk associated with Unrestricted Resource Consumption in API security?**  
**A:** Denial of Service attacks and increased operational costs.

---

**Q34. Which of the following preventive measures would NOT help to protect against Unrestricted Resource Consumption?**  
**A:** Disabling server-side validation for query string and request body parameters.

---

**Q35. If an API provider does not control the number of requests that can be made by a consumer then the provider is vulnerable to which of the following risks?**  
**A:** Unrestricted Resource Consumption.

---

**Q36. Which of the following decreases the likelihood of Unrestricted Resource Consumption?**  
**A:** Implementing strong rate limits.

---

**Q37. Which of the following risk categories is present if an attacker is able to continuously upload large files and increase the cloud storage needs of an API provider?**  
**A:** Unrestricted Resource Consumption.

---

**Q38. The following OWASP preventative recommendation is best applied to which risk category?**
> "Define and enforce maximum size of data on all incoming parameters and payloads such as maximum length for strings and maximum number of elements in arrays."

**A:** Unrestricted Resource Consumption.

---

## Broken Function Level Authorization (BFLA)

**Q39. Which of the following best describes what Broken Function Level Authorization is in the context of API security?**  
**A:** A vulnerability where API functions have insufficient access controls, potentially allowing an attacker to perform actions of other roles, including administrative actions.

---

**Q40. Which vulnerability allows an attacker to leverage the functionality of user groups that the attacker should not have access to?**  
**A:** Broken Function Level Authorization.

---

**Q41. Which vulnerability allows a non-admin attacker to make the following request?**
```
DELETE api/v1/admin/user/hapihacker
```
**A:** Broken Function Level Authorization.

---

**Q42. What are the potential impacts of Broken Function Level Authorization for API security?**  
**A:** It can lead to data disclosure, data loss, data corruption, or service disruption.

---

**Q43. Which of the following is NOT a recommended preventive measure for Broken Function Level Authorization?**  
**A:** Ensure that all access is allowed by default, requiring explicit denials to specific roles for access to every function.

---

**Q44. From 2019 to 2022, the Texas Department of Insurance exposed the personal information of 1.8 million people. The affected endpoint allowed authenticated public users with the ability to access sensitive functions of the API. Which risk is relevant?**  
**A:** Broken Function Level Authorization.

---

## Unrestricted Access to Sensitive Business Flows

**Q45. What does Unrestricted Access to Sensitive Business Flows refer to in API security?**  
**A:** The risk of an attacker identifying and exploiting API-driven workflows to obstruct other users or harm the business.

---

**Q46. Which vulnerability is most likely to be leveraged by scalpers to take advantage of product purchase processes?**  
**A:** Unrestricted Access to Sensitive Business Flows.

---

**Q47. How can Unrestricted Access to Sensitive Business Flows impact a business?**  
**A:** It might prevent legitimate users from purchasing a product or lead to inflation in the internal economy of a game.

---

**Q48. Which of the following is NOT a recommended preventative measure against Unrestricted Access to Sensitive Business Flows?**  
**A:** Allow unrestricted access to APIs that are consumed by trusted partners.

---

**Q49. According to OWASP, which of the following answers is a potential impact of not restricting access to sensitive business flows?**  
**A:** It could prevent consumers from being able to purchase a product.

---

**Q50. The following OWASP preventative recommendation is best applied to which risk category?**
> "Non-human patterns: analyze the user flow to detect non-human patterns (e.g. the user accessed the 'add to cart' and 'complete purchase' functions in less than one second)"

**A:** Unrestricted Access to Sensitive Business Flows.

---

**Q51. Which of the following risk categories is present if an attacker is able to use an API provider's request structure to obstruct other users from being able to purchase a product?**  
**A:** Unrestricted Access to Sensitive Business Flows.

---

## Server Side Request Forgery (SSRF)

**Q52. What does a Server Side Request Forgery vulnerability refer to?**  
**A:** A situation where a user can control the remote resources retrieved by an application.

---

**Q53. What are the two general types of SSRF?**  
**A:** In-Band and Out of Band (Blind).

---

**Q54. What is the difference between In-Band SSRF and Out of Band (Blind) SSRF?**  
**A:** In-Band SSRF means the server responds with the resources specified by the end user, while Blind SSRF does not send a response back to the attacker.

---

**Q55. Which is a preventative measure against SSRF?**  
**A:** Isolate the resource fetching mechanism and use allow lists of remote origins.

---

**Q56. Which of the following is NOT a recommended preventative measure against Server Side Request Forgery?**  
**A:** Send sanitized raw responses to clients.

---

**Q57. Which vulnerability is present in the following request?**
```
POST api/v1/store/products
{"updated":"http://localhost/webstore/jwt/secret"}

Response: {"jwt_secret":"jwt4w"}
```
**A:** Server Side Request Forgery.

---

**Q58. Which OWASP Attack Vector Description describes SSRF?**  
> "Exploitation requires the attacker to find an API endpoint that accesses a URI that's provided by the client."

**A:** Server Side Request Forgery.

---

## Security Misconfiguration

**Q59. Which vulnerability includes misconfigured headers, misconfigured transit encryption, the use of default accounts, the acceptance of unnecessary HTTP methods, a lack of input sanitization, and verbose error messaging?**  
**A:** Security Misconfiguration.

---

**Q60. Which OWASP API Security Top Ten (2023) vulnerability is most associated with the exploitation of unpatched flaws?**  
**A:** Security Misconfiguration.

---

**Q61. Which vulnerability is considered a gateway to other API security vulnerabilities?**  
**A:** Improper Inventory Management.  
*(Note: Security Misconfiguration is closely related but Improper Inventory Management is the correct answer per OWASP.)*

---

**Q62. According to the OWASP preventative measures, what steps should be included in the API life cycle to mitigate security misconfiguration?**  
**A:** A repeatable hardening process, a review and update task for configurations, and an automated process to assess the effectiveness of configurations and settings.

---

**Q63. Which OWASP Attack Vector Description describes Security Misconfiguration?**  
> "Attackers will often attempt to find unpatched flaws, common endpoints, or unprotected files and directories to gain unauthorized access or knowledge of the system."

**A:** Security Misconfiguration.

---

## Improper Inventory Management

**Q64. Which of the following best describes the security weakness of improper inventory management in APIs?**  
**A:** Unsupported or non-production API versions being exposed, often lacking necessary security measures.

---

**Q65. What are common consequences of improper inventory management vulnerabilities in APIs?**  
**A:** Exposure to other vulnerabilities like excessive data exposure, mass assignment, and API injection.

---

**Q66. Which of the following increases the likelihood of Improper Inventory Management?**  
**A:** Providing a large number of versions of a single API.

---

**Q67. Which of the following risk categories is present if an attacker is able to use a deprecated endpoint to get access to administrative functions?**  
**A:** Improper Inventory Management.

---

**Q68. The following OWASP preventative recommendation is best applied to which risk category?**
> "Inventory all API hosts and document important aspects of each one of them, focusing on the API environment (e.g., production, staging, test, development)..."

**A:** Improper Inventory Management.

---

**Q69. What are some of the preventative measures that can be taken against improper inventory management in APIs?**  
**A:** Automatic generation and updating of API documentation, maintaining an inventory of all API hosts and versions, and using API security firewalls for all exposed versions.

---

**Q70. In the course, what does "API sprawl" most closely relate to?**  
**A:** Improper Inventory Management — undocumented/forgotten APIs still live in production.

---

## Unsafe Consumption of APIs

**Q71. Which OWASP API Security Top Ten (2023) category is the only one that focuses more on the API consumer than the API provider?**  
**A:** Unsafe Consumption of APIs.

---

**Q72. Which of the following best explains why Unsafe Consumption of APIs is particularly risky for an API consumer?**  
**A:** If a third-party API provider is compromised, the insecure API connection back to the consumer becomes a new attack vector.

---

**Q73. What common weakness tends to be present in the consumption of APIs that makes it unsafe?**  
**A:** Excessive trust and lack of verification of endpoints interacting with external or third-party APIs, along with weaker security requirements.

---

**Q74. Which of the following increases the likelihood of Unsafe Consumption of APIs?**  
**A:** Trusting the security of a third-party API provider because they are well known.

---

**Q75. Which of the following is a preventative measure that can be taken to protect against unsafe consumption of APIs?**  
**A:** Validate and sanitize data received from integrated APIs.

---

**Q76. Which OWASP Attack Vector Description describes Unsafe Consumption of APIs?**  
> "Exploiting this issue requires attackers to identify and potentially compromise other APIs/services the target API integrated with."

**A:** Unsafe Consumption of APIs.

---

## Beyond the Top 10

**Q77. Which OWASP API Security Top Ten (2019) represents the ability of an attacker to successfully query a SQL database using a public API?**  
**A:** Injection.

---

**Q78. Which of the following are recommended preventative measures against injection vulnerabilities?**  
**A:** Sanitize client-provided data.

---

**Q79. Which of the following best describes an injection vulnerability in the context of APIs?**  
**A:** An attacker is able to send commands through the API that are executed by the underlying systems, due to a lack of input sanitization.

---

**Q80. What are some of the potential impacts of successful injection attacks as described by OWASP (2019)?**  
**A:** Information disclosure, data loss, Denial of Service (DoS), or complete host takeover.

---

**Q81. Which OWASP API Security Top Ten (2019) risk category represents the inability of an organization to review the requests an attacker used to breach their data?**  
**A:** Insufficient Logging and Monitoring.

---

**Q82. Why is logging and monitoring a crucial part of API security?**  
**A:** It provides patterns of API usage and can detect suspicious activities.

---

**Q83. What are some of the consequences of insufficient logging and monitoring in APIs?**  
**A:** Attackers can abuse systems without being noticed.

---

**Q84. What actions should an organization take to enhance the logging and monitoring of their APIs?**  
**A:** Use a Security Information and Event Management (SIEM) system.

---

**Q85. Which vulnerability, beyond the OWASP API Security Top Ten (2023), represents a weakness where an API's features can be leveraged against the API in an attack?**  
**A:** Business Logic Flaws.

---

**Q86. What makes the identification and mitigation of business logic vulnerabilities particularly challenging?**  
**A:** They are unique to each application and exploit the normal intended functioning of an application's business processes, often requiring specific knowledge of the application's functionality.

---

**Q87. How can an organization mitigate the risk of business logic vulnerabilities in their APIs?**  
**A:** Using a threat modeling approach to understand how business processes might be abused.

---

## Real-World Breach Examples

| Breach | Vulnerability | Key Detail |
|---|---|---|
| **Optus (2022)** | Broken Authentication | Attacker accessed ~10M records with no API token/key |
| **Parler (2021)** | Broken Authentication | Anyone could make requests to URLs storing private data |
| **Texas Dept. of Insurance (2019–2022)** | Broken Function Level Authorization | Authenticated public users accessed sensitive API functions |
| **US Patent & Trademark Office (2020–2023)** | Improper Inventory Management | Unknown endpoint leaked home addresses of 61,000 people |
| **Capital One** | SSRF | Misconfigured WAF exploited via SSRF |
| **Coinbase** | Business Logic Flaw | Missing logic validation allowed selling ETH as BTC |

---

## Vulnerability Identification by Request

**Q88. Based on these consecutive requests, which vulnerability is most likely being tested for?**
```
GET /api/v3/user/profile/3111
GET /api/v3/user/profile/3211
GET /api/v3/user/profile/3311
```
**A:** Broken Object Level Authorization (incrementing user IDs to access other users' profiles).

---

**Q89. Based on these consecutive requests, which vulnerability is most likely being tested for?**
```
GET /api/mobile/user/profile/3321
GET /api/test/user/profile/3321
GET /api/preprod/user/profile/3321
```
**A:** Improper Inventory Management (testing different API environments/versions).

---

**Q90. Based on these consecutive requests, which vulnerability is most likely being tested for?**
```
POST /api/user/profile/3111
POST /api/admin/profile/3111
POST /api/administrator/profile/3111
```
**A:** Broken Function Level Authorization (probing for admin endpoints).

---

## Key Takeaways

| Vulnerability | Core Concept | Key Mitigation |
|---|---|---|
| **BOLA** | Access other users' data via object ID manipulation | Server-side auth checks + unpredictable IDs |
| **Broken Auth** | Bypass authentication mechanisms | Strong passwords, no brute force, MFA |
| **BOPLA** | Read/write sensitive object properties | Filter what properties are returned/accepted |
| **Unrestricted Resource Consumption** | DoS via excessive API requests | Rate limiting, payload size limits |
| **BFLA** | Access admin/privileged functions | Role-based access control (RBAC) |
| **Sensitive Business Flows** | Abuse purchase/game flows via automation | Device fingerprinting, human detection |
| **SSRF** | Server fetches attacker-controlled URLs | Allow lists, isolate fetching mechanism |
| **Security Misconfiguration** | Default configs, verbose errors, open CORS | Hardening process, automated config review |
| **Improper Inventory** | Old/shadow APIs still live | Full API inventory, retire old versions |
| **Unsafe API Consumption** | Trust third-party APIs blindly | Validate + sanitize all third-party data |
| **Injection** | Commands executed via unsanitized input | Input sanitization, parameterized queries |
| **Business Logic Flaws** | Exploit intended app workflows | Threat modeling, non-human pattern detection |

---

> 🔗 **References:**  
> - [OWASP API Security Top 10 (2023)](https://owasp.org/API-Security/)  
> - [OWASP API Security Top 10 (2019)](https://owasp.org/www-project-api-security/)  
> - [APIsec University - CASA](https://www.apisecuniversity.com/)
