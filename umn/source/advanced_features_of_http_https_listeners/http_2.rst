:original_name: en-us_topic_0150301849.html

.. _en-us_topic_0150301849:

HTTP/2
======

Scenarios
---------

Hypertext Transfer Protocol 2.0 (HTTP/2) is the next-generation HTTP protocol. HTTP/2 is used to secure connections between the load balancer and clients. You can enable HTTP/2 when you add HTTPS listeners. If you have already added an HTTPS listener, you can also enable this function.

Enabling HTTP/2
---------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image1| and select the desired region and project.
#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Under **Listeners**, click **Add Listener**.
#. In the **Add Listener** dialog box, set **Frontend Protocol** to **HTTPS**.
#. In the **Add Listener** dialog box, expand **Advanced Settings** and enable HTTP/2.
#. Click **OK**.

.. note::

   HTTP/2 is available only for HTTPS listeners.

Disabling HTTP/2
----------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image3| and select the desired region and project.
#. Locate the load balancer and click its name.
#. Click **Listeners**, locate the listener, and click |image4|.
#. In the **Modify Listener** dialog box, expand **Advanced Settings** and disable HTTP/2.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
.. |image3| image:: /_static/images/en-us_image_0000001495375721.png
.. |image4| image:: /_static/images/en-us_image_0000001495695261.png
