:original_name: elb_faq_0066.html

.. _elb_faq_0066:

Why Can't I Access My Backend Servers Through a Load Balancer?
==============================================================

Symptom
-------

This FAQ provides guidance for you to troubleshoot the following problems:

-  Backend servers cannot be accessed through a load balancer.
-  You can access the load balancer from a private IP address, but not from a public IP address.
-  Backend servers are considered unhealthy.

Background
----------

:ref:`Figure 1 <elb_faq_0066__en-us_topic_0145103412_fig18748172215710>` shows how clients access backend servers through a load balancer.

#. The public network load balancer uses an EIP to receive traffic over the Internet, while the private network load balancer receives traffic from within the VPC.
#. The load balancer receives incoming traffic using the frontend protocol and port configured for the listener.
#. The listener checks the health of backend servers. Only healthy backend servers can receive traffic from the listener.
#. The listener forwards the traffic to backend servers based on their weights and the listening rules.

Generally, the problem is probably caused by an access control issue (the parts in yellow) or a health check setting (the green parts).

Troubleshooting should start with backend servers, then move on to the load balancer, and finally to the clients.

.. _elb_faq_0066__en-us_topic_0145103412_fig18748172215710:

.. figure:: /_static/images/en-us_image_0000001445375566.png
   :alt: **Figure 1** How clients access backend servers through a load balancer

   **Figure 1** How clients access backend servers through a load balancer

Troubleshooting Process
-----------------------


.. figure:: /_static/images/en-us_image_0000001445535482.png
   :alt: **Figure 2** Troubleshooting process

   **Figure 2** Troubleshooting process

#. :ref:`Check whether the backend server can be accessed directly. <elb_faq_0066__section084328121219>` Use the client to access the backend server and verify that the backend server configuration and application configuration are correct.
#. :ref:`Check whether the health check is enabled on the console. <elb_faq_0066__section1083219023318>`
#. :ref:`Check whether the health check result of the backend server on the console. <elb_faq_0066__section484511811213>` If the backend server is unhealthy, the load balancer will not route traffic to it.
#. :ref:`Check whether the weight and port of the backend server are correctly configured on the console. <elb_faq_0066__section1971285511441>`
#. :ref:`Check whether access control is enabled and the IP address of the client is allowed to access the listener on the console. <elb_faq_0066__section964310411693>`

.. _elb_faq_0066__section084328121219:

Step 1: Check Whether the Backend Server Can Be Accessed Directly
-----------------------------------------------------------------

Use a client to access the backend server to determine whether the fault is caused by the load balancer or backend server. To do so, ensure that the firewall rules allow network communication between the client and backend server are enabled.

-  Clients on the public network: Bind an EIP to the backend server. After the verification is complete, release the EIP.
-  Clients on the private network: No EIP is required. If the client is in another VPC, set up a VPC peering connection.

If the fault persists, go to :ref:`Step 2: Check Whether the Health Check Is Enabled <elb_faq_0066__section1083219023318>`.

.. _elb_faq_0066__section1083219023318:

Step 2: Check Whether the Health Check Is Enabled
-------------------------------------------------

If the client can access the backend server directly, check whether the health check is enabled. If the health check is enabled but the backend server is detected unhealthy, the load balancer will not route traffic to it.

#. Log in to the management console.
#. In the upper left corner of the page, click |image1| and select the desired region and project.
#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Click the name of the load balancer.
#. On the **Backend Server Groups** tab page, check whether the health check is enabled.

   -  If the health check is enabled, go to :ref:`Step 3: Check Whether the Backend Server Is Healthy <elb_faq_0066__section484511811213>`.
   -  If the health check is disabled, check whether security group and firewall rules allow traffic from the 100.125.0.0/16 (for load balancers) or the VPC CIDR block (for dedicated load balancers) to backend servers. If traffic is allowed but the fault persists, go to :ref:`Step 4: Check Whether the Backend Server Configuration Is Correct <elb_faq_0066__section1971285511441>`.

   .. caution::

      -  Load balancer: If **Cross-VPC Backend** is not enabled for a load balancer that has a TCP or UDP listener, there is no need to configure security group rules and firewall rules to allow traffic from the VPC where the load balancer works to the backend servers associated with TCP or UDP listener.

.. _elb_faq_0066__section484511811213:

Step 3: Check Whether the Backend Server Is Healthy
---------------------------------------------------

If the health check is enabled but the backend server is detected unhealthy, the load balancer will not route traffic to it. Locate the listener, click the **Backend Server Groups** tab on the right, and view the health check result of the backend server.

-  If the backend server is unhealthy, rectify the fault by referring to :ref:`How Do I Troubleshoot an Unhealthy Backend Server? <en-us_topic_0018127975>`
-  If the backend server is healthy, go to :ref:`Step 4: Check Whether the Backend Server Configuration Is Correct <elb_faq_0066__section1971285511441>`.

If the fault persists, go to :ref:`Step 4: Check Whether the Backend Server Configuration Is Correct <elb_faq_0066__section1971285511441>`.

.. _elb_faq_0066__section1971285511441:

Step 4: Check Whether the Backend Server Configuration Is Correct
-----------------------------------------------------------------

Locate the listener, click the **Backend Server Groups** tab on the right, and view the backend server parameters. Note the following parameters:

-  **Weight**: If the weight is set to 0, traffic will not be forwarded to the server.
-  **Backend port**: It must be the same as the port used by the backend server.

If the fault persists, go to :ref:`Step 5: Check Whether Access Control Is Enabled <elb_faq_0066__section964310411693>`.

.. _elb_faq_0066__section964310411693:

Step 5: Check Whether Access Control Is Enabled
-----------------------------------------------

On the **Basic Information** tab page of the listener, check whether access control is enabled and the client is allowed to access the listener.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
