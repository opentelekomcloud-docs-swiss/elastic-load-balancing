:original_name: elb_faq_0087.html

.. _elb_faq_0087:

How Can I Handle Error Codes?
=============================

Common error codes include 400, 403, 502, and 504. If any of these codes is returned, it is recommended that you access the backend server to check if it can respond properly.

If the backend server responds properly, rectify the fault by referring to :ref:`Table 1 <elb_faq_0087__table19909154633611>`. If the fault persists, contact the administrator.

.. _elb_faq_0087__table19909154633611:

.. table:: **Table 1** Common error codes

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Error Code            | Description           | Possible Causes                                                                                                                                                                    |
   +=======================+=======================+====================================================================================================================================================================================+
   | 400                   | Bad Request           | -  The client sent a malformed request that does not comply with the HTTP specification.                                                                                           |
   |                       |                       | -  An HTTP request was sent to the HTTPS port.                                                                                                                                     |
   |                       |                       | -  The size of the request header exceeded 64 KB.                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 401                   | Unauthorized          | Authentication on the backend server failed. (This error code is returned to the client by the backend server.)                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 403                   | Forbidden             | The request was intercepted by the backend server. (This error code is returned to the client by the backend server.)                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 404                   | Not Found             | -  The backend server is abnormal or the application does not exist. (This error code is returned to the client by the backend server.)                                            |
   |                       |                       | -  The forwarding policy was incorrectly configured, and the request was not routed to the right backend server.                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 408                   | Request Timeout       | The client did not send the request within the time that the server was configured to wait, which is 60s by default. Sending a TCP keepalive packet does not prevent this timeout. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 413                   | Payload Too Large     | The size of the request body sent by the client exceeded 10 GB.                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 414                   | URI Too Long          | The request URL or query string parameter sent by the client was too long.                                                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 499                   | Client Closed Request | The client disconnected from the load balancer before receiving a response from the load balancer. This error code is recorded only in access logs.                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 500                   | Internal Server Error | There was an internal error. (This error code is returned to the client by the backend server.)                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 501                   | Not Implemented       | The load balancer failed to identify the request.                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                    |
   |                       |                       | The value of the **Transfer-Encoding** header field is not **chunked** or **identity**.                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 502                   | Bad Gateway           | -  The port used by the backend server was incorrectly configured.                                                                                                                 |
   |                       |                       | -  The load balancer received a TCP RST packet from the backend server when attempting to establish a connection with or sending data to the backend server.                       |
   |                       |                       | -  The format of the response from the backend server was incorrect, or the response contained an invalid HTTP response header.                                                    |
   |                       |                       | -  The backend server is incorrectly configured, for example, incorrect routes or firewall.                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 503                   | Service Unavailable   | The application or backend server was unavailable. Generally, this error code is returned by the backend server.                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 504                   | Gateway Timeout       | -  During the first connection, the load balancer fails to connect to the backend server before the connection times out. (The default timeout is 5 seconds).                      |
   |                       |                       | -  The load balancer established a connection with the backend server, but did not respond before the response timeout (which is 300s by default) elapsed.                         |
   |                       |                       | -  The firewall of the subnet did not allow the load balancer to access backend servers in the subnet.                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
