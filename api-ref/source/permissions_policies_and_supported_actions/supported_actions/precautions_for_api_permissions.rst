:original_name: elb_sq_lb_0012.html

.. _elb_sq_lb_0012:

Precautions for API Permissions
===============================

**elb:quotas:list** controls the fine-grained permission for quota display.

**elb:logtanks:create**, **elb:logtanks:list**, **elb:logtanks:get**, **elb:logtanks:put**, and **elb:logtanks:delete** control the fine-grained permission for log creation, log list query, log details query, log update, and log deletion.

The logging function relies on LTS, and the **lts:*:get\*** and **lts:*:list\*** permissions at the project level are required.

The monitoring function relies on Cloud Eye.
