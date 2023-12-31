:original_name: ShowL7Rule.html

.. _ShowL7Rule:

Viewing Details of a Forwarding Rule
====================================

Function
--------

This API is used to view details of a forwarding rule.

URI
---

GET /v3/{project_id}/elb/l7policies/{l7policy_id}/rules/{l7rule_id}

.. table:: **Table 1** Path parameters

   =========== ========= ====== ================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ================================
   project_id  Yes       String Specifies the project ID.
   l7policy_id Yes       String Specifies the forwarding policy.
   l7rule_id   Yes       String Specifies the forwarding rule.
   =========== ========= ====== ================================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                      |
   +==============+===========+========+==================================================+
   | X-Auth-Token | Yes       | String | Specifies the token used for IAM authentication. |
   +--------------+-----------+--------+--------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------+----------------------------------------------------+-----------------------------------------------------------------+
   | Parameter  | Type                                               | Description                                                     |
   +============+====================================================+=================================================================+
   | request_id | String                                             | Specifies the request ID. The value is automatically generated. |
   +------------+----------------------------------------------------+-----------------------------------------------------------------+
   | rule       | :ref:`L7Rule <showl7rule__response_l7rule>` object | Specifies the forwarding rule.                                  |
   +------------+----------------------------------------------------+-----------------------------------------------------------------+

.. _showl7rule__response_l7rule:

.. table:: **Table 4** L7Rule

   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                                                                                                                                                                                                                       |
   +=======================+============================================================================+===================================================================================================================================================================================================================================================================+
   | admin_state_up        | Boolean                                                                    | Specifies the administrative status of the forwarding rule. The default value is **true**.                                                                                                                                                                        |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | This parameter is unsupported. Please do not use it.                                                                                                                                                                                                              |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | compare_type          | String                                                                     | Specifies how requests are matched with the domain name or URL.                                                                                                                                                                                                   |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  If **type** is set to **HOST_NAME**, this parameter can only be set to **EQUAL_TO**.                                                                                                                                                                           |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  If **type** is set to **PATH**, this parameter can be set to **REGEX**, **STARTS_WITH**, or **EQUAL_TO**.                                                                                                                                                      |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key                   | String                                                                     | Specifies the key of the match content. This parameter will not take effect when **type** is set to **HOST_NAME** or **PATH**. It can be updated but will not take effect.                                                                                        |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | This parameter is unsupported. Please do not use it.                                                                                                                                                                                                              |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | Minimum: **1**                                                                                                                                                                                                                                                    |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | Maximum: **255**                                                                                                                                                                                                                                                  |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                     | Specifies the project ID.                                                                                                                                                                                                                                         |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                                                                     | Specifies the match content. The value can be one of the following:                                                                                                                                                                                               |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  **HOST_NAME**: A domain name will be used for matching.                                                                                                                                                                                                        |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  **PATH**: A URL will be used for matching.                                                                                                                                                                                                                     |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | If **type** is set to **HOST_NAME**, **PATH**, **METHOD**, or **SOURCE_IP**, only one forwarding rule can be created for each type.                                                                                                                               |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                                                                     | Specifies the value of the match item. For example, if a domain name is used for matching, **value** is the domain name.                                                                                                                                          |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  If **type** is set to **HOST_NAME**, the value can contain letters, digits, hyphens (-), and periods (.) and must start with a letter or digit. If you want to use a wildcard domain name, enter an asterisk (``*``) as the leftmost label of the domain name. |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  If **type** is set to **PATH** and **compare_type** to **STARTS_WITH** or **EQUAL_TO**, the value must start with a slash (/) and can contain only letters, digits, and special characters ``_~';@^-%#&$.*+?,=!:|/()[]{}``                                     |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | Minimum: **1**                                                                                                                                                                                                                                                    |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | Maximum: **128**                                                                                                                                                                                                                                                  |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | provisioning_status   | String                                                                     | Specifies the provisioning status of the forwarding rule.                                                                                                                                                                                                         |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | invert                | Boolean                                                                    | Specifies whether reverse matching is supported. The value is fixed at **false**. This parameter can be updated but remains invalid.                                                                                                                              |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | Default: **false**                                                                                                                                                                                                                                                |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                                                                     | Specifies the forwarding policy ID.                                                                                                                                                                                                                               |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | conditions            | Array of :ref:`RuleCondition <showl7rule__response_rulecondition>` objects | Specifies the matching conditions of the forwarding rule.                                                                                                                                                                                                         |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  If **conditions** is specified, **key** and **value** will not take effect, and the value of this parameter will contain all conditions configured for the forwarding rule. The keys in the list must be the same, whereas each value must be unique.          |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | -  If **conditions** is not specified, the values of **key** and **value** are displayed.                                                                                                                                                                         |
   |                       |                                                                            |                                                                                                                                                                                                                                                                   |
   |                       |                                                                            | This parameter is unsupported. Please do not use it.                                                                                                                                                                                                              |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showl7rule__response_rulecondition:

.. table:: **Table 5** RuleCondition

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================================================================================================================================================================================================================+
   | key                   | String                | Specifies the key of match item. This parameter is left blank.                                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       | Maximum: **128**                                                                                                                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Specifies the value of the match item.                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       | -  If **type** is set to **HOST_NAME**, **key** is left blank, and **value** indicates the domain name, which can contain 1 to 128 characters, including letters, digits, hyphens (-), periods (.), and asterisks (*), and must start with a letter, digit, or asterisk (*). If you want to use a wildcard domain name, enter an asterisk (``*``) as the leftmost label of the domain name. |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       | -  If **type** is set to **PATH**, **key** is left blank, and **value** indicates the request path, which can contain 1 to 128 characters. If **compare_type** is set to **STARTS_WITH** or **EQUAL_TO** for the forwarding rule, the value must start with a slash (/) and can contain only letters, digits, and special characters ``_~';@^-%#&$.*+?,=!:|/()[]{}``                        |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       | Maximum: **128**                                                                                                                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   GET

   https://{elb_endpoint}/v3/99a3fff0d03c428eac3678da6a7d0f24/elb/l7policies/cf4360fd-8631-41ff-a6f5-b72c35da74be/rules/84f4fcae-9c15-4e19-a99f-72c0b08fd3d7

Example Responses
-----------------

**Status code: 200**

Successful request.

.. code-block::

   {
     "rule" : {
       "compare_type" : "STARTS_WITH",
       "provisioning_status" : "ACTIVE",
       "project_id" : "99a3fff0d03c428eac3678da6a7d0f24",
       "invert" : false,
       "admin_state_up" : true,
       "value" : "/ccc.html",
       "key" : null,
       "type" : "PATH",
       "id" : "84f4fcae-9c15-4e19-a99f-72c0b08fd3d7"
     },
     "request_id" : "0d799435-259e-459f-b2bc-0beee06f6a77"
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
