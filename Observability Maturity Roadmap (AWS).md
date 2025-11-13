

## Phase 1 — Foundation
- Goal: Establish core observability across infrastructure and applications.
- Technical Actions
     - ✅ Metrics
          - Enable Amazon CloudWatch metrics for EC2, RDS, EKS, ALB, etc.
          - Deploy Amazon Managed Prometheus (AMP).
          - Install Prometheus exporters:
          - Node exporter (EC2)
          - kube-state-metrics & cAdvisor (EKS)
          - AWS CloudWatch Exporter for AWS service metrics

     - ✅ Logs
          - Centralize logs with CloudWatch Logs.
          - Standardize log format (JSON preferred).
          - Enable VPC Flow Logs, ALB/ELB Logs, Lambda Logs.
     
     - ✅ Visualization
          - Deploy Amazon Managed Grafana (AMG).
          - Integrate Grafana → AMP + CloudWatch as data sources.
          - Create base dashboards (infra, app, network, database).

     - ✅ Alerting
          - Basic CloudWatch Alarms + SNS for CPU/memory thresholds.

     - Tool Choices
          - Metrics: CloudWatch, AMP
          - Logs: CloudWatch Logs
          - Visualization: Amazon Managed Grafana
          - Alerting: SNS, CloudWatch Alarms

     - Ownership Milestones
          - Platform Team owns data pipeline setup (exporters, Grafana)
          - Infra team owns CloudWatch metrics/alarms
          - App teams start pushing app metrics/logs
      
## Phase 2 — Centralization & Standardization (Quarter 2)
- Goal: Unify observability data and enforce standards across services. 
- Technical Actions
     - ✅ Central Data Pipeline
          - Implement FluentBit or FluentD → ship logs to OpenSearch or Loki.
          Integrate with Amazon Kinesis Firehose for scalability (optional).
     - ✅ Standardization
          - Define naming conventions for metrics (service, env, region).
          - Define standard labels and dashboards templates.
     - ✅ Tracing
          - Introduce AWS X-Ray or OpenTelemetry Collector for distributed tracing.
          - Instrument 2–3 core services for tracing.
     - ✅ Alerting
          - Integrate alert routing to PagerDuty / OpsGenie / Slack.
          - Begin defining SLO-based alerting (e.g., latency > p95 threshold). 
     - Tool Choices
          - Logs: CloudWatch → OpenSearch/Loki
          - Traces: AWS X-Ray or OpenTelemetry Collector
          - Alerts: PagerDuty / OpsGenie
          - Visualization: Grafana (standard dashboards)
     - Ownership Milestones
          - Platform team owns observability standards & CI/CD templates.
          - Application teams instrument traces.
          - SRE team starts tracking alert quality and noise.


