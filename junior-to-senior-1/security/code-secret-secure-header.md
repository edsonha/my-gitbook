# Code Secret, Secure Header, Access Control

**Code Secret:**

* Use .env file to store sensitive information 
* Be careful with git commit history

**Secure Header:**

HTTP headers are important in telling the browser what to do with some of the contents that we've delivered and sometimes to tell servers what to do as well with these requests. To have secure headers in express app, all we need is "helmet". For example, to remove X-Powered-By: Express \(Don't let attacker know what server we are building\)

**Access Control:**

Access control is having restrictions on what authenticated users are allowed to do or not. ****With access control, the main idea is principle of least privilege. Meaning, always give the least amount of privilege possible give only enough that people can do their work. For example, CORS Whitelist.



