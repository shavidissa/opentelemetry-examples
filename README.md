# Sending Trace Data to Tanzu Observability by Wavefront

This README is for all users who want to send OpenTelemetry trace data or metrics data to Tanzu Observability. This README explains how you can start sending data to Tanzu observability with links to the Documentation. This repository includes specific examples for using the OpenTelemetry collector in java, python, and .NET, etc.

## Overview

If your application uses an OpenTelemetry SDK, you can configure the application to send trace data or metrics data to Tanzu Observability using the Wavefront Proxy or the OpenTelemetry Collector.

## Prerequisites

* **A Tanzu Observability account** (If you don't have one already, you
  can [sign up for one](https://tanzu.vmware.com/observability)).
* **Install the Wavefront Proxy**: See [Install a Proxy](https://docs.wavefront.com/proxies_installing.html#install-a-proxy) for details.
  
  For example, use Docker to install the proxy. You have to specify:

  * The Tanzu Observability instance (for example, https://longboard.wavefront.com).
  * A Tanzu Observability API token that is linked to an account with **Proxy** permission.
    See [Generating and an API Token](https://docs.wavefront.com/wavefront_api.html#generating-an-api-token).

  ```
  docker run -d \
        -e WAVEFRONT_URL=https://{INSTANCE_NAME}.wavefront.com/api/ \
        -e WAVEFRONT_TOKEN={TOKEN} \
        -e JAVA_HEAP_USAGE=512m \
        -e WAVEFRONT_PROXY_ARGS="--customTracingListenerPorts 30001" \
        -p 2878:2878 \
        -p 30001:30001 \
        wavefronthq/proxy:latest
  ```

## Send Trace Data
If your application uses an OpenTelemetry SDK, you can configure the application to send trace data to Tanzu Observability:

* [Directly sending OpenTelemetry data to the Wavefront proxy](https://docs.wavefront.com/opentelemetry_tracing.html#send-data-using-the-wavefront-proxy---recommended) - [Recommended]
* Or [using the OpenTelemetry Collector](https://docs.wavefront.com/opentelemetry_tracing.html#send-data-using-the-opentelemetry-collector)

You can then use our tracing dashboards to visualize any request as a trace, which consists of a hierarchy of spans. This visualization helps you pinpoint where the request is spending most of its time and discover problems.

## Send Metrics data

If your application uses an OpenTelemetry SDK, you can configure the application to send metrics data to Tanzu Observability using the Tanzu Observability OpenTelemetry Collector. See [ADD LINK WHEN PUBLISHED]() for details.

## Tutorials
