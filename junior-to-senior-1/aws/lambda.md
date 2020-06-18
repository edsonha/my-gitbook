# Lambda

In the past, we've built and deployed web applications where we control everything. We need to be responsible for:

* Deployment and making sure all resources are set \(provisioning and managing resources\)
* Problem with this is we will get charged for keeping the server up even though we are not using or serving out requests
* Maintenance and upgrade and security

And this is the idea of Serveless come in \(Serveless does not mean not using server\). But, it simply means we build applications where we hand in to the cloud provided \(like AWS\). The benefits:

* We only get charged for what we use. \(because cloud provider can reallocate unused server to other company\)
* Scalability, maintenance, and security are taken care

**Lambda**

When we give a function to AWS Lambda, it is going to run it for us. Underneath the hood, the cloud provider creates a container \(like Docker\) and it runs the function inside of it. So if there are five users requesting, they are going to create five separate container for each user and give response.

All they do is simply store the function that we give it in their database and whenever it's being called it will grab it from the database and actually run it. Now you may see a problem with this and this is actually called the cold start problem. When the first time it is being called, they grab the function from database, it will takes a bit of time \(which is still fast\)

**Serverless**

NPM package that helps us deploy AWS lambda functions from our command line.

```text
// create a boiler template
sls create -t aws-nodejs
```

In order for our serverless to connect with AWS, we have to use a service called IAM \(Identity and Access Management\)

```text
// connect serverless with AWS
sls config credentials --provider aws --key ${yourKey} --secret ${yourSecretKey}
```

Lambda is stateless and that is it's not going to remember anything for us. Remember these things are created because the function is stored in a database and when it's ready to be invoked it's going to be put into a container by Amazon and it's going to get run and after it's done running and there's no more requests it's going to get put back into the database or that container is going to go down and there's no way to remember anything.

So you want to keep your functions stateless and if you ever want to store information or data you can use Dynamo DB or S3.

```text
// to deploy
sls deploy

// to invoke
sls invoke --function rank
OR
sls invoke local --function rank 
// This is done in local, so it is not going to be counted as charge
// Downside is there is no connection with other resources that Amazon have like
// S3 and others. So your code cannot have that dependency.
```

Lambda functions are great if you have a task that you don't want your servers running and you want somebody else \(AWS\) to manage it for you. This can be because of many reasons but the two main ones:

1. More scalable and can make sure that if you have really high requests at certain time of day, it can be handled. 

2. Lower cost compared to managing your own servers.

