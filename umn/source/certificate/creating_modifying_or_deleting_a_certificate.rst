:original_name: elb_ug_zs_0004.html

.. _elb_ug_zs_0004:

Creating, Modifying, or Deleting a Certificate
==============================================

Scenarios
---------

To enable authentication for securing data transmission over HTTPS, you can create certificates for load balancers. You can also modify and delete certificates.

.. note::

   -  A certificate can be bound to only one type of load balancer. Ensure that you have selected the correct type.

.. _elb_ug_zs_0004__section26868475171830:

Creating a Certificate
----------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image1| and select the desired region and project.
#. Hover on |image2| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. In the navigation pane on the left, choose **Certificates**.
#. Click **Create Certificate**. In the **Create Certificate** dialog box, configure the parameters.

   -  **Certificate Name**

   -  **Certificate Type**

      -  **Server certificate**: used for SSL handshake negotiations if an HTTPS listener is used. Both the certificate content and private key are required.
      -  **CA certificate**: issued by a certificate authority (CA) and used to verify the certificate issuer. If HTTPS mutual authentication is required, HTTPS connections can be established only when the client provides a certificate issued by a specific CA.

   -  **Certificate**: The content must be in PEM format. This parameter is mandatory when **Certificate Type** is set to **Server certificate** or **CA certificate**.

      Click **Upload** and select the certificate to be uploaded. Ensure that your browser is of the latest version.

      The format of the certificate body is as follows:

      .. code-block::

         -----BEGIN CERTIFICATE-----
         Base64-encoded certificate
         -----END CERTIFICATE-----

   -  **Private Key**: This parameter is mandatory when **Certificate Type** is set to **Server certificate**.

      Click **Upload** and select the private key to be uploaded. Ensure that your browser is of the latest version.

      **Private Key**: This must be an unencrypted private key. The format is as follows:

      .. code-block::

         -----BEGIN PRIVATE KEY-----
         [key]
         -----END PRIVATE KEY-----

   -

      .. note::

         If there is a certificate chain, you need to configure the certificates in the following sequence: sub-certificate (server certificate), intermediate certificate, and root certificate. If the root certificate has been preset on the server and is not contained in the issued certificates, first configure the sub-certificate (server certificate) and then the intermediate certificate.

      For example, if a CA issued a private key **private.key** and two certificates: a sub-certificate (server certificate) **server.cer** and an intermediate certificate **mid.crt**, paste the content of **server.cer** in the **Certificate** text box, press **Enter**, then paste the content of **mid.crt** in the **Certificate** text box, and paste the content of **private.key** in the **Private Key** text box to make the entire certificate chain take effect. The format of the certificate body in a certificate chain is as follows:

      Certificate body

      .. code-block::

         -----BEGIN CERTIFICATE-----
         Content of the server certificate server.cer
         -----END CERTIFICATE-----
         -----BEGIN CERTIFICATE-----
         Content of the intermediate certificate mid.crt
         -----END CERTIFICATE-----

      Private key

      .. code-block::

         -----BEGIN PRIVATE KEY-----
         Content of the private key private.key
         -----END PRIVATE KEY-----

   -  **Domain Name**

      If the created certificate will be used for SNI, you need to specify a domain name for each certificate, and the domain name must be the same as that in the certificate.

   -  **Description**

6. Click **OK**.

Modifying a Certificate
-----------------------

#. Log in to the management console.
#. In the upper left corner of the page, click |image3| and select the desired region and project.
#. Hover on |image4| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. In the navigation pane on the left, choose **Certificates**.
#. Locate the certificate and click **Modify** in the **Operation** column.
#. Modify the parameters as required.
#. Click **OK**.

Deleting a Certificate
----------------------

Only certificates that are not in use can be deleted.

#. Log in to the management console.
#. In the upper left corner of the page, click |image5| and select the desired region and project.
#. Hover on |image6| in the upper left corner to display **Service List** and choose **Network** > **Elastic Load Balancing**.
#. In the navigation pane on the left, choose **Certificates**.
#. Locate the certificate and click **Delete** in the **Operation** column.
#. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001495375721.png
.. |image2| image:: /_static/images/en-us_image_0000001495615121.png
.. |image3| image:: /_static/images/en-us_image_0000001495375721.png
.. |image4| image:: /_static/images/en-us_image_0000001495615121.png
.. |image5| image:: /_static/images/en-us_image_0000001495375721.png
.. |image6| image:: /_static/images/en-us_image_0000001495615121.png
