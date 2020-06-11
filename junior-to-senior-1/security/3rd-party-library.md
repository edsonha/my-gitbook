# 3rd Party Library

As our applications grow, we depend more and more on third party libraries, which means codes that we do not write ourselves. So you want to make sure the library you added can be trusted

To solve this:

* npm audit \(check \# audit package.json\). 
* npm install -g snyk \(snyk test for \# audit node\_modules directory\)

So always make sure that the third party libraries that you're using are always up to date and that you're not using any packages that have known vulnerabilities \(at the same time, make sure the update does not make breaking change\)



