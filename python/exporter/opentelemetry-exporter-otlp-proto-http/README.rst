OpenTelemetry Metrics over HTTP Exporter
===================================================

|pypi|

.. |pypi| image:: https://badge.fury.io/py/opentelemetry-exporter-otlp-proto-http.svg
   :target: https://pypi.org/project/opentelemetry-exporter-otlp-proto-http/

This library allows to export data to the OpenTelemetry Collector using the OpenTelemetry Protocol using HTTP.

Installation
------------

::

     pip install sb-opentelemetry-extension-exporter-otlp-proto-http


.. code-block:: python

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


References
----------

* `OpenTelemetry Collector Exporter <https://opentelemetry-python.readthedocs.io/en/latest/exporter/otlp/otlp.html>`_
* `OpenTelemetry Collector <https://github.com/open-telemetry/opentelemetry-collector/>`_
* `OpenTelemetry <https://opentelemetry.io/>`_
* `OpenTelemetry Protocol Specification <https://github.com/open-telemetry/oteps/blob/main/text/0035-opentelemetry-protocol.md>`_
