

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
      

 
- 
