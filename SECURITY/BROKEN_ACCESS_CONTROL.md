# Broken Access Control

### Links
[OWASP: Broken Access Control](https://owasp.org/www-project-top-ten/2017/A5_2017-Broken_Access_Control)

### Questions

<details>
  <summary>What is a Broken Access Control risk?</summary>

Restrictions on what authenticated users are allowed to do are often not enough enforced.

Access control enforces policy such that users cannot act outside of their intended permissions. Failures typically lead to unauthorized information disclosure, modification or destruction of all data, or performing a business function outside. Common access control vulnerabilities include:

* Bypassing access control checks by modifying the URL, internal application state, or the HTML page, or simply using a custom API attack tool.

* Allowing the primary key to be changed to different users' records, permitting viewing or editing someone else's account.

* Elevation of privilege.

* Metadata manipulation, such as replaying or tampering with a JSON Web Token (JWT) access control token or a cookie or hidden field manipulated to elevate privileges, or abusing JWT invalidation.

* CORS misconfiguration allows unauthorized API access.

* Force browsing to authenticated pages as an unauthenticated user. Accessing API with missing access controls for POST, PUT and DELETE.

Access control is only effective if enforced in trusted server-side code or server-less API, where the attacker cannot modify the access control check or metadata.

* Except for public resources, deny by default.

* Implement access control mechanisms once and re-use them throughout the application, including minimizing CORS usage.

* Model access controls should enforce record own, rather than accepting that the user can create, read, update, or delete any records.

* Enforce unique application business limit requirements into domain models.

* Disable webserver directory listing and ensure file metadata (e.g. .git) and backup files are not present within web roots.

* Log access control failures, alert admins when appropriate (e.g. repeated failures).
Invalidate JWT tokens on the server after logout.

Developers and QA staff should include functional access control unit and integration tests.

</details>
