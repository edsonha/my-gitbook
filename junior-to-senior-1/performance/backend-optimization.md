# Backend Optimization

1. Content Delivery Network helps with accelerating web site delivery by caching its files in servers around the world and served content to users from the nearest server. All you need to do is update your DNS name servers to use Cloudfare. 

Benefits:

* Improve page load speed because it reduce latency and jumping between routers as cached content is served from nearest server
* Security \(prevent scrapper, DDOS attack\)
* Load balancing

2. GZIP can optimize performance because it makes the files smaller and very easy to implement. For example in Express App, we have middleware called compression.

3. Database Scaling principles:

* Identify inefficient queries
* Increase memory
* Vetical Scaling \(Redis\)
* Sharding \(Separating database based on certain criteria\)
* More Database \(Distributed\)
* Database type

4 Caching

5. Load Balancer using NGINX, but usually provided by cloud provider like AWS out of the box

