
## **Introduction**

APIs are widely used in modern applications, but they also introduce security risks. Since the **2019** release of the **OWASP API Security Top 10**, API-related breaches have increased, and new attack methods have emerged. To address these changes, **OWASP released an updated 2023 version**.

## **Why is API Security Important?**

1. **APIs are Everywhere** – They power web apps, mobile apps, cloud services, and IoT devices.
2. **Increased API Attacks** – Akamai observed **114 million API attacks** in a single day in 2021.
3. **Bug Bounties and Disclosures** – Many security vulnerabilities reported in recent years have targeted APIs.

### **#  Updated Risks**

1. **Excessive Data Exposure & Mass Assignment → Broken Object Property Level Authorization (BOPLA)** – Addressing improper access to object properties.

### **# 5 New Risks in 2023**

1. **Server-Side Request Forgery (SSRF)** – APIs allowing attackers to send unauthorized requests to internal systems.
2. **Unsafe Consumption of APIs** – Trusting third-party APIs without proper validation, leading to security risks.
3. **Broken Object Property Level Authorization (BOPLA)** – Combines excessive data exposure and mass assignment.
4. **Unrestricted Resource Consumption** – APIs allowing excessive resource usage, leading to performance issues.
5. **Unrestricted Access to Sensitive Business Flows** – APIs exposing critical business logic, making them vulnerable to exploitation.

## **2023 OWASP API Security Top 10 List**

|Rank|Risk|Description|
|---|---|---|
|**API1:2023**|**Broken Object Level Authorization (BOLA)**|Unauthorized access to objects due to weak authorization controls.|
|**API2:2023**|**Broken Authentication**|Weak authentication mechanisms allowing unauthorized access.|
|**API3:2023**|**Broken Object Property Level Authorization (BOPLA)**|Exposure of sensitive object properties due to improper access controls.|
|**API4:2023**|**Unrestricted Resource Consumption**|Lack of rate limiting or resource control, leading to DoS attacks.|
|**API5:2023**|**Broken Function Level Authorization (BFLA)**|Users gaining access to privileged functions due to misconfigured authorization.|
|**API6:2023**|**Unrestricted Access to Sensitive Business Flows**|API endpoints exposing critical business logic, allowing attackers to manipulate workflows.|
|**API7:2023**|**Server-Side Request Forgery (SSRF)**|APIs allowing attackers to send malicious internal requests.|
|**API8:2023**|**Security Misconfiguration**|Poorly configured APIs leading to security vulnerabilities.|
|**API9:2023**|**Improper Inventory Management**|Poor API documentation, outdated endpoints, and exposed APIs.|
|**API10:2023**|**Unsafe Consumption of APIs**|Trusting unverified third-party APIs without security validation.|

## **Risk Ratings (2019 vs. 2023)**

The OWASP API Security Project assigns risk scores based on **exploitability, prevalence, detectability, and technical impact**. The **overall score** does not represent absolute risk but serves as a guideline for organizations.

### **Risk Scores Comparison**

|Rank|2019 Risk|Score|2023 Risk|Score|
|---|---|---|---|---|
|API1|BOLA|**11**|BOLA|**11**|
|API2|Broken User Authentication|**10**|Broken Authentication|**11**|
|API3|Excessive Data Exposure|**9**|BOPLA|**10**|
|API4|Lack of Resources & Rate Limiting|**10**|Unrestricted Resource Consumption|**11**|
|API5|BFLA|**8**|BFLA|**11**|
|API6|Mass Assignment|**8**|Unrestricted Access to Sensitive Business Flows|**10**|
|API7|Security Misconfiguration|**11**|Security Misconfiguration|**12**|
|API8|Injection|**11**|SSRF|**10**|
|API9|Improper Assets Management|**10**|Improper Inventory Management|**10**|
|API10|Insufficient Logging & Monitoring|**8**|Unsafe Consumption of APIs|**10**|

## **Conclusion**

The **OWASP API Security Top 10 (2023)** reflects the evolving threat landscape for APIs. Organizations must continuously assess their API security posture and implement **proper authentication, authorization, rate limiting, and security monitoring** to mitigate these risks.

## That's all for Day 1 of learning OWASP TOP 10 API SECURITY ... 
Now I will be continues in these...