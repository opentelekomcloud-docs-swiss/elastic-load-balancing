:original_name: elb_ug_jt_0003.html

.. _elb_ug_jt_0003:

Load Balancing Algorithms
=========================

Load balancers receive requests from clients and forward them to backend servers in one or more AZs. Each load balancer has at least a listener and a backend server. The load balancing algorithm you select when you add the listener determines how requests are distributed.


Load Balancing Algorithms
-------------------------

ELB supports the following load balancing algorithms:

-  Weighted round robin: Requests are routed to backend servers using the round robin algorithm. Backend servers with higher weights receive proportionately more requests, whereas equal-weighted servers receive the same number of requests. This algorithm is often used for short connections, such as HTTP connections.

   The following figure shows an example of how requests are distributed using the weighted round robin algorithm. Two backend servers are in the same AZ and have the same weight, and each server receives the same proportion of requests.


   .. figure:: /_static/images/en-us_image_0000001495615237.png
      :alt: **Figure 1** Traffic distribution using the weighted round robin algorithm

      **Figure 1** Traffic distribution using the weighted round robin algorithm

-  Weighted least connections: In addition to the weight assigned to each server, the number of connections being processed by each backend server is also considered. Requests are routed to the server with the lowest connections-to-weight ratio. In addition to the number of connections, each server is assigned a weight based on its capacity. Requests are routed to the server with the lowest connections-to-weight ratio. This algorithm is often used for persistent connections, such as connections to a database.

   The following figure shows an example of how requests are distributed using the weighted least connections algorithm. Two backend servers are in the same AZ and have the same weight, 100 connections have been established with backend server 01, and 50 connections have been connected with backend server 02. New requests are preferentially routed to backend server 02.


   .. figure:: /_static/images/en-us_image_0000001495495245.png
      :alt: **Figure 2** Traffic distribution using the weighted least connections algorithm

      **Figure 2** Traffic distribution using the weighted least connections algorithm

-  Source IP hash: The source IP address of each request is calculated using the consistent hashing algorithm to obtain a unique hashing key, and all backend servers are numbered. The generated key is used to allocate the client to a particular server. This allows requests from different clients to be routed based on source IP addresses and ensures that a client is directed to the same server that it was using previously. This algorithm works well for TCP connections of load balancers that do not use cookies.

   The following figure shows an example of how requests are distributed using the source IP hash algorithm. Two backend servers are in the same AZ and have the same weight. If backend server 01 has processed a request from IP address A, the load balancer will route new requests from IP address A to backend server 01.


   .. figure:: /_static/images/en-us_image_0000001445535346.png
      :alt: **Figure 3** Traffic distribution using the source IP hash algorithm

      **Figure 3** Traffic distribution using the source IP hash algorithm

Changing the Load Balancing Algorithm
-------------------------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image1| and select the desired region and project.
#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Backend Server Groups** and click |image3| on the right of the backend server group name.
#. Select a load balancing algorithm.

   .. note::

      The modification will take effect immediately. The load balancer will establish new connections with the clients, and request routing over established connections will not be affected.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
.. |image3| image:: /_static/images/en-us_image_0000001495495253.png
