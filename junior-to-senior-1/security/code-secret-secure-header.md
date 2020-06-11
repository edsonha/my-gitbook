# Code Secret, Secure Header

Code Secret:

* Use .env file to store sensitive information 
* Be careful with git commit history

Secure Header:

HTTP headers are important in telling the browser what to do with some of the contents that we've delivered and sometimes to tell servers what to do as well with these requests. To have secure headers in express app, all we need is "helmet". For example, to remove X-Powered-By: Express \(Don't let attacker know what server we are building\)



