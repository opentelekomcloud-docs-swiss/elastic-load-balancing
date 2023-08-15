:original_name: elb_pro_01_0004.html

.. _elb_pro_01_0004:

Load Balancing on a Public or Private Network
=============================================

A load balancer can work on either a public or private network.

Load Balancing on a Public Network
----------------------------------

You can bind an EIP to a load balancer so that it can receive requests from the Internet and route the requests to backend servers.


.. figure:: /_static/images/en-us_image_0000001445855310.png
   :alt: **Figure 1** Load balancing on a public network

   **Figure 1** Load balancing on a public network

Load Balancing on a Private Network
-----------------------------------

A load balancer has only a private IP address to receive requests from clients in a VPC and route the requests to backend servers in the same VPC. This type of load balancer can only be accessed in a VPC.


.. figure:: /_static/images/en-us_image_0000001495695409.png
   :alt: **Figure 2** Load balancing on a private network

   **Figure 2** Load balancing on a private network
