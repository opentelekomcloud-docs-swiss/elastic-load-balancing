:original_name: elb_ug_sj_0001.html

.. _elb_ug_sj_0001:

Key Operations Recorded by CTS
==============================

You can use CTS to record operations on ELB for query, auditing, and backtracking.

:ref:`Table 1 <elb_ug_sj_0001__table1419082716297>` lists the operations recorded by CTS.

.. _elb_ug_sj_0001__table1419082716297:

.. table:: **Table 1** ELB operations recorded by CTS

   ================================ ============= ===================
   Action                           Resource Type Trace
   ================================ ============= ===================
   Configuring access logs          logtank       createLogtank
   Deleting access logs             logtank       deleteLogtank
   Creating a certificate           certificate   createCertificate
   Modifying a certificate          certificate   updateCertificate
   Deleting a certificate           certificate   deleteCertificate
   Creating a health check          healthmonitor createHealthMonitor
   Modifying a health check         healthmonitor updateHealthMonitor
   Deleting a health check          healthmonitor deleteHealthMonitor
   Adding a forwarding policy       l7policy      createL7policy
   Modifying a forwarding policy    l7policy      updateL7policy
   Deleting a forwarding policy     l7policy      deleteL7policy
   Adding a forwarding rule         l7rule        createl7rule
   Modifying a forwarding rule      l7rule        updateL7rule
   Deleting a forwarding rule       l7rule        deleteL7rule
   Adding a listener                listener      createListener
   Modifying a listener             listener      updateListener
   Deleting a listener              listener      deleteListener
   Creating a load balancer         loadbalancer  createLoadbalancer
   Modifying a load balancer        loadbalancer  updateLoadbalancer
   Deleting a load balancer         loadbalancer  deleteLoadbalancer
   Adding a backend server          member        createMember
   Modifying a backend server       member        updateMember
   Removing a backend server        member        batchUpdateMember
   Creating a backend server group  pool          createPool
   Modifying a backend server group pool          updatPool
   Deleting a backend server group  pool          deletePool
   ================================ ============= ===================
