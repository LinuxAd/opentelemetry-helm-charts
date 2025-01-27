# Upgrade guidelines

## 0.15.0 to 0.16.0

Jaeger receiver no longer supports remote sampling. To be able to perform an update, it must be deactivated or replaced by a configuration of the [jaegerremotesampling](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/v0.61.0/extension/jaegerremotesampling) extension.<br/>
It is important that the `jaegerremotesampling` extension and the `jaegerreceiver` do not use the same port.<br/>To increase the collector version afterwards, the update must be triggered again by restarting the operator. Alternatively, the `OpenTelemetryCollector` CRD can be re-created. [otel-contrib#14707](https://github.com/open-telemetry/opentelemetry-collector-contrib/issues/14707)

## 0.13.0 to 0.14.0

[Allow byo webhooks and cert](https://github.com/open-telemetry/opentelemetry-helm-charts/pull/411)

The ability to use admission webhooks has been moved from `admissionWebhooks.enabled` to `admissionWebhooks.create` as it now supports more use cases.

In order to completely disable admission webhooks you need to explicitly set the environment variable `ENABLE_WEBHOOKS: "false"` in `.Values.manager.env` .
