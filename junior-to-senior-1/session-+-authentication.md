# Session + Authentication

**Cookie-based Auth**

Once authenticated, cookie-based authentication send a header that is set cookie with the session to identify the browser \(client\). 

* **Stateful**

The browser keeps their session cookie in the header and the server has to keep track of the cookies that it's sent out to the clients in database or some other way to manage that data. Whenever they get a request they have to go through those cookies and figure out if any of them are valid \(similar to password checking\) and which user information they pass based on that cookie and has to keep track of these active sessions in the database. Once the user logs out, the session is destroyed both on client and server side.

**Token-based Auth**

Characteristics**:**

* Can store information inside the token
* Stored in local storage or session storage of browser instead of header like cookie
* Stateless as the server does not need to keep a record of which users are logged in or which have been issued. All the server needs to do is decode this JWT and make sure that it's a valid token \(by verify method of JWT\).
* Once a user logs out, the token is destroyed on the client side with no interaction on the server \(backend\)

**Pros of token-based auth:**

* Stateless. The backend does not need to actually record or store the tokens in a database. Each token is self-contained and contains all the data required to check its validity as well as convey user information. So the server's job is actually simplified. The only job is then to sign the tokens. And any time it gets a request to just verify the token.
* Unlike cookies which are meaningless strings, in JWT you can actually have any type of data you want inside of the JWT.
* Work well across different API. You can use the same JWT token across different API.
* Serve both browser and native mobile platforms like iOS and Android.

**Cons of token-based auth:**

* Cookie works well with one single domain - the classic browser server client relationship.
* Bigger data is JWT token hold more information.
* Storing info in JWT can be dangerous.

