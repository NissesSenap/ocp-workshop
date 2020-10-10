# Requirement

To be able to use ServiceMonitor cr you need to install the prometheus operator.

If you are running on OCP you can follow this [document](https://docs.openshift.com/container-platform/4.5/monitoring/monitoring-your-own-services.html#enabling-monitoring-of-your-own-services_monitoring-your-own-services)

If you are using [CRC](https://developers.redhat.com/products/codeready-containers/overview) this won't work by default.
You can follow these [instructions](https://code-ready.github.io/crc/#starting-monitoring-alerting-telemetry_gsg) to enable the built in monitoring.

If you are on kubernetes and haven't installed prometheus already checkout [operatorhub](https://operatorhub.io/operator/prometheus).
