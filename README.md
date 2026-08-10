# 🛡️ Sophos Endpoint SOC Investigation Lab

![Sophos](https://img.shields.io/badge/Sophos-Endpoint-0A5CA8?style=for-the-badge&logo=sophos&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-Endpoint-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Lab-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![SOC](https://img.shields.io/badge/SOC-Investigation-111827?style=for-the-badge)
![Threat Analysis](https://img.shields.io/badge/Threat-Analysis-7C3AED?style=for-the-badge)

# 🛡️ Sophos Endpoint SOC Investigation Lab

A practical security investigation lab focused on understanding how **Sophos Endpoint and Sophos Central** detect, investigate, and respond to suspicious activity on Windows endpoints.

This project was built to go beyond simply generating detections. The goal was to understand how Sophos connects **endpoint protection, identity context, detection telemetry, investigation, and response** within a centralized security platform.

---

## 🎯 Lab Objective

The objective of this lab was to understand the Sophos security workflow from an analyst's perspective.

Rather than treating Sophos as only an endpoint antivirus product, I explored how its different security capabilities work together during an investigation.

The lab focused on:

- 🔍 Endpoint threat detection
- 🌐 Web protection
- 🧪 Controlled security testing
- 👥 Active Directory identity context
- 📊 Detection investigation
- 🌳 Process Lineage
- 🚨 Alerts and attack-level visibility
- 🧹 Threat remediation
- ☁️ Centralized investigation through Sophos Central

---

## 🏗️ Lab Architecture

![Sophos Endpoint SOC Lab Architecture](Images/sophos-lab-architecture.png)

---

## 🧪 Investigation Approach

The lab used controlled security test files and scenarios on a Windows 10 endpoint protected by Sophos Endpoint.

The activity was then investigated through Sophos Central to understand what was detected, what telemetry was available, how the endpoint activity could be traced, and how Sophos responded to the activity.

The investigations are documented separately in the repositories below.
