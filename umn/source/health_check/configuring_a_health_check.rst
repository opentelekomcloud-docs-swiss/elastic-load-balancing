:original_name: en-us_topic_0162227063.html

.. _en-us_topic_0162227063:

Configuring a Health Check
==========================

Scenarios
---------

You can configure a health check when you add a listener. If you have no special requirements, retain the default settings.

Function Description
--------------------

-  The health check protocol can be different from the backend protocol.
-  To reduce the CPU usage of backend servers, you can use TCP for health checks. If you want to use HTTP for health checks, use static files to obtain the health statuses.
-  You can increase the health check interval to reduce the health check frequency.
-  After you enable health checks, the load balancer immediately checks the health of backend servers and will start routing requests over new connections. If a backend server becomes unhealthy, the load balancer will stop routing traffic to it. However, request routing over established connections is not affected. To ensure service availability, you can enable health checks during off-peak hours.
-  New requests are not routed to the backend server whose weight is 0, even if the backend server is considered healthy.


Configuring a Health Check
--------------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.

#. Locate the load balancer and click its name.

#. Click **Backend Server Groups**, locate the backend server group, and click its name.

#. In the **Basic Information** area, click **Configure** next to **Health Check**.

#. In the **Configure Health Check** dialog box, enable the health check. Configure the parameters based on :ref:`Table 1 <en-us_topic_0162227063__table1646416142718>`.

   .. _en-us_topic_0162227063__table1646416142718:

   .. table:: **Table 1** Parameters for configuring a health check

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                      | Example Value         |
      +=======================+==================================================================================================================================================================================================================================================+=======================+
      | Enable Health Check   | Specifies whether to enable health checks.                                                                                                                                                                                                       | N/A                   |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protocol              | -  Specifies the protocol used by the load balancer to perform health checks on backend servers. You can select TCP, HTTP, or HTTPS. .                                                                                                           | HTTP                  |
      |                       | -  If the frontend protocol is UDP, the health check protocol is UDP by default.                                                                                                                                                                 |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | **Advanced Settings** |                                                                                                                                                                                                                                                  |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Interval (s)          | Specifies the maximum time between two consecutive health checks, in seconds.                                                                                                                                                                    | 5                     |
      |                       |                                                                                                                                                                                                                                                  |                       |
      |                       | The interval ranges from **1** to **50**.                                                                                                                                                                                                        |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Timeout (s)           | Specifies the maximum time required for waiting for a response from the health check, in seconds. The timeout duration ranges from **1** to **50**.                                                                                              | 3                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Check Path            | Specifies the health check URL, which is the destination on backend servers for health checks. Configure this parameter only if you have set **Protocol** to **HTTP**. The value can contain 1 to 80 characters and must start with a slash (/). | /index.html           |
      |                       |                                                                                                                                                                                                                                                  |                       |
      |                       | The value can contain letters, digits, hyphens (-), slashes (/), periods (.), percent signs (%), ampersands (&), and the following special characters: ``_~';@$*+,=!:()``                                                                        |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Maximum Retries       | Specifies the maximum number of health check retries. The value ranges from **1** to **10**.                                                                                                                                                     | 3                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Finish**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
