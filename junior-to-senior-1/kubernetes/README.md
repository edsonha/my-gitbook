# Kubernetes

Container orchestration helps to monitor the state, the performance and the health of the container \(the instances as well as the host\) and take necessary action to remediate the situation in a production environment.

Usually container orchestration consists of multiple docker hosts that can host multiple containers. That way, even if one host fails, the application is still accessible through the others.

Some benefits of container orchestration:

1. Scale up the number of instances when demand increase and vice versa
2. Add additional host to support the user load
3. Provide advanced net networking between these container across different hosts 
4. Load balancing user requests across different host 
5. Provide support for sharing storage between the hosts 
6. Support configuration management and security within the cluster
7. Test new features of your application by only upgrading a percentage of the instances through AB testing method

