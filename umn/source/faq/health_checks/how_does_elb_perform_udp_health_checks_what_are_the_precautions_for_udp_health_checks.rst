:original_name: elb_faq_0024.html

.. _elb_faq_0024:

How Does ELB Perform UDP Health Checks? What Are the Precautions for UDP Health Checks?
=======================================================================================

How UDP Health Checks Work
--------------------------

UDP is a connectionless protocol. A UDP health check is implemented as follows:

-  The health check node sends an ICMP request to the backend server based on the health check configuration.

   -  If the health check node receives an ICMP reply from the backend server, it considers the backend server healthy and continues the health check.
   -  If the health check node does not receive an ICMP reply from the backend server, it considers the backend server unhealthy.

-  After receiving the ICMP reply, the health check node sends a UDP probe packet to the backend server.

   -  If the health check node receives an ICMP Port Unreachable message from the backend server within the timeout duration, the backend server is considered unhealthy.
   -  If the health check node does not receive an ICMP Port Unreachable message from the backend server within the timeout duration, the backend server is considered healthy.

When you use UDP for health checks, retain default parameter settings.

Troubleshooting
---------------

If the backend server is unhealthy, use either of the following methods to locate the fault:

-  Check whether the timeout duration is too short.

   One possible cause is that the ICMP Echo Reply or ICMP Port Unreachable message returned by the backend server does not reach the health check node within the timeout duration. As a result, the health check result is inaccurate.

   It is recommended that you change the timeout duration to a larger value.

   UDP health checks are different from other health checks. If the health check timeout duration is too short, the health check result of the backend server frequently toggles back and forth between **Healthy** and **Unhealthy**.

-  Check whether the backend server restricts the rate at which ICMP messages are generated.

For Linux servers, run the following commands to query the rate limit and rate mask:

.. code-block::

   sysctl -q net.ipv4.icmp_ratelimit

The default rate limit is **1000**.

.. code-block::

   sysctl -q net.ipv4.icmp_ratemask

The default rate mask is **6168**.

If the returned value of the first command is the default value or **0**, run the following command to remove the rate limit of Port Unreachable messages:

.. code-block::

   sysctl -w net.ipv4.icmp_ratemask=6160

For more information, see the *Linux Programmer's Manual*. On the Linux CLI, run the following command to display the manual:

.. code-block::

   man 7 icmp

Alternatively, visit http://man7.org/linux/man-pages/man7/icmp.7.html.

.. note::

   Once the rate limit is lifted, the number of ICMP Port Unreachable messages on the backend server will not be limited.

Precautions
-----------

Note the following when you configure UDP health checks:

-  UDP health checks use ping packets to check the health of the backend server. To ensure smooth transmission of these packets, ensure that ICMP is enabled on the backend server by performing the following:

   Log in to the server and run the following command as user **root**:

   **cat /proc/sys/net/ipv4/icmp_echo_ignore_all**

   -  If the returned value is **1**, ICMP is disabled.
   -  If the returned value is **0**, ICMP is enabled.

-  The health check result may be different from the actual health of the backend server.

   If the backend server runs Linux, the rate of ICMP packets may be limited due to Linux's defense against ping flood attacks when there is a large number of concurrent requests. In this case, if a service exception occurs, the load balancer will not receive error message **port XX unreachable** and will consider the health check to be successful. As a result, there is an inconsistency between the health check result and the actual server health.
