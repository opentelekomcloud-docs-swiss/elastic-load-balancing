:original_name: elb_faq_210306.html

.. _elb_faq_210306:

Can I Bind Multiple EIPs to a Load Balancer?
============================================

No.

-  If you want to use the load balancer on a public network, you can only bind one EIP to the load balancer to receive requests from the Internet.
-  If you want to use the load balancer in a VPC, bind a private IP address. To route requests from a different VPC, you need to create a VPC peering connection between the VPC where the load balancer works and the other VPC.
