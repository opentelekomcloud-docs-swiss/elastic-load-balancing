:original_name: elb_faq_0068.html

.. _elb_faq_0068:

Why Are Backend Servers Frequently Accessed by IP Addresses in 100.125.0.0/16?
==============================================================================

IP addresses in 100.125.0.0/16 are internal IP addresses used by load balancers to communicate with backend servers. Load balancers use these IP addresses as source addresses to route traffic to backend servers and to check the health of backend servers, if you have enabled health check.

To ensure that your load balancer can provide services properly, ensure that the security groups that contain the backend servers allow traffic from 100.125.0.0/16.
