:original_name: elb_pro_0005.html

.. _elb_pro_0005:

Product Advantages
==================

ELB Advantages
--------------

-  Robust performance

   Each load balancer has exclusive use of isolated resources, meeting your requirements for handling a massive number of requests. A single load balancer deployed in one AZ can handle up to 20 million concurrent connections.

   If you deploy a load balancer in multiple AZs, its performance such as the number of new connections and the number of concurrent connections will multiply. For example, if you deploy a load balancer in two AZs, it can handle up to 40 million concurrent connections.

   .. note::

      -  If requests are from the Internet, the load balancer in each AZ you select routes the requests based on source IP addresses.
      -  For requests from a private network:

         -  If clients are in an AZ you select when you create the load balancer, requests are distributed by the load balancer in this AZ. If the load balancer is unavailable, requests are distributed by the load balancer in another AZ you select.
         -  If clients are in an AZ that is not selected when you create the load balancer, requests are distributed by the load balancer in each AZ you select based on source IP addresses.

-  High availability

   ELB can route traffic uninterruptedly. If your servers in one AZ are unhealthy, it automatically routes traffic to healthy servers in other AZs. ELB provides a comprehensive health check system to ensure that incoming traffic is routed only to healthy backend servers, improving the availability of your applications.

-  Ultra-high security

   ELB supports . It allows you to select security policies that fit your security requirements.

-  Multiple protocols

   ELB supports the following protocols, including , TCP, UDP, HTTP, and HTTPS, so that they can route requests from different types of applications.

-  No limits

   ELB can route requests to both servers on the cloud and on premises, allowing you to leverage cloud resources to handle burst traffic.

-  Ease-of-use

   ELB provides a diverse set of algorithms that allow you to configure different traffic routing policies to meet your requirements while keeping deployments simple.
