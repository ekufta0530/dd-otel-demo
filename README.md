# OpenTelemetry Collector Demo

This demo contains a client and server applications that use the
opentelemetry Go library for instrumentation and for sending telemetry data
to the opentelemetry collector. The otel collector is configured with the 
Datadog exporter. This is a WIP. The next challenge is connecting traces to logs. 

To send these traces to Datadog, make sure you have a file named sandbox.docker.env 
in your local ~/ directory. At minimum, it should contain your API Key in the following format
`DD_API_KEY=<YOUR_DATADOG_SANDBOX_ORG_API_KEY_HERE>`

The client periodically makes http calls to the server which
create client spans, server spans and metrics that track information like
number of http requests and latency.

This demo presents the typical flow of observability data with multiple
OpenTelemetry Collectors deployed:

- The client and server send data directly to the OTel Collector;
- The OTel Collector then sends the data to the appropriate backend, in this demo
 Datadog;

This demo uses `docker-compose` so to get it running, make sure you have 
docker compose installed and run the following command:

```shell
docker-compose up -d
```

Notes:

- It may take some time for containers to start. This is a WIP but it works as is with a bit of patience.

To clean up any docker container from the demo run `docker-compose down`