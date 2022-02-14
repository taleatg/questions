# Broken Authntication

### Links
[OWASP: Broken Authentication](https://owasp.org/www-project-top-ten/2017/A2_2017-Broken_Authentication)
[Implement Digital Identity](https://owasp.org/www-project-proactive-controls/v3/en/c6-digital-identity)
[Test Role Definitions](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/03-Identity_Management_Testing/01-Test_Role_Definitions)
[Test User Registration Process](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/03-Identity_Management_Testing/02-Test_User_Registration_Process)
[Test Account Provisioning Process](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/03-Identity_Management_Testing/03-Test_Account_Provisioning_Process)

### Questions

<details>
  <summary>What is broken authentication risk?</summary>

Application authentication and session management functionality often have an implementation that allows attackers to compromise passwords, keys, session tokens, etc.

Confirmation of the user identity, authentication, and session management is critical to protect against authentication-related attacks. There may be authentication weaknesses if the application:

* Permit automated attacks such as credential stuffing, where the attacker has a list of valid usernames and passwords.

* Permit brute force or other automated attacks.

* Permit default, weak, or well-known passwords, such as Password1 or admin/admin.

* Use weak or ineffective credential recovery and forget password processes, such as knowledge-based answers, which cannot be made safe.

* Uses plain text, encrypted, or weakly hashed passwords (see A3:2017-Sensitive Data Exposure).

* Have missing or ineffective multi-factor authentication.

* Exposes Session IDs in the URL (e.g., URL rewriting).

* Do not rotate Session IDs after successful login.

* Do not invalidate Session IDs. User sessions or authentication tokens.

Solving:

* Where possible, implement multi-factor authentication to prevent credential stuffing, brute force, and stolen credential reuse attacks.

* Do not ship or deploy with any default credentials, particularly for admin users.

* Implement weak password checks, such as testing new or changed passwords against a list of the top 10000 worst passwords.

* Align password length, complexity and rotation policies.

* Ensure registration, credential recovery, and API pathways have protection against account enumeration attacks by using the same messages for all outcomes.

* Limit or increasingly delay failed login attempts. Log all failures and alert administrators when credential stuffing, brute force, or other attacks are detected.

* Use a server-side, secure, built-in session manager that generates a new random session ID with high entropy after login. Session IDs should not be in the URL, be securely stored and invalidated after logout, idle, and absolute timeouts.

</details>

<details>
  <summary>What is digital identity?</summary>

Digital Identity is the unique representation of a user (or another subject) as they engage in an online transaction.

</details>

<details>
  <summary>What is authentication?</summary>

Authentication is the process of verifying that an individual or entity is who they claim to be.

</details>

<details>
  <summary>What is session management?</summary>

Session management is a process when a server maintains the state of the user authentication data. So users may continue to use the system without re-authentication.

</details>

<details>
  <summary>What are authentication Levels?</summary>

* Password
* Multi-factor authentication
* Cryptographic based authentication

</details>

<details>
  <summary>How do test role definitions?</summary>

* Roles identification:

The tester should start by identifying the application roles. It is possible to use application documentation, guidance for developers or administrators, comments. Moreover, he could fuzz roles through cookie variables, account variables, hidden directories or files, switching to well-known users.

* Switching to available roles:

After identifying possible attack vectors, the tester needs to test and validate that they can access the available roles.

* Review roles permissions:

After gaining access to the roles on the system, the tester must understand the permissions provided for each user role.

</details>

<details>
  <summary>How test user registration process?</summary>

Objectives:
* Verify that the identity requirements for user registration flow with business and security requirements;
* Validate the registration process.

For testing, answer to following questions:
1. Can anyone register for access?
2. Are registrations vetted by a human prior to provisioning, or are they automatically granted if the criteria are met?
3. Can the same person or identity register multiple times?
4. Can users register for different roles or permissions?
5. What proof of identity is required for registration to be successful?
6. Are registered identities verified?

For the validation of the registration process, answer to following questions:
1. Can identity information be easily forged or faked?
2. Can the exchange of identity information be manipulated during registration?

</details>

<details>
  <summary>How test account provisioning process?</summary>

Objective:
Verify which accounts may provide others and of what type.

For testing, answer to following questions:
1. Is there any verification, vetting and authorization of provisioning requests?
2. Is there any verification, vetting and authorization of de-provisioning requests?
3. Can an administrator provision other administrators or just users?
4. Can an administrator or other user provision accounts with greater privileges than their own?
5. Can an administrator or user de-provision themselves?
6. How are the files or resources owned by the de-provisioned user-managed? Are they deleted? Is access transferred?

</details>
