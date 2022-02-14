# Sensitive Data Exposure

### Links
[OWASP: Sensitive Data Exposure](https://owasp.org/www-project-top-ten/2017/A3_2017-Sensitive_Data_Exposure)

### Questions

<details>
  <summary>What is sensitive data exposure?</summary>

Many web applications and APIs do not protect sensitive data, such as financial, healthcare, and PII. Attackers may steal or modify such weakly protected data to conduct credit card fraud, identity theft, or other crimes. Sensitive data may be compromised without extra protection, such as encryption at rest or in transit, and requires special precautions when exchanged with the browser.

The first thing is to determine the protection needs of data in transit and at rest. For example, passwords, credit card numbers, health records, personal information and business secrets require extra protection. For all such data:

* Protocols such as HTTP, SMTP and FTP should be concerned because they transmit data into clear text.

* Using old or weak cryptographic algorithms.

* Using weak crypto keys.

* Using not enforced encryption.

* Using invalid certificates.

Do the following, at a minimum, and consult the references:

* Classify data processed, stored or transmitted by an application. Identify which data is sensitive according to privacy laws, regulatory requirements, or business needs.

* Apply controls as per the classification.

* Avoid storing sensitive data unnecessarily. Discard it as soon as possible or use PCI DSS compliant tokenization or even truncation. 

* Make sure to encrypt all sensitive data at rest.

* Ensure up-to-date and more secure standard algorithms, protocols, and keys are in place; use proper key management.

* Encrypt all data in transit with security protocols such as TLS with perfect forward secrecy (PFS) cyphers.

* Disable caching for a response that contains sensitive data.

* Store passwords using adaptive and salted hashing functions with a work factor (delay factor).

* Verification.

</details>
