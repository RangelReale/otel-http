# OpenTelemetry Collector Metrics over HTTP Exporter

```shell
pip install rr-opentelemetry-extension-exporter-otlp-proto-http
```

Usage:

```python
from opentelemetry import metrics
from opentelemetry.sdk.resources import SERVICE_NAME, Resource
from opentelemetry.sdk.metrics import MeterProvider
from opentelemetry.sdk.metrics.export import PeriodicExportingMetricReader
from opentelemetry.extension.exporter.otlp.proto.http.metric_exporter import OTLPMetricExporter

resource = Resource(attributes={
    SERVICE_NAME: "service",
})

metric_reader = PeriodicExportingMetricReader(OTLPMetricExporter())
provider = MeterProvider(resource=resource, metric_readers=[metric_reader])

# Sets the global default meter provider
metrics.set_meter_provider(provider)
```
