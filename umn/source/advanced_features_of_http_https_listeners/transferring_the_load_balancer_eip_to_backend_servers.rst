:original_name: en-us_topic_0118147668.html

.. _en-us_topic_0118147668:

Transferring the Load Balancer EIP to Backend Servers
=====================================================

Scenarios
---------

ELB allows the EIPs of the load balancers to be passed to backend servers. You can enable the function when you add HTTPS or HTTP listeners.

Load balancer EIPs are placed in the X-Forwarded-ELB-IP field in the HTTPS or HTTP header in the format of *XX.XXX.XX.XXX*, as shown below:

.. code-block::

   X-Forwarded-ELB-IP: XX.XXX.XX.XXX

Enabling the Function
---------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image1| and select the desired region and project.
#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Under **Listeners**, click **Add Listener**.
#. In the **Add Listener** dialog box, expand **Advanced Settings** and enable the function.
#. Click **OK**.

   .. note::

      This function can be enabled only for HTTPS or HTTP listeners.

Disabling the Function
----------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image3| and select the desired region and project.
#. Hover on |image4| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. Locate the load balancer and click its name.
#. Click **Listeners**, locate the listener, and click |image5| on the right of its name.
#. In the **Modify Listener** dialog box, expand **Advanced Settings** and disable the function.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
.. |image3| image:: /_static/images/en-us_image_0000001495375721.png
.. |image4| image:: /_static/images/en-us_image_0000001495615121.png
.. |image5| image:: /_static/images/en-us_image_0000001495375765.png
