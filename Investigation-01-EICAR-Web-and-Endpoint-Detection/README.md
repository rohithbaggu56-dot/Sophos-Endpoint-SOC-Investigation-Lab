# 🛡️ Investigation 01 — EICAR Web & Endpoint Detection

A controlled endpoint security investigation using the EICAR antivirus test file to examine how Sophos protects a Windows endpoint and how the resulting activity can be investigated through Sophos Central.

> ⚠️ **Lab Disclaimer**
> 
>This investigation was performed in an isolated lab environment using the harmless EICAR antivirus test file. No real malware was used.

---

## 🎯 Objective

The objective of this investigation was to understand how **Sophos Endpoint** protects a Windows endpoint and how Sophos Central supports the detection and investigation of a security event.

Using the harmless EICAR antivirus test file, the investigation explored Sophos **Web Protection, Endpoint Detection, Process Lineage, and Threat Graph** to understand how different security controls contribute to detection and investigation.

The goal was not simply to verify that Sophos could detect EICAR, but to understand **how the protection layers respond, what telemetry they provide, and how an analyst can investigate the resulting event in Sophos Central.**

---

## 🧪 Test Environment

- **Endpoint:** Windows 10
- **Security Platform:** Sophos Endpoint
- **Management:** Sophos Central
- **Test File:** EICAR antivirus test file
- **Test Source:** AMTSO EICAR test page
- **User Context:** Windows user account

---

## 🔎 Investigation

The investigation followed the activity through the security telemetry available in Sophos Central, starting with the initial web protection event and then examining the related endpoint detection and investigation context.

### 1. Initial Activity — Web Protection

The EICAR test file was accessed from the protected Windows endpoint.

Sophos Web Protection blocked access to the test content before it could be successfully accessed by the endpoint.

**Evidence observed:**
- Web Protection blocked the requested content
- The activity was identified as a restricted file type
- The event provided the initial indication that protection had been triggered

![Sophos Web Protection](Images/01-AMTSO-EICAR-Sophos-Web-Protection.png)
*Sophos Web Protection blocked access to the EICAR test content.*

### 2. Endpoint Detection

The same test activity generated an endpoint detection in Sophos Central.

The detection provided additional context around the activity, including the affected Windows endpoint, detection details, process information, and severity.

**Evidence observed:**
- Endpoint: Windows 10
- Process: `msedge.exe`
- Detection severity: Medium
- Detection details associated with the EICAR test activity

![Sophos Central EICAR Detection](Images/02-Sophos-Central-EICAR-Detection.png)
*Sophos Central generated an endpoint detection associated with the EICAR test activity.*

### 3. Process Lineage

I then reviewed Process Lineage to understand the process context surrounding the detection rather than stopping at the detection itself.

The lineage view provided additional context about the browser process and the activity associated with the detected event.

**Analyst purpose:**

The goal here was to determine how the detected activity originated and what process context was available for further investigation.

![Sophos EICAR Process Lineage](Images/03-Sophos-EICAR-Process-Lineage.png)
*Process Lineage provided additional context around the browser process associated with the detection.*

### 4. Threat Graph

The detection was also reviewed in Sophos Threat Graph to examine the activity in a broader investigation view.

Threat Graph provided additional context around the detected activity and exposed further information and available response options.

![Sophos EICAR Threat Graph](Images/04-Sophos-EICAR-Threat-Graph.png)
*Threat Graph provided a broader view of the detected activity and related investigation context.*

---

## 🧠 Analyst Assessment

The evidence showed a clear progression from the attempted web access to endpoint detection and additional investigation telemetry.

**Investigation chain:**

> EICAR test content access was attempted → Web Protection blocked the activity → Endpoint Detection generated → Process Lineage provided process context → Threat Graph provided broader investigation context

The activity was expected test behavior using the EICAR security test file in a controlled lab environment.

The investigation therefore focused on validating how Sophos detected, recorded, and exposed the activity for analyst investigation rather than treating the event as a real malware infection.

---

## 🛡️ Protection and Investigation Layers

| Layer | Evidence from the investigation | Analyst value |
|---|---|---|
| Web Protection | Access to the EICAR test content was blocked | Shows prevention at the web layer |
| Endpoint Detection | Sophos generated a detection for the activity | Provides an investigation starting point |
| Process Lineage | Process activity and browser context were available | Helps understand how the activity originated |
| Threat Graph | Related activity was presented in a broader investigation view | Provides additional context for analysis |
| Response | Available response options were exposed in the investigation workflow | Supports analyst decision-making |

---

## 💡 Key Takeaways

- A detection is the starting point of an investigation, not the end.
- Process context and related telemetry are important for understanding what actually happened.
- Multiple security layers can provide different pieces of evidence around the same activity.

---
## ✅ Conclusion

This investigation demonstrated how a single controlled test activity could be followed across multiple Sophos security layers:

**Web Protection → Endpoint Detection → Process Investigation → Threat Graph**

The main takeaway was that an endpoint investigation should not stop at the initial detection. The surrounding telemetry provides the context needed to understand what happened, how the activity originated, and what response options are available to the analyst.
