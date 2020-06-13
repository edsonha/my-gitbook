# Docker

The idea is to have project run on a different machine without any errors. We need a way for us to be able to run our programs and our apps in all the environments possible. And this is where containers come in.

Companies uses micro-services and have their products composed of multiple layers. These layers can be considered services, each with their own container doing its own thing and communicating with each other to make the whole system work.

The problem with micro-services is each service or container may have its own requirements from different node versions to conflicting library dependencies. And when you add in the fact that every developer's machine and environment is different, it can be challenged to onboard new developers quickly or run this service on another machine.

So, Docker helps us create these containers around our services.

