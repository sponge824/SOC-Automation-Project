# SOC Automation Project

## Objective

This Lab aimed to design and build an automated workflow similar to a Next-Gen Security Operation Centre (SOC). It leverages a SIEM, an automation platform, and AI to handle the initial investigation of a security alert automatically. The system triages, enriches with threat intelligence, summarises, and reports on alerts, which reduces the workload for L1 analysts.

### Skills Learned

- **Security Orchestration, Automation, and Response (SOAR)**: Designing and implementing an end-to-end automation pipeline to connect different security tools.
- **SIEM Implementation & Management**: Deploying, configuring, and managing Splunk for log ingestion, searching, and alerting.
- **API Integration**: Connecting Gemini, AbuseIPDB, and Slack through their APIs to automate the workflow. 
- **Threat Intelligence**: Used AbuseIPDB to enrich the IOC.
- **VM**: Building and managing multi-VM environments using VMware, such as Windows and Ubuntu.
- **Docker**: Deploying and managing application (N8N) using Docker.

### Tools Used
- **Splunk**: SIEM Platform
- **N8N**: Core automation and workflow engine
- **Gemini**: AI analysis and reporting
- **AbuseIPDB**: IP Address threat intelligence enrichment
- **VMWare**: Lab Environment
- **Docker**: Deployment of N8N
- **Slack**: Automated Alert Notifications
- **OS**: Windows 10 (Log Source) & Ubuntu Server (Splunk, N8N)




## Steps


**Ref 1: Architecture Diagram**

![Architecture Diagram (SOC-Project)](https://github.com/user-attachments/assets/0dd6af91-b1ad-4121-b83d-d45de7a96432)  

This diagram shows the automation workflow for the project. Logs from the Windows 10 VM are sent with Splunk Universal Forwarder to Splunk. Splunk generates an alert that triggers a webhook in N8N. N8N then coordinates API calls to Gemini and AbuseIPDB for analysis and enrichment before sending a report to Slack.

**Ref 2: Log Ingestion in Splunk**
<img width="1913" height="907" alt="image" src="https://github.com/user-attachments/assets/a602e648-9967-4e2b-9589-d1abf55efb22" />

This screenshot shows that the Splunk Universal Forwarder on the Windows 10 VM is successfully sending security event logs to the Splunk indexer.

**Ref3: Brute-Force Alert in Splunk**
<img width="1212" height="296" alt="image" src="https://github.com/user-attachments/assets/584bf381-f0f2-441f-8b84-0e26bfba2a82" />

This is the Splunk alert that is configured to detect brute force. It uses Search Processing Language (SPL) query to detect failed login attempts (EventCode=4625). The configured action is to trigger the N8N webhook.
