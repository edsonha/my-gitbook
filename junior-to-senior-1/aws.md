# AWS

\*\*\*\*

\*\*\*\*

**Example of AWS Flow**

![](../.gitbook/assets/aws-flow.png)

* With our app, we can ****have Cloudfront CDN all over the world so that when a user goes online from anywhere in the world they're served HTML, CSS and JS files from whatever service that is the closest.
* If the users make a request to our backend REST API which we can put on the EC2 instance.
* We can store user information in Dynamo DB 
* When the users submit an image, instead of having it work in EC2 because this machine is already busy listening to connections, we just trigger a lambda function that will take the URL of the image and send it to Clarify to get a response.
* Once the response is obtained, the response object is stored inside S3 that will be returned to EC2 when ready.

**Monolith vs Microservices**

Monolithic giant infrastructure or code base does everything for us with all the pieces all together in one place running our application and logic.

With docker and AWS, the idea of Microservices has become more popular. That is the idea to split your application into a set of smaller interconnected services that have its own architecture, consisting of its own business logic and concerned with doing one thing really well.

The benefit for Microservices is 

* Smaller chunks that can be tested on their own. In monolith, we have one giant codebase and we have to make sure nobody break anything and all the tests pass before we send it to production.
* Can have different developer teams on their own which means the services can be released individually to production at different time. 
* As long as we have Service Level Agreement \(SLA\) - meaning no matter what updates you do, you give me this return data or you respond to me this way.

