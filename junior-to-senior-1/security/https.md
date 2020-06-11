# HTTPS, Cross-Site-Scripting \(XSS\) and Cross-Site-Request-Forgery \(CSRF\)

HTTPS use SSL / TLS certificates and HTTP without "s" is a clear text protocol, meaning anybody that  intercepts the message, they can read it. SSL / TLS creates a tunnel known as HTTPS  which is secure and this encrypts the information between client and server.

**Cross-Site-Scripting \(XSS\) and Cross-Site-Request-Forgery \(CSRF\)**

XSS occurs whenever an application includes untrusted data in a web page without proper validation or updating a web page with supplied data using JavaScript. So, XSS allows an attacker to execute scripts in a victim's browser \(remember input injection\). So always validate \(sanitize\) your data.

CSRF is when attackers create a bad URL that has malicious code in it. For example scam email to steal your session cookie.

