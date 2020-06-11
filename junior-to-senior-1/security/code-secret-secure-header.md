# Code Secret, Secure Header, Access Control, Data Management, Authentication

**Code Secret:**

* Use .env file to store sensitive information 
* Be careful with git commit history

**Secure Header:**

HTTP headers are important in telling the browser what to do with some of the contents that we've delivered and sometimes to tell servers what to do as well with these requests. To have secure headers in express app, all we need is "helmet". For example, to remove X-Powered-By: Express \(Don't let attacker know what server we are building\)

**Access Control:**

Access control is having restrictions on what authenticated users are allowed to do or not. ****With access control, the main idea is principle of least privilege. Meaning, always give the least amount of privilege possible give only enough that people can do their work. For example, CORS Whitelist.

**Data Management:**

Two main ideas: 

* Hashing your password
* Encrypt your database. Not always feasible to encrypt everything, but can focus on sensitive data first.

**Authentication:**

Authentication means making sure that the person on the other end is who they say they are**.** Firstly, this is done through passwords to authenticate that they are the person that has access to this account. Secondly, we have to manage their session. That is to make sure that they are the correct person sending the request. Always be wary when attacker compromised passwords, keys, session tokens or other flaws because it can mean that they can impersonate other users.

