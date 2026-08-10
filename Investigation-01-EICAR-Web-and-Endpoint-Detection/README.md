# 🛡️ Investigation 01 — EICAR Web & Endpoint Detection

A controlled endpoint security investigation using the **EICAR antivirus test file** to examine how Sophos protects a Windows endpoint and provides investigation visibility through Sophos Central.

> ⚠️ EICAR is a harmless industry-standard antivirus test file used to validate security products. It is not real malware.


## 🎯 Objective

The objective of this investigation was to understand how **Sophos Endpoint** protects a Windows endpoint against a controlled malware test and how the resulting security event can be investigated through **Sophos Central**.

The investigation focused on understanding Sophos **Web Protection, endpoint detection, process lineage, and Threat Graph analysis** by using the harmless EICAR test file.

The test was not simply to confirm that Sophos could detect EICAR, but to understand the **security controls involved, the telemetry they generate, and how an analyst can investigate the resulting event**.

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

### 1. Web Protection

The EICAR test file was accessed from the protected Windows endpoint.

Sophos Web Protection blocked access to the file and displayed:

> **Access denied — Restricted file type**

The event demonstrated that Sophos can prevent potentially dangerous file types from being accessed through the web before they are successfully downloaded to the endpoint.

![Sophos Web Protection](Images/01-AMTSO-EICAR-Sophos-Web-Protection.png)

---

### 2. Sophos Central Detection

Sophos Central recorded the activity as an endpoint threat detection.

**Detection observed:**

- **Detection:** `WIN-PROT-WEB-MALWARE-EICAR-AV-TEST`
- **Severity:** Medium
- **Process:** `msedge.exe`
- **Endpoint:** Windows 10

![Sophos Central EICAR Detection](Images/02-Sophos-Central-EICAR-Detection.png)

---

### 3. Process Lineage

The detection was investigated through Sophos process lineage to understand the activity surrounding the event.

The lineage showed the browser activity and the associated EICAR file activity, providing additional context about how the detection occurred.

![Sophos EICAR Process Lineage](Images/03-Sophos-EICAR-Process-Lineage.png)

---

### 4. Threat Graph

The detection was opened in Sophos Threat Graph to investigate the event in greater detail.

The graph identified the EICAR test file with a **bad reputation / likely malware** classification and provided additional file information and response options.

![Sophos EICAR Threat Graph](Images/04-Sophos-EICAR-Threat-Graph.png)

---

## 🛡️ Security Controls Demonstrated

| Control | What was observed |
|---|---|
| Web Protection | Blocked access to the restricted EICAR file |
| Endpoint Detection | Generated a detection in Sophos Central |
| Process Lineage | Provided context around the browser and file activity |
| Threat Graph | Connected the detection with additional file and process context |
| Threat Response | Sophos provided response options for the detected threat |

---

## 💡 Key Takeaways

- Sophos can provide protection at multiple stages of a web-based file event.
- Web Protection can prevent access to restricted or potentially dangerous content.
- Sophos Central provides centralized visibility into endpoint detections.
- Process lineage helps investigate how an event originated.
- Threat Graph provides additional context for understanding and investigating a detection.
- The investigation showed how prevention and endpoint telemetry can work together rather than relying on a single security control.

---

## ✅ Conclusion

The EICAR test demonstrated a layered endpoint protection workflow:

**Web Protection → Endpoint Detection → Process Investigation → Threat Graph Analysis**

The test provided a practical view of how a security event can be detected and investigated through Sophos Central rather than simply confirming that an antivirus product can detect a test file.

---

### 🔐 Lab Disclaimer

This investigation was performed in an isolated lab environment using the harmless EICAR antivirus test file. No real malware was used.
