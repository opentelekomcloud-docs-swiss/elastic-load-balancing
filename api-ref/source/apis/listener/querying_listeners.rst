:original_name: ListListeners.html

.. _ListListeners:

Querying Listeners
==================

Function
--------

This API is used to query listeners.

Constraints
-----------

Parameters **marker**, **limit**, and **page_reverse** are used for pagination query.

Parameters **marker** and **page_reverse** take effect only when they are used together with parameter **limit**.

URI
---

GET /v3/{project_id}/elb/listeners

.. table:: **Table 1** Path parameters

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

.. table:: **Table 2** Query parameters

   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory       | Type            | Description                                                                                                                                                                                                                      |
   +==============================+=================+=================+==================================================================================================================================================================================================================================+
   | limit                        | No              | Integer         | Specifies the number of records on each page.                                                                                                                                                                                    |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Minimum: **0**                                                                                                                                                                                                                   |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Maximum: **2000**                                                                                                                                                                                                                |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                       | No              | String          | Specifies the ID of the last record on the previous page.                                                                                                                                                                        |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Note:                                                                                                                                                                                                                            |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | -  This parameter must be used together with **limit**.                                                                                                                                                                          |
   |                              |                 |                 | -  If this parameter is not specified, the first page will be queried.                                                                                                                                                           |
   |                              |                 |                 | -  This parameter cannot be left blank or set to an invalid ID.                                                                                                                                                                  |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | page_reverse                 | No              | Boolean         | Specifies the page direction.                                                                                                                                                                                                    |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | The value can be **true** or **false**, and the default value is **false**.                                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | The last page in the list requested with **page_reverse** set to **false** will not contain the "next" link, and the last page in the list requested with **page_reverse** set to **true** will not contain the "previous" link. |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | This parameter must be used together with **limit**.                                                                                                                                                                             |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol_port                | No              | Array           | Specifies the port used by the listener.                                                                                                                                                                                         |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple ports can be queried in the format of *protocol_port=xxx&protocol_port=xxx*.                                                                                                                                            |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                     | No              | Array           | Specifies the protocol used by the listener. The protocol can be UDP, TCP, HTTP, or HTTPS.                                                                                                                                       |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple protocols can be queried in the format of *protocol=xxx&protocol=xxx*.                                                                                                                                                  |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                  | No              | Array           | Provides supplementary information about the listener.                                                                                                                                                                           |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple descriptions can be queried in the format of *description=xxx&description=xxx*.                                                                                                                                         |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_tls_container_ref    | No              | Array           | Specifies the ID of the server certificate used by the listener.                                                                                                                                                                 |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IDs can be queried in the format of *default_tls_container_ref=xxx&default_tls_container_ref=xxx*.                                                                                                                      |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | client_ca_tls_container_ref  | No              | Array           | Specifies the ID of the CA certificate used by the listener.                                                                                                                                                                     |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IDs can be queried in the format of *client_ca_tls_container_ref=xxx&client_ca_tls_container_ref=xxx*.                                                                                                                  |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up               | No              | Boolean         | Specifies the administrative status of the listener. The value can only be **true**.                                                                                                                                             |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | This parameter is unsupported. Please do not use it.                                                                                                                                                                             |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | connection_limit             | No              | Array           | Specifies the maximum number of connections that the load balancer can handle. The default value is **-1**.                                                                                                                      |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple values can be queried in the format of *connection_limit=xxx&connection_limit=xxx*.                                                                                                                                     |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | This parameter is unsupported. Please do not use it.                                                                                                                                                                             |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_pool_id              | No              | Array           | Specifies the ID of the default backend server group. If there is no matched forwarding policy, requests will be routed to the default backend server.                                                                           |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IDs can be queried in the format of *default_pool_id=xxx&default_pool_id=xxx*.                                                                                                                                          |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                           | No              | Array           | Specifies the listener ID.                                                                                                                                                                                                       |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IDs can be queried in the format of *id=xxx&id=xxx*.                                                                                                                                                                    |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                         | No              | Array           | Specifies the name of the listener added to the load balancer.                                                                                                                                                                   |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple names can be queried in the format of *name=xxx&name=xxx*.                                                                                                                                                              |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | http2_enable                 | No              | Boolean         | Specifies whether to use HTTP/2. This parameter is available only for HTTPS listeners. If you configure this parameter for other types of listeners, it will not take effect.                                                    |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Enable HTTP/2 if you want the clients to use HTTP/2 to communicate with the load balancer. However, connections between the load balancer and backend servers use HTTP/1.x by default.                                           |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | loadbalancer_id              | No              | Array           | Specifies the ID of the load balancer that the listener is added to.                                                                                                                                                             |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IDs can be queried in the format of *loadbalancer_id=xxx&loadbalancer_id=xxx*.                                                                                                                                          |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tls_ciphers_policy           | No              | Array           | Specifies the security policy used by the listener. This parameter is available only for HTTPS listeners.                                                                                                                        |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | The value can be **tls-1-0**, **tls-1-1**, **tls-1-2**, or **tls-1-2-strict**, and the default value is **tls-1-0**.                                                                                                             |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple security policies can be queried in the format of *tls_ciphers_policy=xxx&tls_ciphers_policy=xxx*.                                                                                                                      |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_address               | No              | Array           | Specifies the private IP address bound to the backend server. This parameter is used only as a query condition and is not included in the response.                                                                              |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IP addresses can be queried in the format of *member_address=xxx&member_address=xxx*.                                                                                                                                   |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_device_id             | No              | Array           | Specifies the ID of the cloud server that serves as a backend server. This parameter is used only as a query condition and is not included in the response.                                                                      |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IDs can be queried in the format of *member_device_id=xxx&member_device_id=xxx*.                                                                                                                                        |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id        | No              | Array           | Specifies the enterprise project ID.                                                                                                                                                                                             |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | -  If this parameter is not passed, resources in the default enterprise project are queried, and authentication is performed based on the default enterprise project.                                                            |
   |                              |                 |                 | -  If this parameter is passed, its value can be the ID of an existing enterprise project or **all_granted_eps**.                                                                                                                |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | If the value is a specific ID, resources in the specific enterprise project are required. If the value is **all_granted_eps**, resources in all enterprise projects are queried.                                                 |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple IDs can be queried in the format of *enterprise_project_id=xxx&enterprise_project_id=xxx*.                                                                                                                              |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | This parameter is unsupported. Please do not use it.                                                                                                                                                                             |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_member_retry          | No              | Boolean         | Specifies whether to enable health check retries for backend servers.                                                                                                                                                            |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_timeout               | No              | Array           | Specifies the timeout duration for waiting for a request from a backend server, in seconds.                                                                                                                                      |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | This parameter is available only for HTTP and HTTPS listeners. The value ranges from **1** to **300**.                                                                                                                           |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple durations can be queried in the format of *member_timeout=xxx&member_timeout=xxx*.                                                                                                                                      |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | client_timeout               | No              | Array           | Specifies the timeout duration for waiting for a request from a client, in seconds.                                                                                                                                              |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | This parameter is available only for HTTP and HTTPS listeners. The value ranges from **1** to **300**.                                                                                                                           |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple durations can be queried in the format of *client_timeout=xxx&client_timeout=xxx*.                                                                                                                                      |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keepalive_timeout            | No              | Array           | Specifies the idle timeout duration, in seconds.                                                                                                                                                                                 |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | -  For TCP listeners, the value ranges from **10** to **4000**, and the default value is **300**.                                                                                                                                |
   |                              |                 |                 | -  For HTTP and HTTPS listeners, the value ranges from **0** to **4000**, and the default value is **60**.                                                                                                                       |
   |                              |                 |                 | -  For UDP listeners, this parameter does not take effect.                                                                                                                                                                       |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | Multiple durations can be queried in the format of *keepalive_timeout=xxx&keepalive_timeout=xxx*.                                                                                                                                |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | transparent_client_ip_enable | No              | Boolean         | Specifies whether to pass source IP addresses of the clients to backend servers.                                                                                                                                                 |
   |                              |                 |                 |                                                                                                                                                                                                                                  |
   |                              |                 |                 | The value can only be **true** for all types of listeners. If this parameter is not passed, the default value is **true**.                                                                                                       |
   +------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                      |
   +==============+===========+========+==================================================+
   | X-Auth-Token | Yes       | String | Specifies the token used for IAM authentication. |
   +--------------+-----------+--------+--------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------+---------------------------------------------------------------------+-----------------------------------------------------------------+
   | Parameter  | Type                                                                | Description                                                     |
   +============+=====================================================================+=================================================================+
   | request_id | String                                                              | Specifies the request ID. The value is automatically generated. |
   +------------+---------------------------------------------------------------------+-----------------------------------------------------------------+
   | page_info  | :ref:`PageInfo <listlisteners__response_pageinfo>` object           | Listener pagination information                                 |
   +------------+---------------------------------------------------------------------+-----------------------------------------------------------------+
   | listeners  | Array of :ref:`Listener <listlisteners__response_listener>` objects | Lists the listeners.                                            |
   +------------+---------------------------------------------------------------------+-----------------------------------------------------------------+

.. _listlisteners__response_pageinfo:

.. table:: **Table 5** PageInfo

   +-----------------+---------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                                                                              |
   +=================+=========+==========================================================================================================================================+
   | previous_marker | String  | Specifies the ID of the first record in the pagination query result. This parameter will not be returned if no query result is returned. |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------------------------------------+
   | next_marker     | String  | Marks the start record on the next page in the pagination query result. This parameter will not be returned if there is no next page.    |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------------------------------------+
   | current_count   | Integer | Specifies the number of records.                                                                                                         |
   +-----------------+---------+------------------------------------------------------------------------------------------------------------------------------------------+

.. _listlisteners__response_listener:

.. table:: **Table 6** Listener

   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Type                                                                                | Description                                                                                                                                                                                                                                 |
   +==============================+=====================================================================================+=============================================================================================================================================================================================================================================+
   | admin_state_up               | Boolean                                                                             | Specifies the administrative status of the listener. And the value can only be **true**.                                                                                                                                                    |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter is unsupported. Please do not use it.                                                                                                                                                                                        |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | Default: **true**                                                                                                                                                                                                                           |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | client_ca_tls_container_ref  | String                                                                              | Specifies the ID of the CA certificate used by the listener.                                                                                                                                                                                |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | connection_limit             | Integer                                                                             | Specifies the maximum number of connections. The default value is **-1**.                                                                                                                                                                   |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter is unsupported. Please do not use it.                                                                                                                                                                                        |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                   | String                                                                              | Specifies the time when the listener was created.                                                                                                                                                                                           |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_pool_id              | String                                                                              | Specifies the ID of the default backend server group. If there is no matched forwarding policy, requests are forwarded to the default backend server.                                                                                       |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_tls_container_ref    | String                                                                              | Specifies the ID of the server certificate used by the listener.                                                                                                                                                                            |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                  | String                                                                              | Provides supplementary information about the listener.                                                                                                                                                                                      |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | http2_enable                 | Boolean                                                                             | Specifies whether to use HTTP/2. This parameter is available only for HTTPS listeners. If you configure this parameter for other types of listeners, it will not take effect.                                                               |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | Enable HTTP/2 if you want the clients to use HTTP/2 to communicate with the load balancer. However, connections between the load balancer and backend servers use HTTP/1.x by default.                                                      |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | Default: **true**                                                                                                                                                                                                                           |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                           | String                                                                              | Specifies the listener ID.                                                                                                                                                                                                                  |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | insert_headers               | :ref:`ListenerInsertHeaders <listlisteners__response_listenerinsertheaders>` object | Specifies the HTTP header fields.                                                                                                                                                                                                           |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | loadbalancers                | Array of :ref:`LoadBalancerRef <listlisteners__response_loadbalancerref>` objects   | Specifies the ID of the load balancer that the listener is added to.                                                                                                                                                                        |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                         | String                                                                              | Specifies the listener name.                                                                                                                                                                                                                |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id                   | String                                                                              | Specifies the ID of the project where the listener is used.                                                                                                                                                                                 |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol                     | String                                                                              | Specifies the protocol used by the listener.                                                                                                                                                                                                |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol_port                | Integer                                                                             | Specifies the port used by the listener.                                                                                                                                                                                                    |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | Minimum: **1**                                                                                                                                                                                                                              |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | Maximum: **65535**                                                                                                                                                                                                                          |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sni_container_refs           | Array of strings                                                                    | Lists the IDs of SNI certificates (server certificates with domain names) used by the listener.                                                                                                                                             |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | Each SNI certificate can have up to 30 domain names, and each domain name in the SNI certificate must be unique.                                                                                                                            |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter will be ignored and an empty array will be returned if the listener's protocol is not HTTPS.                                                                                                                                 |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                         | Array of :ref:`Tag <listlisteners__response_tag>` objects                           | Lists the tags.                                                                                                                                                                                                                             |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at                   | String                                                                              | Specifies the time when the listener was updated.                                                                                                                                                                                           |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tls_ciphers_policy           | String                                                                              | Specifies the security policy used by the listener. This parameter is available only for HTTPS listeners.                                                                                                                                   |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | The value can be **tls-1-0**, **tls-1-1**, **tls-1-2**, or **tls-1-2-strict**, and the default value is **tls-1-0**.                                                                                                                        |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_member_retry          | Boolean                                                                             | Specifies whether to enable health check retries for backend servers. This parameter is available only for HTTP and HTTPS listeners.                                                                                                        |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keepalive_timeout            | Integer                                                                             | Specifies the idle timeout duration, in seconds.                                                                                                                                                                                            |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | -  For TCP listeners, the value ranges from **10** to **4000**, and the default value is **300**.                                                                                                                                           |
   |                              |                                                                                     | -  For HTTP and HTTPS listeners, the value ranges from **0** to **4000**, and the default value is **60**.                                                                                                                                  |
   |                              |                                                                                     | -  For UDP listeners, this parameter does not take effect.                                                                                                                                                                                  |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | client_timeout               | Integer                                                                             | Specifies the timeout duration for waiting for a request from a client, in seconds.                                                                                                                                                         |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter is available only for HTTP and HTTPS listeners. The value ranges from **1** to **300**, and the default value is **60**.                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_timeout               | Integer                                                                             | Specifies the timeout duration for waiting for a request from a backend server, in seconds.                                                                                                                                                 |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter is available only for HTTP and HTTPS listeners. The value ranges from **1** to **300**, and the default value is **60**.                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ipgroup                      | :ref:`ListenerIpGroup <listlisteners__response_listeneripgroup>` object             | Specifies the IP address group associated with the listener.                                                                                                                                                                                |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter is unsupported. Please do not use it.                                                                                                                                                                                        |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | transparent_client_ip_enable | Boolean                                                                             | Specifies whether to pass source IP addresses of the clients to backend servers.                                                                                                                                                            |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | The value can only be **true** for all types of listeners. If this parameter is not passed, the default value is **true**.                                                                                                                  |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enhance_l7policy_enable      | Boolean                                                                             | Specifies whether to enable advanced forwarding. The value can be **true** or **false** (default).                                                                                                                                          |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | -  **true** indicates that advanced forwarding will be enabled.                                                                                                                                                                             |
   |                              |                                                                                     | -  **false** indicates that advanced forwarding will not be enabled.                                                                                                                                                                        |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | The following parameters will be available only when advanced forwarding is enabled:                                                                                                                                                        |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | -  **redirect_url_config**                                                                                                                                                                                                                  |
   |                              |                                                                                     | -  **fixed_response_config**                                                                                                                                                                                                                |
   |                              |                                                                                     | -  **priority**                                                                                                                                                                                                                             |
   |                              |                                                                                     | -  **conditions**                                                                                                                                                                                                                           |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | For details, see the descriptions in the APIs of forwarding policies and forwarding rules.                                                                                                                                                  |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter is unsupported. Please do not use it.                                                                                                                                                                                        |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_policy_id           | String                                                                              | Specifies the ID of the custom security policy. Custom security policies take effect only for dedicated load balancers. If both **security_policy_id** and **tls_ciphers_policy** are passed, only **security_policy_id** will take effect. |
   |                              |                                                                                     |                                                                                                                                                                                                                                             |
   |                              |                                                                                     | This parameter is unsupported. Please do not use it.                                                                                                                                                                                        |
   +------------------------------+-------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listlisteners__response_listenerinsertheaders:

.. table:: **Table 7** ListenerInsertHeaders

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                        |
   +=======================+=======================+====================================================================================================================================================================================================================================================================+
   | X-Forwarded-ELB-IP    | Boolean               | Specifies whether to transparently transmit the load balancer EIP to backend servers. If **X-Forwarded-ELB-IP** is set to **true**, the load balancer EIP will be stored in the HTTP header and passed to backend servers.                                         |
   |                       |                       |                                                                                                                                                                                                                                                                    |
   |                       |                       | Default: **false**                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Forwarded-Port      | Boolean               | Specifies whether to transparently transmit the listening port of the load balancer to backend servers. If **X-Forwarded-Port** is set to **true**, the listening port of the load balancer will be stored in the HTTP header and passed to backend servers.       |
   |                       |                       |                                                                                                                                                                                                                                                                    |
   |                       |                       | Default: **false**                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Forwarded-For-Port  | Boolean               | Specifies whether to transparently transmit the source port of the client to backend servers. If **X-Forwarded-For-Port** is set to **true**, the source port of the client will be stored in the HTTP header and passed to backend servers.                       |
   |                       |                       |                                                                                                                                                                                                                                                                    |
   |                       |                       | Default: **false**                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Forwarded-Host      | Boolean               | Specifies whether to rewrite the **X-Forwarded-Host** header. If **X-Forwarded-Host** is set to **true**, **X-Forwarded-Host** in the request header from the clients can be set to **Host** in the request header sent from the load balancer to backend servers. |
   |                       |                       |                                                                                                                                                                                                                                                                    |
   |                       |                       | Default: **true**                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listlisteners__response_loadbalancerref:

.. table:: **Table 8** LoadBalancerRef

   ========= ====== ===============================
   Parameter Type   Description
   ========= ====== ===============================
   id        String Specifies the load balancer ID.
   ========= ====== ===============================

.. _listlisteners__response_tag:

.. table:: **Table 9** Tag

   ========= ====== ========================
   Parameter Type   Description
   ========= ====== ========================
   key       String Specifies the tag key.
   value     String Specifies the tag value.
   ========= ====== ========================

.. _listlisteners__response_listeneripgroup:

.. table:: **Table 10** ListenerIpGroup

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                           |
   +=======================+=======================+=======================================================================================================================+
   | ipgroup_id            | String                | Specifies the ID of the IP address group associated with the listener.                                                |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  If **ip_list** is set to **[]** and **type** to **whitelist**, no IP addresses are allowed to access the listener. |
   |                       |                       | -  If **ip_list** is set to **[]** and **type** to **blacklist**, any IP address is allowed to access the listener.   |
   |                       |                       | -  The specified IP address group must exist and this parameter cannot be set to **null**.                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | enable_ipgroup        | Boolean               | Specifies whether to enable access control.                                                                           |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **true**: Access control is enabled.                                                                               |
   |                       |                       | -  **false**: Access control is disabled.                                                                             |
   |                       |                       |                                                                                                                       |
   |                       |                       | A listener with access control enabled can be directly deleted.                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Specifies how access to the listener is controlled.                                                                   |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  **white**: A whitelist is configured. Only IP addresses in the whitelist can access the listener.                  |
   |                       |                       | -  **black**: A blacklist is configured. IP addresses in the blacklist are not allowed to access the listener.        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   GET

   https://{ELB_Endpoint}/v3/060576782980d5762f9ec014dd2f1148/elb/listeners?limit=2&marker=22e221c4-37c7-45d6-a76a-6e5a3bf485ba

Example Responses
-----------------

**Status code: 200**

Successful request.

.. code-block::

   {
     "request_id" : "e77338298c98d52202fd60bdacec0d75",
     "listeners" : [ {
       "id" : "683cf917-3e51-4c41-830c-bc3a57e090f0",
       "name" : "My listener",
       "protocol_port" : 90,
       "protocol" : "HTTPS",
       "description" : "",
       "default_tls_container_ref" : "4e7761d7c7d141c389479f2641c8bff8",
       "admin_state_up" : true,
       "loadbalancers" : [ {
         "id" : "ac82ca77-8be3-4d65-9c4d-155771b463df"
       } ],
       "client_ca_tls_container_ref" : null,
       "project_id" : "060576782980d5762f9ec014dd2f1148",
       "sni_container_refs" : [ ],
       "connection_limit" : -1,
       "default_pool_id" : null,
       "tls_ciphers_policy" : "tls-1-0",
       "security_policy_id" : null,
       "tags" : [ ],
       "created_at" : "2021-04-02T07:48:38Z",
       "updated_at" : "2021-04-02T07:48:38Z",
       "http2_enable" : false,
       "insert_headers" : {
         "X-Forwarded-ELB-IP" : false,
         "X-Forwarded-Host" : true,
         "X-Forwarded-For-Port" : false,
         "X-Forwarded-Port" : false
       },
       "member_timeout" : 60,
       "client_timeout" : 60,
       "keepalive_timeout" : 60,
       "ipgroup" : null,
       "enable_member_retry" : true,
       "transparent_client_ip_enable" : true,
       "enhance_l7policy_enable" : false
     }, {
       "id" : "1173360b-5911-4aa9-a1ec-05e9f714370c",
       "name" : "listener-sshd",
       "protocol_port" : 22,
       "protocol" : "TCP",
       "description" : "",
       "default_tls_container_ref" : null,
       "admin_state_up" : true,
       "loadbalancers" : [ {
         "id" : "4d196846-d63c-4e7b-9875-2c4f04a48661"
       } ],
       "client_ca_tls_container_ref" : null,
       "project_id" : "060576782980d5762f9ec014dd2f1148",
       "sni_container_refs" : [ ],
       "connection_limit" : -1,
       "default_pool_id" : "6350052f-e060-4f80-b92f-f21255dba4c4",
       "tls_ciphers_policy" : null,
       "security_policy_id" : null,
       "tags" : [ ],
       "created_at" : "2021-04-01T08:21:15Z",
       "updated_at" : "2021-04-01T08:21:15Z",
       "http2_enable" : false,
       "insert_headers" : {
         "X-Forwarded-ELB-IP" : false,
         "X-Forwarded-Host" : true,
         "X-Forwarded-For-Port" : false,
         "X-Forwarded-Port" : false
       },
       "member_timeout" : null,
       "client_timeout" : null,
       "keepalive_timeout" : 4000,
       "ipgroup" : null,
       "enable_member_retry" : true,
       "transparent_client_ip_enable" : true,
       "enhance_l7policy_enable" : false
     } ],
     "page_info" : {
       "next_marker" : "1173360b-5911-4aa9-a1ec-05e9f714370c",
       "previous_marker" : "683cf917-3e51-4c41-830c-bc3a57e090f0",
       "current_count" : 2
     }
   }

Status Codes
------------

=========== ===================
Status Code Description
=========== ===================
200         Successful request.
=========== ===================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
