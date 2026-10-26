# ContentSphere Monitoring Requirements

## 1. Project Objective
Monitor infrastructure and application health, visualize metrics, configure alerts, centralize logs, and support incident investigation for the sample ContentSphere platform.

## 2. Components to Monitor
- Ubuntu Linux EC2 instances
- CPU, memory, filesystem and network usage
- Prometheus and Node Exporter services
- Grafana dashboards
- AWS EC2, EBS and CloudWatch metrics
- CloudWatch alarms and SNS notifications
- Application, web-server and operating-system logs
- Fluent Bit, Elasticsearch and Kibana
- Custom monitoring website and backend API

## 3. Infrastructure Metrics
- CPU utilization and system load
- Total and available memory
- Root filesystem utilization
- Network bytes received and transmitted
- Host, service and Prometheus target availability

## 4. Application Metrics
Where an application and suitable instrumentation are available, collect:
- HTTP request volume
- HTTP response status codes
- HTTP 5xx error rate
- Request latency
- Application availability

Application metrics must not be reported as available until collection is configured and verified.

## 5. AWS Metrics
Review CloudWatch EC2 CPUUtilization, NetworkIn, NetworkOut and status-check metrics. Review applicable EBS volume metrics. Standard EC2 metrics do not generally include operating-system memory and filesystem usage; configure CloudWatch Agent or use Prometheus and Node Exporter when needed.

## 6. Log Sources
Potential sources include the systemd journal, Ubuntu system and authentication logs, web-server access/error logs, application logs, and monitoring service logs. Confirm actual file paths and available sources during implementation.

## 7. Initial KPI Thresholds
- CPU warning above 70%; critical above 85%
- Memory warning above 75%; critical above 90%
- Root filesystem warning above 75%; critical above 90%
- Investigate intermittent scrape failures; escalate a sustained DOWN target
- Investigate increasing HTTP 5xx errors and sustained elevated error rates
- Investigate delayed log ingestion or missing expected events

These are illustrative laboratory thresholds. Tune them to the workload and normal baseline.

## 8. Stakeholders and Notifications
Stakeholders: DevOps/operations, application developers and platform administrators.

Prometheus and Grafana support metrics investigation. CloudWatch alarms can notify an SNS topic. Email subscribers must confirm their subscription. Kibana supports log investigation when log ingestion is operational.

## 9. Incident Investigation
1. Record the alert, affected resource and timestamp.
2. Inspect Prometheus and Grafana metrics.
3. Review relevant CloudWatch metrics and alarm history.
4. Search related logs when available.
5. Identify the likely cause from evidence.
6. Apply a safe corrective action.
7. Verify recovery and document the outcome.

## 10. Security and Cost
Restrict access to monitoring services. Avoid unnecessary public exposure of Elasticsearch and Kibana. Never commit credentials, tokens or private keys. Review AWS charges before creating resources. Configure appropriate access controls and log retention. Stop or remove unused lab resources.

## 11. Implementation Status
Requirements documented. Actual metric availability, application instrumentation and log paths must be verified during implementation. Monitoring deployment and end-to-end testing are pending.
