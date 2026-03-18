## Project Overview

This project builds upon a previous lab in which I designed and deployed my own Windows Active Directory (AD) environment. After establishing the domain infrastructure, the next objective was to implement centralized security monitoring using Splunk Enterprise.
To achieve this, I integrated my Domain Controller (DC-KING) and client workstation (KING-CLIENT) with a Splunk server running on Ubuntu. Using Splunk Universal Forwarder, both systems were configured to forward authentication activity and security telemetry to the SIEM platform.
The result is a centralized monitoring environment capable of capturing and analyzing authentication activity across the domain infrastructure. This setup simulates the type of security monitoring architecture used by enterprise Security Operations Centers (SOC) to detect suspicious login behavior and support security investigations.

## This project demonstrates my ability to:

- Build and deploy an Active Directory environment
- Integrate enterprise SIEM infrastructure
- Configure centralized log collection
- Enable authentication monitoring across domain systems

## Objective

The objective of this project was to extend my existing Active Directory lab by integrating it with Splunk Enterprise to support centralized security monitoring.

Specifically:

- Configured Splunk Universal Forwarder on both the Domain Controller and client workstation
- Forwarded authentication events and security logs to the Splunk server
- Centralized logs enable monitoring of login behavior, providing visibility for threat detection and cybersecurity operations

This demonstrates how enterprise organizations use SIEM platforms to monitor identity infrastructure and detect suspicious authentication activity.

## Lab Architecture
Component	Description
- SIEM Platform	Ubuntu 22.04 running Splunk Enterprise
- Domain Controller	Windows Server 2022 – DC-KING
- Client Workstation	Windows endpoint – KING-CLIENT
- Log Forwarding	Splunk Universal Forwarder
- Virtualization	Oracle VM VirtualBox

## Architecture Flow:

KING-CLIENT  ─┐
              ├──> Splunk Enterprise Server (Ubuntu)
DC-KING      ─┘

Both Windows systems forward security telemetry to the Splunk server for centralized analysis.

## Implementation Workflow
1. Installed Splunk Enterprise on Ubuntu
- Enabled Splunk Web interface
- Configured receiving port for log ingestion
- Created dedicated index for Windows security logs

This setup allows the Splunk server to receive telemetry from external systems.

2. Endpoint Integration with Splunk

- Installed Splunk Universal Forwarder on: DC-KING (Domain Controller) and KING-CLIENT (Windows endpoint)
- Forwarders transmit Windows security telemetry to the Splunk server
- Integration validated by checking active hosts in Splunk

3. Monitoring & Dashboard Panels

After integration, Windows systems forwarded authentication activity to Splunk. Using Splunk’s search and reporting capabilities, authentication events could be queried and visualized.

Example Queries:

- Failed Logins (4625): index=wineventlog EventCode=4625 | timechart span=5m count
- Successful Logins (4624): index=wineventlog EventCode=4624 | timechart span=5m count
- Top Targeted Users/ Account lockout (4625 & 4740): index=wineventlog EventCode IN (4625,4740) | head 10
- Privileged Logins (4672): index=wineventlog EventCode=4672 | head 10

## Skills Demonstrated

- Active Directory Administration
- Domain Controller deployment
- Domain environment configuration
- Windows endpoint integration
- SIEM Deployment
- Splunk Enterprise installation and configuration
- Log ingestion pipeline setup
- Index management and event monitoring
- Multi-host log aggregation
- Authentication activity monitoring
- Privileged account tracking

## Project Significance

This project demonstrates a complete identity infrastructure monitoring workflow, from deploying a Windows AD lab to integrating it with a SIEM platform for centralized monitoring.

Key outcomes:

- End-to-end enterprise SIEM deployment experience
- SOC-style dashboards for authentication monitoring
- Ability to detect suspicious login behavior and analyze targeted accounts

Practical experience with Blue Team workflows in a lab environment
