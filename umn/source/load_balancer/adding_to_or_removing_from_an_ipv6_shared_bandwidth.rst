:original_name: elb_lb_000011.html

.. _elb_lb_000011:

Adding to or Removing from an IPv6 Shared Bandwidth
===================================================

Scenarios
---------

After you bind an IPv6 address to a load balancer, you can add the load balancer to a shared bandwidth to enable it to route requests over the Internet. After you are finished with the shared bandwidth, you can remove the load balancer from the shared bandwidth, so that it can only route requests within a VPC.

.. note::

   The private IPv4 address is added to a shared bandwidth by default after you create the load balancer.

Adding to an IPv6 Shared Bandwidth
----------------------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.

#. On the **Elastic Load Balancers** tab page, locate the load balancer that you want to add to a shared bandwidth, and click **More** > **Add to Shared Bandwidth** in the **Operation** column.

#. In the **Add to Shared Bandwidth** dialog box, select the shared bandwidth to which you want to add the dedicated load balancer.

   If no shared bandwidths are available, buy one as prompted.

#. Click **OK**.

Removing from an IPv6 Shared Bandwidth
--------------------------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image3| and select the desired region and project.
#. Hover on |image4| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. On the **Elastic Load Balancers** tab page, locate the load balancer that you want to remove from a shared bandwidth, and click **More** > **Remove from IPv6 Shared Bandwidth** in the **Operation** column.
#. In the **Remove from IPv6 Shared Bandwidth** dialog box, confirm the shared bandwidth from which you want to remove the load balancer.

   .. note::

      After the load balancer is removed from the shared bandwidth, the load balancer cannot route requests over the Internet.

#. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
.. |image3| image:: /_static/images/en-us_image_0000001495375721.png
.. |image4| image:: /_static/images/en-us_image_0000001495615121.png
