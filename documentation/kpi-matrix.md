# ContentSphere KPI Matrix

| KPI | Collection Method | Warning | Critical | Notes |
|---|---|---|---|---|
| CPU utilization | Node Exporter / CloudWatch | >70% | >85% | Tune to workload |
| Memory utilization | Node Exporter / CloudWatch Agent | >75% | >90% | Requires suitable OS metric collection |
| Root filesystem utilization | Node Exporter / CloudWatch Agent | >75% | >90% | Requires filesystem metric collection |
| Network traffic | Node Exporter / CloudWatch | Unusual deviation | Sustained abnormal traffic | Establish a baseline |
| EC2 status checks | CloudWatch | Investigate failure | Sustained failure | AWS-managed metric |
| Prometheus target | Prometheus up metric | Intermittent failures | Sustained DOWN | Check connectivity and service status |
| HTTP 5xx errors | Application instrumentation / logs | Increasing rate | Sustained elevated rate | Requires application data |
| Request latency | Application instrumentation | Above baseline | Sustained objective breach | Requires latency measurements |
| Log ingestion | Fluent Bit and Elasticsearch | Delayed events | Expected events absent | Requires a known test event or baseline |
| Service availability | Health checks / service monitoring | Intermittent failure | Sustained outage | Define checks for deployed services |

## Threshold Guidance

These are initial laboratory thresholds, not universal production limits.
Tune them according to normal workload and service objectives.

A missing metric must be documented as unavailable until the required
collector, exporter, agent or application instrumentation is configured.

## Alert Response

1. Confirm the alert and incident timestamp.
2. Inspect the relevant metrics and service health.
3. Search related logs where available.
4. Apply a safe corrective action.
5. Verify recovery and document the result.
