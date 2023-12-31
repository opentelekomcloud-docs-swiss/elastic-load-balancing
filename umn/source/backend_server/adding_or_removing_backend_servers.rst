:original_name: elb_ug_hd_0003.html

.. _elb_ug_hd_0003:

Adding or Removing Backend Servers
==================================

Scenarios
---------

When you use ELB, ensure that at least a healthy backend server is in the backend server group associated with your load balancer. If incoming traffic increases, you need to add more backend servers.

After a backend server is removed, it cannot receive requests from the load balancer. You can add it back to the backend server group when the traffic goes up again.

If the load balancer is associated with an AS group, instances in the AS group are automatically added to the backend server group associated with the load balancer. If instances are removed from the AS group, they will be automatically removed from the backend server group.

Adding Backend Servers
----------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image1| and select the desired region and project.
#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Backend Server Groups**, locate the backend server group, and click its name.
#. Click **Backend Servers**.

Removing Backend Servers
------------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image3| and select the desired region and project.
#. Hover on |image4| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Backend Server Groups**, locate the backend server group, and click its name.
#. In the **Basic Information** area, locate the target backend server and click **Remove** in the **Operation** column. To remove multiple backend servers, select the backend servers you want to remove and click **Remove** above the server list.
#. Click **Yes**.

Adding a Backend Server Group
-----------------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image5| and select the desired region and project.

#. Hover on |image6| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.

#. Locate the load balancer and click its name.

#. Under **Backend Server Groups**, click **Add Backend Server Group**.

#. In the **Add Backend Server Group** dialog box, configure the parameters.

   Configure the parameters based on :ref:`Table 1 <elb_ug_hd_0003__table299811529239>` and :ref:`Table 2 <elb_ug_hd_0003__table1022053182319>`.

   .. _elb_ug_hd_0003__table299811529239:

   .. table:: **Table 1** Parameters for adding a backend server group

      +--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                   | Example Value         |
      +==========================+===============================================================================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Name                     | Specifies the name of the backend server group.                                                                                                                                                                                                                                                                                                                                                                                               | server_group-sq4v     |
      +--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Backend Protocol         | Specifies the protocol used by backend servers to receive requests.                                                                                                                                                                                                                                                                                                                                                                           | HTTP                  |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          | The backend protocol can be TCP, UDP, or HTTP.                                                                                                                                                                                                                                                                                                                                                                                                |                       |
      +--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Load Balancing Algorithm | Specifies the algorithm used by the load balancer to distribute traffic. The following options are available:                                                                                                                                                                                                                                                                                                                                 | Weighted round robin  |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          | -  **Weighted round robin**: Requests are routed to different servers based on their weights, which indicate server processing performance. Backend servers with higher weights receive proportionately more requests, whereas equal-weighted servers receive the same number of requests.                                                                                                                                                    |                       |
      |                          | -  **Weighted least connections**: In addition to the number of active connections established with each backend server, each server is assigned a weight based on their processing capability. Requests are routed to the server with the lowest connections-to-weight ratio.                                                                                                                                                                |                       |
      |                          | -  **Source IP hash**: The source IP address of each request is calculated using the consistent hashing algorithm to obtain a unique hashing key, and all backend servers are numbered. The generated key is used to allocate the client to a particular server. This allows requests from different clients to be routed based on source IP addresses and ensures that a client is directed to the same server that it was using previously. |                       |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          |    -  Choose an appropriate algorithm based on your requirements for better traffic distribution.                                                                                                                                                                                                                                                                                                                                             |                       |
      |                          |    -  For **Weighted round robin** or **Weighted least connections**, no requests will be routed to a server with a weight of 0.                                                                                                                                                                                                                                                                                                              |                       |
      +--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Sticky Session           | Specifies whether to enable sticky sessions. If you enable sticky sessions, all requests from a client are sent to the same backend server.                                                                                                                                                                                                                                                                                                   | ``-``                 |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          |    You can enable sticky sessions only if you select **Weighted round robin** for **Load Balancing Algorithm**.                                                                                                                                                                                                                                                                                                                               |                       |
      +--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Sticky Session Type      | After you enable the sticky session feature, select a sticky session type:                                                                                                                                                                                                                                                                                                                                                                    | Load balancer cookie  |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          | -  **Source IP address**: The source IP address of each request is calculated using the consistent hashing algorithm to obtain a unique hashing key, and all backend servers are numbered. The system allocates the client to a particular server based on the generated key. This enables requests from different clients to be routed and ensures that a client is directed to the same server that it was using previously.                |                       |
      |                          | -  **Load balancer cookie**: The load balancer generates a cookie after receiving a request from the client. All subsequent requests with the same cookie are then routed to the same backend server.                                                                                                                                                                                                                                         |                       |
      +--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description              | Provides supplementary information about the backend server group.                                                                                                                                                                                                                                                                                                                                                                            | ``-``                 |
      |                          |                                                                                                                                                                                                                                                                                                                                                                                                                                               |                       |
      |                          | You can enter a maximum of 255 characters.                                                                                                                                                                                                                                                                                                                                                                                                    |                       |
      +--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   .. _elb_ug_hd_0003__table1022053182319:

   .. table:: **Table 2** Parameters for configuring a health check

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                           | Example Value         |
      +=======================+=======================================================================================================================================================================================================================================================+=======================+
      | Enable Health Check   | Specifies whether to enable health checks.                                                                                                                                                                                                            | N/A                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol              | Specifies the protocol used by the load balancer to perform health checks on backend servers. You can select HTTP or TCP. The health check protocol cannot be changed once it is set.                                                                 | HTTP                  |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | **Advanced Settings** |                                                                                                                                                                                                                                                       |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Interval (s)          | The maximum time between two consecutive health checks, in seconds.                                                                                                                                                                                   | 5                     |
      |                       |                                                                                                                                                                                                                                                       |                       |
      |                       | The interval ranges from **1** to **50**.                                                                                                                                                                                                             |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Timeout (s)           | Specifies the maximum time required for waiting for a response from the health check, in seconds. The timeout duration ranges from **1** to **50**.                                                                                                   | 3                     |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Check Path            | Specifies the health check URL, which is the destination on backend servers for health checks. Configure this parameter only if you have set **Protocol** to **HTTP**. The check path must start with a slash (/) and can contain 1 to 80 characters. | /index.html           |
      |                       |                                                                                                                                                                                                                                                       |                       |
      |                       | The value can contain letters, digits, hyphens (-), slashes (/), periods (.), percent signs (%), ampersands (&), and the following special characters: ``_~';@$*+,=!:()``                                                                             |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Maximum Retries       | Specifies the maximum number of health check retries. The value ranges from **1** to **10**.                                                                                                                                                          | 3                     |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

Modifying a Backend Server Group
--------------------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image7| and select the desired region and project.
#. Hover on |image8| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Backend Server Groups**, locate the backend server group, and click |image9| on the right of its name.
#. Modify the parameters as needed and click **OK**.

Deleting a Backend Server Group
-------------------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image10| and select the desired region and project.
#. Hover on |image11| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Backend Server Groups**, locate the backend server group, and click |image12| on the right of its name.
#. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
.. |image3| image:: /_static/images/en-us_image_0000001495375721.png
.. |image4| image:: /_static/images/en-us_image_0000001495615121.png
.. |image5| image:: /_static/images/en-us_image_0000001495375721.png
.. |image6| image:: /_static/images/en-us_image_0000001495615121.png
.. |image7| image:: /_static/images/en-us_image_0000001495375721.png
.. |image8| image:: /_static/images/en-us_image_0000001495615121.png
.. |image9| image:: /_static/images/en-us_image_0000001495615317.png
.. |image10| image:: /_static/images/en-us_image_0000001495375721.png
.. |image11| image:: /_static/images/en-us_image_0000001495615121.png
.. |image12| image:: /_static/images/en-us_image_0000001445535430.png
