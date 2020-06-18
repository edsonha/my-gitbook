# Backend Optimization

1. Content Delivery Network helps with accelerating web site delivery by caching its files in servers around the world and served content to users from the nearest server. All you need to do is update your DNS name servers to use Cloudfare. 

Benefits:

* Improve page load speed because it reduce latency and jumping between routers as cached content is served from nearest server
* Security \(prevent scrapper, DDOS attack\)
* Load balancing

2. GZIP can optimize performance because it makes the files smaller and very easy to implement. For example in Express App, we have middleware called compression.

