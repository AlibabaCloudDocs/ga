# Overdue instructions {#concept_av3_d5w_5db .concept}

The acceleration service will be stopped if a bill is overdue.  Renew your service on time to reduce the impact on your business.

## Stop instances {#section_kw1_t5w_5db .section}

The instance is locked and the service is stopped if a bill is overdue but it has not been overdue for more than 15 days.  In this case, you cannot perform any operation on the instance, and the instance no longer forwards any traffic. However, the IP address and related configurations of the instance are kept. If you pay your overdue bill during this period, the acceleration service is automatically resumed.

## Release instances {#section_qmv_t5w_5db .section}

If you do not pay an overdue bill within 15 days of the service being stopped, the instance is released. The IP address and the instance configurations are also deleted, and cannot be restored.

