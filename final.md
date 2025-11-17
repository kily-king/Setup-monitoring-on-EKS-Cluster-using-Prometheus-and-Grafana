Observability, Security Operations & FinOps Maturity Plan 

 

Where Do We Derive Metrics From?  

• AWS CloudWatch  

• Prometheus  

• Grafana  

• Splunk  

• OpenSearch/Kibana  

• EC2 heavy forwarder logs  

• EventBridge 

⸻ 

What Is Our Proposal Going Forward? 

Implement a unified, automated observability platform using AWS native + OpenTelemetry covering MELT (Metrics, Events, Logs, Traces) 

⸻ 

What Does “Maturing Security Operations” Mean?  

• Enable Security Hub  

• Shift to proactive detection  

• Automate remediation  

• Central visibility dashboards  

• Strengthen IAM governance  

• Integrate GuardDuty, Inspector, CloudTrail Lake 

⸻ 

How Will We Mature FinOps?  

• Use AWS-native FinOps tools  

• Tagging standards  

• Cost optimization workflows 

• Automated anomaly detection 

• Monthly chargeback/showback  

• Rightsizing insights  

• Forecasting & governance 

 

Current State Assessment + Proposed Roadmap 

⸻ 

Summary 

Our platform currently uses AWS-native services and open-source tools for logs, metrics, and events. While several foundational monitoring components exist (CloudWatch, Prometheus, Grafana, Splunk, EKS metrics, EC2/EBS metrics), the platform requires standardization, automation, and visibility improvements to achieve full Observability, Security Maturity, and FinOps Optimization. 

This document outlines:  

• What we monitor today (current state)  

• Where the data sources come from  

• Gaps and limitations  

• Proposal for future observability platform offering  

• Plan for maturing security operations  

• FinOps platform maturity plan 

⸻ 

Current Monitoring & Observability State 

Below is a consolidated view of everything monitored today and the tools/data sources used. 

⸻ 

2.1 Data Sources (Where monitoring data is coming from?) 

Category Tools / Sources Metrics CloudWatch, Prometheus Logs CloudWatch Logs, Splunk via Heavy Forwarder Distributed Traces AWS X-Ray (limited usage) Events EventBridge Search / Query OpenSearch, Kibana Dashboards Grafana, CloudWatch Dashboards Scripts / Custom Internal custom scripts (limited) 

⸻ 

2.2 Current Metrics Coverage 

EC2 Metrics (AWS CloudWatch)  

• CPU Utilization • Network In/Out  

• Disk IOPS (Read/Write)  

• Disk Throughput (Bytes/sec)  

• Status Checks 

⸻ 

CloudWatch Metrics  

• Incoming log events  

• Incoming bytes  

• Forwarded log events/bytes  

• Delivery errors  

• Throttling indicators 

⸻ 

Prometheus / Grafana  

• Scrape duration  

• Prometheus and Grafana internal metrics 

⸻ 

EBS Metrics  

• Volume read/write ops  

• Queue length  

• Idle time 

⸻ 

Lambda 

❌ No metrics configured (Currently a major observability gap) 

⸻ 

CloudWatch Logs  

• Incoming Bytes  

• Log Events  

• Forwarded log events  

• Error counts (But not parsed into structured logs) 

⸻ 

RDS 

❌ Gaps in both cluster & instance-level observability except a few high-level metrics: 

Cluster Metrics:  

• CPU Utilization  

• DB Connections  

• Available RAM 

 

Instance Metrics:  

• CPU  

• Storage Space  

• RAM  

• Read/Write Ops  

• Latency  

• Throughput 

 

Full slow query analysis and enhanced monitoring not enabled 

⸻ 

EKS Monitoring 

CoreDNS  

• Health  

• DNS requests  

• Return codes  

• Cache hits/misses  

• Request latency  

• Packet size  

• Forward request errors 

 

EKS Pods by Node  

• CPU  

• Memory  

• Networking (partial) 

⸻ 

Istio / Service Mesh 

❌ No ztunnel metrics  

❌ No service dependency map  

❌ No request/response telemetry 

⸻ 

Application Layer (ABP Apps)  

• ABP Error metrics  

• Custom duration metrics  

• Some logs through Splunk  

• HTTP Requests (from NY Prod EKS) 

⸻ 

Kafka Monitoring  

• BytesInPerSec  

• BytesOutPerSec  

• ABP errors / CPA errors  

• Application errors 

⸻ 

Splunk Monitoring (Heavy Forwarder)  

• Forwarder health  

• Logs & metrics  

• Error/warn metrics  

• Network, IO, CPU usage  

• ASG scaling events  

• Backup success/error to S3 

⸻ 

Current Gaps & Challenges 

3.1 Observability Gaps  

• No unified observability platform or single-pane-of-glass  

• Lambda, RDS, Istio, X-Ray, and CloudTrail are underutilized  

• No distributed tracing across microservices • Heavy dependency on manual dashboards  

• No standardized metrics, logs, traces (MELT model not fully implemented)  

• No auto-instrumentation setup  

• No SLOs, Error Budgets, or Burn-rate alerts implemented 

⸻ 

3.2 Security Operations Gaps  

• No centralized AWS Security Hub integration  

• CloudTrail events not fully monitored or correlated  

• No GuardDuty → SIEM automated workflow  

• No baseline security KPIs (IAM usage, root usage, MFA compliance, etc.)  

• No automated threat response using EventBridge & Lambda  

• Manual log analysis  

• No security posture scoring 

⸻ 

3.3 FinOps Gaps  

• No unified cost visibility across accounts  

• No cost anomaly detection configured  

• No tagging standards  

• No automated reports per BU / application  

• No rightsizing insights used (Compute Optimizer not aligned with teams)  

• No chargeback/showback model  

• No automated forecasting 

⸻ 

Proposed Future State — Observability Platform Maturity 

Below is what we propose as the default observability platform offering. 

⸻ 

4.1 Unified Observability Platform (AWS-native + Open-source Hybrid) 

Core Components 

MELT Pillar Proposed Service Metrics CloudWatch, Prometheus, AMP (Amazon Managed Prometheus) Events EventBridge, CloudTrail, AWS Health Logs CloudWatch Logs, OpenSearch, Splunk Traces AWS X-Ray, OpenTelemetry collector 

⸻ 

4.2 Move to OpenTelemetry (OTEL) Standardization  

• Auto instrumentation for all microservices  

• Collect:  

• Metrics  

• Logs  

• Traces  

• Export to: CloudWatch, Prometheus, OpenSearch, Grafana 

⸻ 

4.3 Default Platform Offering to Customers  

1. Application Logging Framework  

2. Distributed Tracing via OTEL/X-Ray  

3. Metrics collection: Infrastructure + Application  

4. Dashboards (provisioned automatically)  

5. Central Alerting & Event Routing  

6. SLOs, Error Budgets & Burn-rate Alerts  

7. Cost visibility dashboards 8. Security visibility dashboards (GuardDuty, Shield, IAM activity) 

⸻ 

4.4 Dashboards Packages (Base Offering) 

Infra Dashboards  

• EC2 performance  

• EKS cluster health  

• RDS performance  

• Kafka cluster health  

• Splunk forwarder health 

 

Application Dashboards  

• Request latency & throughput  

• Error rate  

• SLA/SLO compliance  

• Top slow endpoints 

Security Dashboards  

• IAM risky activity  

• GuardDuty findings  

• Vulnerability status (if integrated with Inspector) 

FinOps Dashboards  

• Cost per microservice  

• Cost per environment  

• Monthly forecast  

• Unused resources 

⸻ 

Security Operations Maturity Plan 

What does “maturing security operations” mean? 

It means moving from reactive → proactive security by automating:  

• Threat detection  

• Threat correlation  

• Automated remediation  

• Security scoring  

• Continuous compliance 

⸻ 

5.1 Current Gaps  

• No Security Hub integration  

• No automated remediation  

• No unified security dashboard  

• No real-time alert correlation  

• No attack surface monitoring 

⸻ 

5.2 Proposed Fixes 

Enable AWS Security Hub  

• Centralize GuardDuty, Inspector, IAM Access Analyzer  

• Unified findings dashboard 

 

Enable AWS GuardDuty (Full features)  

• EKS runtime security  

• Malware detection  

• IAM anomaly detection 

Enable AWS CloudTrail Lake 

To analyze:  

• Account activity  

• User behavior  

• API anomalies 

Setup Automated Incident Response 

Using:  

• EventBridge  

• Lambda  

• Systems Manager 

Examples:  

• Disable suspicious IAM user automatically  

• Auto-stop compromised EC2  

• Block malicious IP in WAF 

Security KPIs  

• MFA compliance  

• Unused IAM roles  

• Root user usage  

• Public S3 buckets  

• GuardDuty findings per severity 

⸻ 

FinOps Platform Maturity Plan 

 

6.1 Which Tools? 

We will leverage AWS native tools: 

Category Tool Cost Monitoring AWS Cost Explorer Optimization AWS Compute Optimizer Forecasting AWS Cost Forecast Anomaly Detection AWS Cost Anomaly Detection Tagging AWS Resource Explorer + Tag Policies Reporting QuickSight dashboards 

⸻ 

6.2 What We Will Monitor  

• Monthly AWS spend  

• Service-wise cost (EC2, EKS, RDS, S3, Lambda, etc.)  

• Environment-wise cost (Prod/Dev/UAT)  

• Application-wise cost  

• Unused resources  

• Rightsizing recommendations  

• Reserved Instance / Savings Plan coverage  

• Storage lifecycle optimization  

• Data transfer cost 

⸻ 

6.3 Maturity Roadmap 

Phase 1 — Visibility  

• Cost Explorer + tagging  

• Cost dashboards (QuickSight) 

 

Phase 2 — Optimization  

• Rightsizing (EC2/EKS/RDS)  

• Storage lifecycle automation  

• Cost anomaly alerts 

Phase 3 — Governance  

• Monthly chargeback  

• Budget guardrails  

• Spend forecast for each BU 

⸻ 

Final Summary to Present to Management 

What Metrics Do We Monitor Today? 

✔ EC2  

✔ EBS  

✔ Some RDS  

✔ CoreDNS & EKS  

✔ Kafka  

✔ ABP application metrics  

✔ Splunk logs & forwarder metrics  

❌ Gaps in Lambda, Istio, distributed traces, structured logs, and RDS deep metrics 

⸻ 

 
