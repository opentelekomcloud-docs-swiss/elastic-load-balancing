:original_name: elb_faq_210307.html

.. _elb_faq_210307:

Why Multiple IP Addresses Are Required When I Create or Enable a Load Balancer?
===============================================================================

These IP addresses are used by underlying resources.

Generally, 4 IP addresses are required for creating a load balancer in a single AZ, and 6 IP addresses are required for creating a load balancer with cross-VPC backend enabled. If you create a load balancer in multiple AZs, more IP addresses will be required. There is an algorithm to determine how many IP addresses are required.
