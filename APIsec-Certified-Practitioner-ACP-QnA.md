# APIsec Certified Practitioner (ACP) — Study Guide & Exam Q&A

> 📚 A complete question-and-answer reference for the **APIsec Certified Practitioner (ACP)** certification exam.  
> Use this to study key API security concepts, authentication, authorization, OWASP Top 10, and documentation best practices.

---

## Table of Contents

- [Authentication & Authorization](#authentication--authorization)
- [OWASP API Security Top 10](#owasp-api-security-top-10)
- [Tokens & OAuth](#tokens--oauth)
- [API Security Concepts](#api-security-concepts)
- [API Documentation](#api-documentation)
- [HTTP & Web Fundamentals](#http--web-fundamentals)

---

## Authentication & Authorization

**Q1. What is the primary difference between authentication and authorization?**  
**A:** Authentication verifies the identity, while authorization controls data/function access.

---

**Q2. What is the primary risk associated with Broken Authentication (OWASP Top 10, A2)?**  
**A:** Attackers can bypass authentication mechanisms to impersonate users and steal sensitive information.

---

**Q3. Which answer best describes how Basic Authentication is achieved?**  
**A:** It sends a username and password (encoded in base64) in the HTTP authorization header.

---

**Q4. What is the primary role of an API key in API authentication?**  
**A:** To identify the application (machine identity) making the request.

---

**Q5. What is a key advantage of token-based authentication over basic authentication in API security?**  
**A:** Tokens can expire and carry additional authorization details.

---

**Q6. Which is most commonly responsible for authentication breaches?**  
**A:** Unsecured endpoints.

---

**Q7. The Instagram password reset flaw is an example of which vulnerability?**  
**A:** Broken Authentication.

---

**Q8. The Peloton breach example demonstrated which API vulnerability?**  
**A:** Broken Authentication due to unsecured endpoints.

---

## OWASP API Security Top 10

**Q9. When was the first edition of the OWASP API Security Top 10 released?**  
**A:** 2019.

---

**Q10. Which organization is responsible for publishing the API Security Top 10?**  
**A:** OWASP (Open Worldwide Application Security Project).

---

**Q11. What is the primary focus of the "OWASP API Security Top 10 and Beyond" course?**  
**A:** Updates on API security vulnerabilities.

---

**Q12. What is a typical vulnerability described by "Broken Function Level Authorization"?**  
**A:** Complex access control policies that allow attackers to gain unauthorized access to user resources or administrative functions.

---

**Q13. What type of vulnerability is characterized by an API allowing users to perform functions (such as transferring funds) that should be restricted to higher-privileged roles?**  
**A:** Broken Function Level Authorization.

---

**Q14. What does the vulnerability "Broken Object Level Authorization (BOLA)" primarily refer to?**  
**A:** User A's ability to access a User B resource.

---

**Q15. What is a characteristic of Broken Object Level Authorization (BOLA) vulnerabilities?**  
**A:** Attackers can manipulate object identifiers to access unauthorized resources or perform actions outside their authorization level.

---

**Q16. In a BOLA vulnerability, what is the main security issue?**  
**A:** Inadequate authorization checks on API resource access.

---

**Q17. Which mitigation is recommended to prevent Broken Object Level Authorization vulnerabilities?**  
**A:** Implementing server-side authorization controls with unpredictable identifiers.

---

**Q18. What vulnerability is illustrated by the Trello example?**  
**A:** Broken Object Property Level Authorization.

---

**Q19. What vulnerability is illustrated by the Venmo example?**  
**A:** The API did not limit the fields returned (Broken Object Property Level Authorization / Excessive Data Exposure).

---

**Q20. Broken Object Property Level Authorization (BOPLA) deals with which of the following issues?**  
**A:** APIs returning excessive data.

---

**Q21. Which risk category in the 2023 update is a combination of Excessive Data Exposure and Mass Assignment?**  
**A:** Broken Object Property Level Authorization.

---

**Q22. Which API security risk involves a lack of safeguards to prevent excessive resource use, potentially leading to denial of service or high operational costs?**  
**A:** Unrestricted Resource Consumption.

---

**Q23. What does "Unrestricted Resource Consumption" refer to in the context of API security?**  
**A:** Attackers exploiting APIs to consume bandwidth, CPU, and memory, leading to DoS or increased costs.

---

**Q24. What is the primary purpose of implementing rate limiting on an API?**  
**A:** To prevent overloading the server and mitigate DoS attacks.

---

**Q25. Rate limiting is important for controlling resource consumption because it:**  
**A:** Helps control server load and reduces costs by preventing abuse.

---

**Q26. What does "Improper Inventory Management" refer to in API security?**  
**A:** Organizations having incomplete view of all APIs.

---

**Q27. What is a common example of Improper Inventory Management in API security?**  
**A:** Outdated or retired API versions in production.

---

**Q28. The Capital One breach was primarily caused by which type of vulnerability?**  
**A:** SSRF, which exploited a misconfigured WAF.

---

**Q29. What is the primary security risk of a Server-Side Request Forgery (SSRF) attack?**  
**A:** It enables unauthorized requests to internal services and networks.

---

**Q30. How does a Server-Side Request Forgery (SSRF) attack typically exploit an application?**  
**A:** By tricking the server into making requests to unintended URLs, such as internal services.

---

**Q31. In the Bumble example, which vulnerability allowed users to upgrade their account without proper payment?**  
**A:** Broken Function Level Authorization.

---

**Q32. The Experian example highlighted a failure in which area?**  
**A:** Security Misconfiguration that allowed unauthorized API access.

---

**Q33. Which of the following is an example of Security Misconfiguration according to the OWASP Top 10?**  
**A:** All of the above (default configurations, unrestricted CORS, no encryption for sensitive data).

---

**Q34. Which of the following is an example of an Injection vulnerability as described in the OWASP Top 10?**  
**A:** A web application failing to check input for SQL commands, allowing an attacker to manipulate database queries.

---

**Q35. Unsafe Consumption of APIs focuses primarily on which of the following?**  
**A:** Mitigating risks from third-party API data.

---

**Q36. Unsafe Consumption of APIs is mostly associated with risks from:**  
**A:** Third-party APIs that are insecure or improperly integrated.

---

**Q37. What is recommended when consuming data from third-party APIs?**  
**A:** Treat third-party APIs with the same security as internally-developed ones.

---

**Q38. Why might traditional web application scanners miss many API vulnerabilities?**  
**A:** They focus on common vulnerabilities, not logic flaws.

---

## Tokens & OAuth

**Q39. Which of the following correctly lists the three parts of a JSON Web Token (JWT)?**  
**A:** Header, Payload, Signature.

---

**Q40. What is the purpose of the 'kid' (Key ID) or 'x5t' field in a JWT header?**  
**A:** To reference the key or certificate used to sign the token.

---

**Q41. What is the "phantom token flow" as described in the course?**  
**A:** Where the gateway converts an opaque token into a JWT.

---

**Q42. What is the main difference between a "by reference" token and a "by value" token?**  
**A:** By value tokens are self-contained, while by reference tokens require an introspection call.

---

**Q43. How do proof-of-possession (POP) tokens differ from bearer tokens?**  
**A:** POP tokens require the sender to prove possession, making them bound to a specific client.

---

**Q44. What is the primary security risk associated with bearer tokens?**  
**A:** They can be used by anyone in possession of the token.

---

**Q45. In OAuth, what is the main function of the Authorization Server?**  
**A:** It issues tokens to clients.

---

**Q46. In OAuth, what purpose do scopes serve?**  
**A:** They define the access privileges granted at an application level.

---

**Q47. What are claims within the context of OAuth tokens?**  
**A:** They provide detailed user identity information for fine-grained authorization.

---

**Q48. Why is a refresh token used in OAuth?**  
**A:** To allow the client to obtain new access tokens without re-prompting the user for credentials.

---

**Q49. What is the purpose of PKCE (Proof Key for Code Exchange) in the OAuth authorization code flow?**  
**A:** To bind the authorization request and token request together.

---

**Q50. Which of the following is NOT one of the four primary actors in the OAuth protocol?**  
**A:** Encryption Server.

---

**Q51. When an API needs to call another API using the received token, which of the following strategies can be employed?**  
**A:** By exchanging the token, embedding a nested token, or sharing the original token.

---

**Q52. Why is it generally discouraged for clients to decode and rely on the contents of access tokens (e.g., JWTs)?**  
**A:** Because the token's internal structure may change over time.

---

## API Security Concepts

**Q53. Which of the following are identified as the three pillars of API Security?**  
**A:** Governance, Monitoring, Testing.

---

**Q54. How does TLS (Transport Layer Security) contribute to API security?**  
**A:** It proves the server's and client's identities over an encrypted channel.

---

**Q55. CORS stands for:**  
**A:** Cross-Origin Resource Sharing.

---

**Q56. Why is CORS ineffective against direct API attacks?**  
**A:** Because it is enforced by browsers, not when an API is accessed directly.

---

**Q57. How does CORS enhance security in web applications?**  
**A:** By allowing browsers to restrict requests from unauthorized origins.

---

**Q58. Why should cookies be treated as untrusted user data?**  
**A:** Because attackers can modify, forge, or harvest cookie data.

---

**Q59. What does the Secure flag on a cookie ensure?**  
**A:** It ensures the cookie is only sent over HTTPS connections.

---

**Q60. What is the primary purpose of the HTTP Only flag on a cookie?**  
**A:** To prevent JavaScript from reading the cookie data.

---

**Q61. What is a path traversal vulnerability?**  
**A:** It allows unintended access to files and directories.

---

**Q62. Which string pattern is most commonly used by attackers in path traversal exploits?**  
**A:** `"../"`

---

**Q63. Which of the following is NOT a common cause of a path traversal vulnerability?**  
**A:** Implementing strict input validation.

---

**Q64. Why is it important to define allowed parameters in your API specification regarding file paths?**  
**A:** To filter and restrict inputs early, preventing invalid file access.

---

**Q65. What is meant by a server information leak?**  
**A:** Any unintended exposure of details about the server's configuration and technology stack.

---

**Q66. Which HTTP header is most commonly exploited to reveal the underlying web server technology?**  
**A:** Server.

---

**Q67. How can you reduce the risk of server information leaks?**  
**A:** Remove or customize server response headers to hide sensitive details.

---

**Q68. Why should error messages sent to end users be generic?**  
**A:** To avoid revealing sensitive internal information that attackers could exploit.

---

**Q69. What does "error disclosure" refer to in API security?**  
**A:** Providing overly detailed error information that may aid attackers.

---

**Q70. Which programming construct, if misused, can lead to unintentional error disclosure?**  
**A:** Try-catch blocks.

---

**Q71. What role does a gateway play in API security?**  
**A:** It inspects requests, validates tokens, and enforces authorization.

---

**Q72. What is one major benefit of using an API gateway?**  
**A:** It centralizes API management and allows consistent policies.

---

**Q73. Which technical tip can help implement effective rate limiting?**  
**A:** Use in-memory solutions like caching to manage throttle counters.

---

**Q74. In the Coinbase example, what was the primary issue that allowed a hacker to sell Ethereum as Bitcoin?**  
**A:** A missing logic validation check on the asset ID.

---

**Q75. Which statement best describes the primary role of APIs in modern applications?**  
**A:** They serve as a bridge for communication between systems and devices.

---

**Q76. How does an API facilitate communication between software applications?**  
**A:** By defining a set of rules and protocols for data exchange.

---

**Q77. During the API design phase, what best practice is recommended to help prevent security vulnerabilities?**  
**A:** Involve security teams early.

---

**Q78. In the course, what does "API sprawl" refer to?**  
**A:** The existence of undocumented APIs leading to duplication.

---

## API Documentation

**Q79. Which specification format is commonly used to create machine- and human-readable API documentation?**  
**A:** OpenAPI.

---

**Q80. Which is NOT a use case for API Documentation?**  
**A:** To examine logs from a previous version of the API.

---

**Q81. Why is it important for API documentation to cater to a broad audience?**  
**A:** To ensure both technical and non-technical stakeholders can understand the API.

---

**Q82. What does the phrase "Developers try, and business buys" imply?**  
**A:** A great developer experience through clear docs can drive overall business adoption.

---

**Q83. What is a key benefit of using a spec-driven approach (e.g., OpenAPI) for API documentation?**  
**A:** It helps keep the documentation in sync with the actual API.

---

**Q84. What is a potential drawback of using hand-curated documentation instead of a spec-driven approach?**  
**A:** It may not easily integrate with automated tools or remain in sync with the API.

---

**Q85. What is one major risk associated with outdated API documentation?**  
**A:** It can lead to confusion and errors when the docs do not match the API's actual behavior.

---

**Q86. Which three high-level types of API documentation were highlighted in the course?**  
**A:** API reference material, conceptual overviews, and workflow guides.

---

**Q87. Which role is particularly valuable for producing high-quality API documentation?**  
**A:** Technical writers who understand APIs.

---

**Q88. How does comprehensive API documentation contribute to improved security?**  
**A:** By defining consistent authentication and authorization practices.

---

**Q89. What is the purpose of having a "security style guide" as part of API documentation?**  
**A:** To enforce consistent security practices across the API.

---

**Q90. Documenting an API early in the development process primarily helps with which of the following?**  
**A:** Enabling early feedback, security reviews, and identifying issues before production.

---

**Q91. In the context of API documentation, what does "governance" refer to?**  
**A:** The enforcement of standards and processes to ensure consistency and security.

---

**Q92. How can multimedia elements (e.g., videos, diagrams) enhance API documentation?**  
**A:** By making complex concepts clearer.

---

**Q93. What is one primary benefit of including interactive "Try it!" features in API docs?**  
**A:** It allows developers to simulate API calls and see live responses.

---

**Q94. How should developers use API documentation when integrating an API?**  
**A:** Read through the endpoints, request formats, and authentication methods before starting integration.

---

**Q95. Why is it important to document error responses in API documentation?**  
**A:** To help developers understand and handle failures.

---

**Q96. Which tool was mentioned as useful for enforcing writing style guidelines in technical documentation?**  
**A:** Vale.

---

## HTTP & Web Fundamentals

**Q97. Which HTTP status code is commonly used to indicate that too many requests have been made?**  
**A:** 429.

---

**Q98. Which HTTP status code is typically used to indicate a client error?**  
**A:** 400.

---

**Q99. Which of the following tools is mentioned as useful for detecting security misconfigurations in APIs?**  
**A:** OWASP ZAP.

---

**Q100. Which of the following professions would benefit most from understanding the OWASP API Top 10?**  
**A:** Penetration testers, to identify and exploit vulnerabilities in APIs.

---

## Key Takeaways

| Concept | Summary |
|---|---|
| **BOLA** | User A accessing User B's resources by manipulating object IDs |
| **BFLA** | Accessing admin/higher-privilege functions without authorization |
| **BOPLA** | Excessive data exposure + mass assignment combined |
| **Unrestricted Resource Consumption** | No rate limiting → DoS risk |
| **Improper Inventory Management** | Old/undocumented API versions still live |
| **SSRF** | Server tricked into making requests to internal services |
| **Phantom Token Flow** | Gateway converts opaque token → JWT |
| **POP Token** | Bound to client; requires proof of possession |
| **Bearer Token** | Anyone who has it can use it |
| **PKCE** | Binds auth request + token request to prevent interception |
| **Three Pillars of API Security** | Governance, Monitoring, Testing |
| **CORS** | Browser-enforced; does NOT protect against direct API calls |

---

> 🔗 **References:**  
> - [OWASP API Security Top 10 (2023)](https://owasp.org/API-Security/)  
> - [APIsec University](https://www.apisecuniversity.com/)
