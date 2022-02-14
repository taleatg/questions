# Security Misconfiguration

### Links
[OWASP: Security Misconfiguration](https://owasp.org/www-project-top-ten/2017/A6_2017-Security_Misconfiguration)

### Questions

<details>
  <summary>What is Security Misconfiguration risk?</summary>

Security misconfiguration is the most commonly seen issue. It is the main result of insecure default configurations, incomplete or ad hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information.

The application might be vulnerable if the application is:

* Miss appropriate improperly configured permissions on cloud services.

* Unnecessary features are enabled or installed (e.g. unnecessary ports, services, pages, accounts, or privileges).

* Default accounts and their passwords still enabled and unchanged.

* Error handling reveals stack traces or other overly informative error messages to users.

* For upgraded systems, the latest security features are disabled or not configured securely.

* The security settings in the application servers, application frameworks (e.g. Struts, Spring, ASP.NET), libraries, databases, etc. not set to secure values.

* The server does not send security headers or directives.

* The software is out of date or vulnerable.

Without a concerted, repeatable application security configuration process, systems are at a higher risk.

</details>
