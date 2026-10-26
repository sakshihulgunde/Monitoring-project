# ContentSphere Component Inventory

| Component | Purpose | Input | Output | Status |
|---|---|---|---|---|
| Ubuntu EC2 | Hosts monitoring services or application | OS and network resources | Host metrics and logs | Existing instance verified |
| Node Exporter | Exposes Linux host metrics | Linux kernel/system statistics | Metrics endpoint, normally port 9100 | Pending |
| Prometheus | Scrapes and stores time-series metrics | Exporter endpoints | PromQL queries and target status | Pending |
| Grafana | Visualizes metrics | Prometheus data source | Dashboards and panels | Pending |
| Amazon CloudWatch | Collects AWS resource metrics | EC2/EBS and configured agents | Metrics, dashboards and alarms | To inspect |
| CloudWatch Agent | Collects selected OS metrics and logs | Host telemetry | CloudWatch metrics/logs | Optional; needs assessment |
| Amazon SNS | Delivers configured notifications | Alarm actions/messages | Email or other subscriptions | Pending cost review |
| Fluent Bit | Collects and forwards logs | Configured log sources | Structured log events | Pending |
| Elasticsearch | Indexes and searches logs | Forwarded log events | Searchable documents | Pending; resource assessment required |
| Kibana | Searches and visualizes logs | Elasticsearch data | Discover views and dashboards | Pending |
| React + TypeScript | Custom monitoring interface | Backend API responses | User interface and charts | Pending |
| Node.js + Express | Backend API | Authorized client requests | Validated metrics and log responses | Pending |

## Important Notes

- Only mark a component operational after testing it.
- Record the installed version and endpoint during implementation.
- Never store credentials in this inventory.
- Protect service endpoints with appropriate network controls and authentication.
