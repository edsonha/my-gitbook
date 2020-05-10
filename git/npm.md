# NPM

## 1. Package.lock

Auto generated file by NPM that locks the version of all the packages inside of our application within a specific range based on the rules that we set inside of package.json. The lock file is simply there so that if multiple people are working on this application they are all using versions of these dependencies that don't conflict with each other. It ensures that everybody is using a consistent version of these dependencies. To update packages version, run npm update.

## 2. Vulnerabilities

They are essentially minor security concerns. Sometimes they're major. That has to do with either a dependency that you have installed or a dependency that your packages depend upon that you yourself don't know that you also installed. To resolve, run npm audit fix.

