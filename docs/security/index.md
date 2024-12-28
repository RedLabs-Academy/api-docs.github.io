---
layout: page
title: Security Testing Guidelines
---

<style>
    .image-container {
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .transparent-image {
        width: 20%;
        background: none;
    }
</style>

<div class="image-container">
    <img src="/img/Logo.png" alt="RedLabs Logo" class="transparent-image" />
</div>

## Introduction

Welcome to the **Security Testing Guidelines** for the APIs provided by **RedLabs Academy**. This document outlines the scope of security testing, the accepted vulnerabilities, and the testing regulations for interacting with RedLabs Academy APIs. By following these guidelines, testers can ensure they are operating within authorized and ethical boundaries while helping improve the security posture of RedLabs Academy.

## In Scope

The following APIs are within the scope for security testing:

1. **/auth (POST)**: Handles user authentication. Testing should focus on identifying vulnerabilities related to session management, token handling, and authentication bypass.

2. **/api/v1/course (GET, POST, PATCH, DELETE)**: API for managing courses. Testing should include testing for unauthorized access, input validation, and course management privileges.

3. **/api/v1/course/:course-name (GET, POST, PATCH, DELETE)**: Endpoint for specific course management. Ensure that the correct authorization checks are in place for managing individual courses.

4. **/api/v1/users (GET)**: API to retrieve user details. Testing should focus on ensuring that unauthorized users cannot access sensitive user data.

5. **/api/v1/:email (GET, DELETE, PATCH)**: User-specific API. This should include testing user-specific data access, modification, and deletion controls.

## Accepted Vulnerabilities

The focus of our security testing is on **critical issues** that can significantly compromise the integrity, confidentiality, and availability of the system. These vulnerabilities include but are not limited to:

1. **Exposure of Sensitive Information**: Any situation where sensitive data such as passwords, personal identifiable information (PII), or tokens are exposed inappropriately.
2. **Escalating Roles**: Testing for privilege escalation where a user can elevate their privileges beyond what is authorized.
3. **Bypassing Protected Routes**: Identifying routes that do not properly enforce authentication and authorization checks, allowing unauthorized access.
4. **Session Token Reuse**: Ensuring that session tokens are properly invalidated after logout or expiration and cannot be reused maliciously.
5. **Weak Cryptographic Algorithms**: Identifying weak or deprecated cryptographic algorithms in use (e.g., MD5 or SHA1).
6. **Reuse of Reset Tokens**: Ensuring that password reset tokens cannot be reused or guessed, protecting users from malicious resets.

We encourage security testers to prioritize these types of vulnerabilities when conducting testing.

## Out of Scope

The following activities are **out of scope** for security testing:

1. **Testing on Production Systems**: Security testing should only be conducted on designated testing environments or development environments. Unauthorized testing in live production environments is prohibited.
2. **Non-API Endpoints**: Any endpoints or resources that are not related to the documented API endpoints are out of scope.
3. **Internal Administrative Systems**: Administrative and backend systems not exposed to API endpoints should not be targeted during testing.
4. **Accessing Non-Authorized User Accounts**: Any attempt to access user accounts or data that are not part of the testing authorization is prohibited.
5. **Infrastructure Attacks**: Attacks targeting the underlying infrastructure, servers, and networks (e.g., attacking the database server or the network layer) are out of scope unless explicitly permitted.

Please make sure to respect these boundaries during testing to ensure ethical and lawful conduct.

## Prohibited Testing

The following types of attacks and testing methodologies are **strictly prohibited**:

1. **Physical Attacks**: Gaining unauthorized physical access to RedLabs Academy systems or facilities.
2. **Social Engineering**: Any attempt to manipulate or deceive individuals to disclose confidential information or credentials, including phishing, vishing, or baiting.
3. **Tailgating**: Following an authorized individual into a restricted area without proper clearance.
4. **Denial of Service (DoS)**: Overloading the system to make services unavailable, including through resource exhaustion.
5. **Distributed Denial of Service (DDoS)**: Coordinated attacks from multiple sources designed to overwhelm the system or infrastructure.
6. **Brute Force Attacks**: Attempting to guess passwords or tokens using automated tools without explicit permission.
7. **Cross-Site Scripting (XSS)**: Injections of malicious scripts into web applications without prior authorization to do so.
8. **Cross-Site Request Forgery (CSRF)**: Attacks designed to trick users into executing malicious requests in the context of their authentication.

These activities are not only unethical but may also be illegal and can result in legal actions if performed without proper authorization.

## Reporting Procedure

If you discover any security vulnerabilities during your testing, please report them as soon as possible through the following procedure:

- **Security Contact**: Rahul Dixit
- **Email**: [cybereyerahul@gmail.com](mailto:cybereyerahul@gmail.com)

Your reports will be handled with the utmost care and confidentiality. We appreciate your efforts in helping secure RedLabs Academy’s systems.

## Confidential Statement

All information related to security testing, vulnerabilities, and testing results must be treated as **confidential**. Unauthorized disclosure of any findings, testing methods, or system vulnerabilities may lead to legal actions. By conducting security testing, you agree to maintain the confidentiality of the information and follow the guidelines as outlined in this document.

We trust that security testers will act responsibly and ethically, helping RedLabs Academy maintain the integrity and security of its systems and services.

Thank you for your commitment to ensuring the security and privacy of RedLabs Academy’s platforms!
