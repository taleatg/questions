# XML External Entities

### Links
[OWASP: XML External Entities](https://owasp.org/www-project-top-ten/2017/A4_2017-XML_External_Entities_(XXE))

### Questions

<details>
  <summary>What is XML External Entities risk?</summary>

Many older or poorly configured XML processors evaluate external entity references within XML documents. It is possible to use external entities to disclose internal files using the file URI handler, internal file shares, internal port scanning, remote code execution, and denial of service attacks.

Applications and in particular XML-based web services or downstream integrations might be vulnerable to attack if:

* To use untrusted data.

* Any of the XML processors in the application has document type definitions (DTDs) enabled. As the exact mechanism for disabling DTD processing varies by the processor.

* SAML protocol for identity processing within federated security or single sign-on (SSO) purposes. SAML uses XML for identity assertions and may be vulnerable.

* If the application uses SOAP before version 1.2, it is likely susceptible to XXE attacks.

Developer training is essential to identify and mitigate XXE. Besides that, preventing XXE requires:

* Whenever possible, use less complex data formats (JSON) and avoid serialization of sensitive data.

* Patch or upgrade all XML processors and libraries.

* Disable XML external entity and DTD processing in all XML parsers in the application.

* Implement positive server-side input validation, filtering, or sanitization to prevent hostile data within XML documents, headers, or nodes.

* Verify that XML or XSL file upload functionality validates incoming XML using XSD validation or similar.

* SAST tools can help detect XXE in source code, although manual code review is the best alternative in large, complex applications with many integrations.

</details>
