:original_name: en-us_topic_0118840332.html

.. _en-us_topic_0118840332:

HTTP Redirection to HTTPS
=========================

Scenarios
---------

HTTPS is an extension of HTTP. HTTPS encrypts data between a web server and a browser.

If you enable redirection, all HTTP requests to your website are transmitted over HTTPS connections to improve security.

.. caution::

   -  If the listener's protocol is HTTP, only the GET or HEAD method can be used for redirection. If you create a redirect for an HTTP listener, the client browser will change POST or other methods to GET. If you want to use other methods rather than GET and HEAD, add an HTTPS listener.
   -  HTTP requests are forwarded to the HTTPS listener as HTTPS requests, which are then routed to backend servers over HTTP.
   -  If an HTTP listener is redirected to an HTTPS listener, no certificate can be deployed on the backend servers associated with the HTTPS listener. If certificates are deployed, HTTPS requests will not take effect.

Prerequisites
-------------

-  You have added an HTTPS listener.
-  You have added an HTTP listener.


HTTP Redirection to HTTPS
-------------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image1| and select the desired region and project.
#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Listeners**, locate the HTTP listener, and click its name.
#. Click **Redirects** and then click **Create** in the right pane.

   .. table:: **Table 1** Configuring parameters for redirection

      +---------------+-------------------------------------------------------------+---------------+
      | Parameter     | Setting                                                     | Example Value |
      +===============+=============================================================+===============+
      | Name          | Enter the redirect name.                                    | redirect-g8h9 |
      +---------------+-------------------------------------------------------------+---------------+
      | Redirected To | Select the HTTPS listener to which requests are redirected. | N/A           |
      +---------------+-------------------------------------------------------------+---------------+
      | Description   | Provides supplementary information about the redirect.      | N/A           |
      +---------------+-------------------------------------------------------------+---------------+

#. In the **Modify Redirect** dialog box, modify the redirect name or description, or select another HTTPS listener, and click **OK**.

.. note::

   -  If requests to an HTTP listener are redirected, its configuration becomes invalid except for access control.
   -  If you create a redirect for an HTTP listener, the backend server will return HTTP 301 Move Permanently to the clients.

Modifying Redirection
---------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image3| and select the desired region and project.
#. Hover on |image4| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Listeners**, locate the HTTP listener, and click its name.
#. Click **Redirects**, locate the redirect, and click **Modify** in the **Operation** column.
#. In the **Modify Redirect** dialog box, modify the redirect name or description, or select another HTTPS listener, and click **OK**.

Deleting Redirection
--------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image5| and select the desired region and project.
#. Hover on |image6| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Listeners**, locate the listener, and click its name.
#. Click **Redirects**, locate the redirect, and click **Delete** in the **Operation** column.
#. In the **Delete Redirect** dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
.. |image3| image:: /_static/images/en-us_image_0000001495375721.png
.. |image4| image:: /_static/images/en-us_image_0000001495615121.png
.. |image5| image:: /_static/images/en-us_image_0000001495375721.png
.. |image6| image:: /_static/images/en-us_image_0000001495615121.png
