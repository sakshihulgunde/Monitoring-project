# ContentSphere - Monitoring and Observability

## Overview
A DevOps project for monitoring Linux server resources using Prometheus, Node Exporter, and Grafana on an existing Ubuntu EC2 instance.

## Technology Stack
- Ubuntu Linux
- AWS EC2
- Prometheus
- Node Exporter
- Grafana
- Git and GitHub

## Architecture
Ubuntu EC2 -> Node Exporter -> Prometheus -> Grafana

## Verification
Prometheus readiness:
http://127.0.0.1:9090/-/ready

Node Exporter metrics:
http://127.0.0.1:9100/metrics

## Example PromQL Queries

CPU usage percentage:
100 * (1 - avg(rate(node_cpu_seconds_total{mode="idle"}[5m])))

Memory usage percentage:
100 * (1 - node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes)

Node Exporter health:
up{job="node_exporter"}

## Security
- Never commit AWS credentials, passwords, private keys, or tokens.
- Restrict Grafana access to trusted IP addresses.
- Do not expose Prometheus port 9090 or Node Exporter port 9100 publicly.
- Review AWS costs before enabling additional services.

## Implementation Status
Prometheus and Node Exporter have been verified on the existing host. Grafana was installed and a dashboard was saved. Confirm that dashboard panels display live data before claiming all panels are fully validated.

CloudWatch, SNS, centralized logging, and the custom web interface require separate implementation and verification.

## Documentation
See the documentation directory for architecture, component inventory, KPI matrix, and monitoring requirements.
