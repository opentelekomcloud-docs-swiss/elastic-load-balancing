:original_name: en-us_topic_0015479966.html

.. _en-us_topic_0015479966:

What Is ELB?
============

Elastic Load Balance (ELB) automatically distributes incoming traffic across multiple backend servers based on the listening rules you configure. ELB expands the service capabilities of your applications and improves their availability by eliminating single points of failure (SPOFs).


.. figure:: /_static/images/en-us_image_0000001445375366.png
   :alt: **Figure 1** Using a load balancer

   **Figure 1** Using a load balancer

ELB Components
--------------

ELB consists of the following components:

-  Load balancer: distributes incoming traffic across backend servers.

-  Listener: uses the protocol and port you specify to check for requests from clients and route the requests to associated backend servers based on the listening rules and forwarding policies you configure. You can add one or more listeners to a load balancer.

-  Backend server group: contains one or more backend servers to receive requests routed by the listener. You need to add at least one backend server to a backend server group.

   You can set a weight for each backend server based on their performance.

   You can also configure health checks for a backend server group to check the health of each backend server. When a backend server is unhealthy, the load balancer stops routing new requests to this server.


.. figure:: /_static/images/en-us_image_0000001495375773.png
   :alt: **Figure 2** ELB components

   **Figure 2** ELB components

Accessing ELB
-------------

You can use either of the following methods to access ELB:

-  Management console

   Log in to the management console and choose **Elastic Load Balance (ELB)**.

-  APIs

   You can call APIs to access ELB. For details, see the *Elastic Load Balancing API Reference*.
