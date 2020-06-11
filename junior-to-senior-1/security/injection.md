# Injection

Injection are the most common attacks. Injection means injecting unwanted code into another piece of code in order to corrupt the data. 

Two injection type is 

* SQL injection \(' or 1=1--\). Bad as you can login without giving the correct password
* Input injection  \(&lt;img src="/" onError="alert\('boom'\);"&gt;\). You can give a boom alert because image source is retrieving from wrong source.

**Solutions:**

* Sanitizing user inputs by data validation. Meaning to check that the user input are of your expected type. Number is number, string is string, etc.
* Use parameterized query or also called prepared statements. Think of it as a function that we can provide parameters. One solution is to use Object Relational Mappers. For SQL \(Sequelize\) and NonSQL \(Mongoose\). They provide these prepared statements \(SQL statements\) for you, so that all you need to supply are the parameters. 

