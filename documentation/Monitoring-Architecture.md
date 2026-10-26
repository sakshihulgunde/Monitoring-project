# ContentSphere Monitoring Architecture

```mermaid
flowchart TD
    APP["ContentSphere Application / Ubuntu EC2"]

    NE["Node Exporter"]
    PROM["Prometheus"]
    GRAF["Grafana Dashboards"]

    AWS["AWS EC2 and EBS"]
    CW["CloudWatch Metrics"]
    ALARM["CloudWatch Dashboard and Alarms"]
    SNS["Amazon SNS Notifications"]

    LOG["Application and System Logs"]
    FB["Fluent Bit"]
    ES["Elasticsearch"]
    KIB["Kibana Dashboards"]

    WEB["React + TypeScript Frontend"]
    API["Node.js + Express Backend API"]

    APP --> NE
    NE --> PROM
    PROM --> GRAF

    AWS --> CW
    CW --> ALARM
    ALARM --> SNS

    APP --> LOG
    LOG --> FB
    FB --> ES
    ES --> KIB

    WEB --> API
    API --> PROM
    API --> CW
    API --> ES

    GRAF --> IR["Incident Investigation"]
    ALARM --> IR
    KIB --> IR
    IR --> FIX["Corrective Action"]
    FIX --> VERIFY["Verify Recovery"]
```

## Component Responsibilities
- Node Exporter exposes Linux host metrics.
- Prometheus scrapes and stores time-series metrics.
- Grafana queries Prometheus and displays dashboards.
- CloudWatch collects supported AWS metrics and evaluates alarms.
- SNS delivers configured notifications.
- Fluent Bit collects and forwards logs to Elasticsearch.
- Kibana searches and visualizes indexed logs.
- The custom website retrieves data through a controlled backend API.

## Security
Restrict service access to authorized networks, use suitable authentication and encryption, apply least-privilege AWS permissions, and keep secrets out of source control.
