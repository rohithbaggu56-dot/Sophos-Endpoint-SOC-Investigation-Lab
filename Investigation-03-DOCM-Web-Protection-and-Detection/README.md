# 🛡️ Investigation 03 — DOCM Web Protection & Detection

A controlled endpoint security investigation using a DOCM security test file to understand how Sophos Web Protection and Sophos Endpoint respond to potentially malicious web-based content and how the resulting activity appears within Sophos Central.

> ⚠️ **Lab Disclaimer**
>
> This investigation was performed in an isolated lab environment using a security test file from the Cyber Essentials test-file repository. The file was used only to safely validate Sophos protection and detection behavior and was not treated as real-world malware.

---

## 🎯 Objective

The objective of this investigation was to understand how Sophos handles a DOCM test file accessed through a web-based source and how the resulting activity is detected and investigated through Sophos Central.

The investigation focused on:

- Sophos Web Protection
- Endpoint detection and telemetry
- Process Lineage
- Detection and investigation context
- Remediation of the detected activity

The goal was not simply to confirm that Sophos blocked or detected the test file, but to understand how the available security controls contributed to the investigation and what evidence was available to an analyst.

---

## 🧪 Test Environment

- **Endpoint:** Windows 10
- **Security Platform:** Sophos Endpoint
- **Management Platform:** Sophos Central
- **Test File:** `CEPlus.docm`
- **Test Source:** Cyber Essentials Test Files
- **Environment:** Isolated home lab

---

## 🔎 Investigation

### 1. DOCM Test File

The `CEPlus.docm` test file was accessed from the Cyber Essentials security testing repository.

The test was performed to observe how Sophos handled the file during a web-based access attempt and what security telemetry was generated on the endpoint.

![DOCM Test File Source](Images/01-test-file-source.png)
*The screenshot shows the test file being accessed from the security testing repository, providing the starting point for the investigation.*

---

### 2. Sophos Web Protection

Sophos Web Protection blocked access to the DOCM test content during the web-based access attempt.
The browser displayed an access-denied response, while Sophos Endpoint also reported the detected activity and subsequent cleanup.

![Sophos Web Protection Block and Threat Cleanup](Images/02-web-protection-block-and-cleanup.png)
*The evidence confirmed that protection occurred at the web-access stage before the test content could be successfully delivered.*

---

### 3. Sophos Central Detection


Sophos Central recorded the activity as an endpoint threat detection.

The detection provided additional endpoint context, including:

- **Detection:** `WIN-PROT-WEB-MALWARE-TROJ-POWERSH-G`
- **Severity:** Medium
- **Process:** `msedge.exe`
- **Endpoint:** Windows 10

The detection details also provided information such as the process path, process command line, parent process information, SHA-256, and the source file path.

![Sophos Central Detection](Images/03-sophos-detection.png)
*The detection provided the investigation starting point and additional endpoint telemetry for understanding the activity.*

---

### 📊 Threat Graph Availability

A Threat Graph was not generated for this DOCM-related detection.

Sophos still provided useful investigation data through the detection details and Process Lineage, allowing the associated process activity to be reviewed.

This showed that Threat Graph availability can vary between detections and that the absence of a Threat Graph does not mean that useful investigation telemetry is unavailable.

> 🔎 **Investigation note:** In this case, Process Lineage provided additional investigation context even though a Threat Graph was not available.

---

### 4. Detection Lineage

The detection's Process Lineage view was reviewed to understand the process activity associated with the event.
The Process Lineage showed the sequence of processes associated with the detected activity and provided additional context beyond the initial detection.

![Sophos Detection Process Lineage](Images/04-Process-lineage.png)
*The lineage was useful for moving beyond the detection itself and examining the process context associated with the event.*


---

## 🧠 Analyst Assessment

The evidence showed a clear progression from the attempted access to the DOCM test content through web protection, endpoint detection, process telemetry, and remediation.

**Investigation context:**

DOCM test activity → Web Protection blocked access → Endpoint Detection generated → Process Lineage provided process context → Remediation completed

The activity was expected test activity performed in a controlled lab environment. The investigation therefore focused on validating how Sophos identified the activity, what evidence was available to an analyst, and how the endpoint responded.

The detection provided additional context such as the affected endpoint, process information, process path, command-line information, and file-related details. Process Lineage then helped connect the detection to the process activity associated with the event.

A Threat Graph was not available for this detection. However, the available detection details and Process Lineage still provided useful investigation context.

---

## 🛡️ Security Controls Demonstrated

| Control | What was observed |
|---|---|
| Web Protection | Blocked access to the DOCM test content |
| Endpoint Detection | Generated a detection for the related activity |
| Endpoint Telemetry | Captured process and related activity associated with the detection |
| Process Lineage | Provided additional context around the detected activity |
| Sophos Central | Centralized detection and investigation information |
| Remediation | Sophos cleaned up the detected test activity |

---

## 💡 Key Takeaways

- Web Protection can prevent access to suspicious or security-testing content before it is successfully delivered.
- Endpoint detection and telemetry provide additional context around activity observed on the endpoint.
- Process Lineage can help an analyst understand the process activity associated with a detection.
- Investigation visibility can vary between detections; in this case, Process Lineage was available while a Threat Graph was not.
  
---

## ✅ Conclusion

This investigation demonstrated how Sophos handled a controlled DOCM-based security test across multiple protection and investigation layers.

The workflow observed during the investigation was:

**Web Protection → Endpoint Detection → Endpoint Telemetry → Process Lineage → Remediation**

The investigation showed that the initial web protection event could be followed by endpoint detection and additional process context in Sophos Central. It also reinforced that investigation visibility can vary between detections. In this case, Process Lineage was available even though a Threat Graph was not.
Overall, the test helped demonstrate how Sophos connects prevention, detection, investigation context, and response within a centralized workflow.
