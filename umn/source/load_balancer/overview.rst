:original_name: en-us_topic_0166333708.html

.. _en-us_topic_0166333708:

Overview
========

A load balancer distributes incoming traffic across multiple backend servers. Before using a load balancer, you need to add at least one listener to it and associate one backend server with it.


.. figure:: /_static/images/en-us_image_0000001445695438.png
   :alt: **Figure 1** ELB components

   **Figure 1** ELB components

Network Type
------------

Load balancers can work on both public and private network.

-  Load balancers on the public network route requests over the Internet.

   Each load balancer has an EIP bound so that it can receive requests from clients on the Internet and routes the requests across backend servers.

   **Application scenario**

   -  A load balancer is used as a single point of contact for clients when a group of servers provide services over the Internet.
   -  Fault tolerance and fault recovery are necessary.

-  Load balancers on a private network route requests within a VPC.

   This type of load balancers has only private IP addresses and can be accessed only in the VPC. They receive requests from clients in the VPC and route the requests across backend servers in the same VPC.

   **Application scenario**

   Both clients and backend servers are in the same VPC as the load balancer.

   -  There are multiple backend servers, and requests need to be evenly distributed across these servers.
   -  Fault tolerance and fault recovery are necessary.
   -  You do not want IP addresses of your physical devices to be exposed.

   **Load balancing on both public and private networks**

   Suppose that you have deployed both web servers and database servers. The web servers are accessible from users on the Internet, while the database servers can be accessed only on the private network. In this case, you can create two load balancers, one for the web servers and one for the database servers. The load balancer on the public network receives requests over the Internet and routes the requests to the web servers. Then, the load balancer on the private network forwards the requests to database servers.


   .. figure:: /_static/images/en-us_image_0000001495375977.png
      :alt: **Figure 2** Load balancing on both public and private networks

      **Figure 2** Load balancing on both public and private networks
