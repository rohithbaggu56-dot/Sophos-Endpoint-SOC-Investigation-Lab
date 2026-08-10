# 🛡️ Investigation 02 — PUA Detection & Investigation

A controlled endpoint security investigation using the AMTSO Potentially Unwanted Application (PUA) test to understand how **Sophos Endpoint** identifies and responds to potentially unwanted software activity on a Windows endpoint.

> ⚠️ **Lab Disclaimer**
>
> This investigation was performed in an isolated lab environment using the harmless AMTSO PUA test file. The test file is not actually malicious and was specifically designed to safely validate security product PUA detection capabilities.

---

## 🎯 Objective

The objective of this investigation was to understand how **Sophos Endpoint** handles Potentially Unwanted Applications (PUAs) and how the resulting security activity can be investigated through **Sophos Central**.

The investigation focused on Sophos **Web Protection, PUA detection, process lineage, and endpoint telemetry** to understand how Sophos identifies potentially unwanted content and provides investigation context to a security analyst.

The goal was not simply to confirm that Sophos could detect a PUA test, but to understand **how the protection controls respond and what information is available for investigating the event**.

---

## 🧪 Test Environment

- **Endpoint:** Windows 10
- **Security Platform:** Sophos Endpoint
- **Management Platform:** Sophos Central
- **Test Standard:** AMTSO PUA Test
- **Test Type:** Potentially Unwanted Application
- **User Context:** Standard Windows user
- **Environment:** Isolated home lab

---

## 🔎 Investigation

### 1. AMTSO PUA Test

The AMTSO Potentially Unwanted Application test page was accessed from the protected Windows endpoint.

The test is designed to safely verify whether endpoint security software is configured to detect potentially unwanted applications.

Sophos Endpoint generated security notifications when the PUA test was accessed/downloaded.

![AMTSO PUA Test](Images/01-AMTSO-PUA-Sophos-Web-Protection.png)

---

### 2. Sophos Web Protection

Sophos Web Protection blocked access to the PUA test content.

The browser displayed an **Access denied** page indicating that the organization had blocked the requested site under its configured threat protection policy.

![Sophos Web Protection Blocking PUA](Images/02-Sophos-Web-Protection-PUA-Blocked.png)

This demonstrated that protection can occur at the web access stage, before the test content is successfully delivered to the endpoint.

---

### 3. Sophos Central Detection

Sophos Central recorded the activity as an endpoint threat detection.

**Detection observed:**

- **Detection:** `WIN-PROT-WEB-MALWARE-APP-EICAR-PUA`
- **Severity:** Medium
- **Process:** `msedge.exe`
- **Endpoint:** Windows 10

The detection provided additional endpoint context, including the process responsible for accessing the test content.

![Sophos Central PUA Detection](Images/03-Sophos-Central-PUA-Detection.png)

---

### 📊 Threat Graph Availability

Not every Sophos detection generates a Threat Graph.

During this investigation, the PUA detection was recorded in Sophos Central, but a Threat Graph was not generated for the event.

This is expected behavior in some PUA detection scenarios. Sophos documentation specifically notes that **Deep Learning (ML) PUA detections do not create Threat Graphs**. Threat Graphs are primarily used when Sophos identifies malware that requires further investigation.

This was an important part of the investigation because it showed that a **detection event and a Threat Graph are not the same thing**. A detection can still provide useful endpoint information even when a full threat graph is unavailable.

> **Investigation note:** Threat Graph availability depends on the type and severity of the detection and the telemetry available for the event.

---

### 4. Detection Lineage

The detection's Lineage view was reviewed to understand the process and file activity associated with the PUA event.

The lineage showed `msedge.exe` accessing the AMTSO test content and provided additional context around the activity that triggered the detection.

![Sophos PUA Process Lineage](Images/04-Sophos-PUA-Process-Lineage.png)

---

## 🛡️ Security Controls Demonstrated

| Control | What was observed |
|---|---|
| **Web Protection** | Blocked access to the PUA test content |
| **PUA Detection** | Sophos generated a PUA-related endpoint detection |
| **Endpoint Telemetry** | Captured the browser process and related activity |
| **Process Lineage** | Provided context around the activity that triggered the detection |
| **Sophos Central** | Centralized the detection and investigation information |

---

## 💡 Key Takeaways

- Sophos can identify **Potentially Unwanted Applications** separately from conventional malware detections.
- Web Protection can prevent access to potentially unwanted or suspicious content before it is successfully delivered.
- Sophos Central provides endpoint telemetry that helps an analyst investigate the detection.
- Process lineage adds useful context around the activity associated with a security event.
- The investigation showed how multiple protection and visibility capabilities can work together instead of relying on a single detection mechanism.

---

## 🧠 Conclusion

This investigation demonstrated how Sophos approaches **PUA protection and endpoint investigation**.

The workflow observed during the test was:

**Web Protection → PUA Detection → Endpoint Telemetry → Process Lineage → Investigation**

Rather than simply confirming that a test file was detected, the investigation helped demonstrate how Sophos protects the endpoint and provides an analyst with additional context for understanding the event.
