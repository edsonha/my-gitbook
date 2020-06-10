# SPA vs Server-Side Rendering

**Single Page Application \(Client-Side-Rendering\)**

Pro

* Faster subsequent load because all assets are downloaded. Only part of the web got re-render.

Cons

* Slower initial page load as you need to download many files including JS.

**Server-Side-Rendering**

Pro

* Better SEO performance as website get rendered almost immediately versus SPA that get rendered later. So it is easier to index.
* Faster initial page load
* If demographic is wide that includes high and low gadget, SSR is better.

Cons

* Lower subsequent load because of full page reload 
* Many requests to server

**Use Cases:**

SaaS company: Website \(Price, Registration\) use SSR to make use of the SEO optimization and WebApp \(Dashboard, etc\) use SPA for better user experience.

