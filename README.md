# 🛡️ Threat Detection Engineering & Simulation Using the Pyramid of Pain

**Platform**: TryHackMe **Type**: Practical Scenario  **Focus**: Threat Simulation & Detection Engineering Using the Pyramid of Pain

---

## 📘 Project Description

In this interactive, hands-on purple-team simulation, I collaborated with a simulated adversary to iteratively detect and prevent malware across six escalating attack scenarios. Using tools such as EDR, firewall, DNS filtering, and SIEM-integrated Sigma rules, I applied the **Pyramid of Pain** methodology to create increasingly resilient detection mechanisms. The exercise tested my ability to operationalize threat intelligence, engineer behavioral detections, and disrupt attacker TTPs.

---

## 🛠️ What I Did

### 🧊 **1. Hash-Based Detection (Hashes)**
- **Tool**: Malware Sandbox + EDR
- **Action**: Analyzed `sample1.exe` and extracted its hash.
- **Response**: Blocklisted hash via EDR.
- **Result**: Malware execution successfully blocked.

---

### 🔥 **2. Network Indicator Block (IP Addresses)**
- **Tool**: Firewall Rule Manager
- **Action**: Identified C2 IP used by `sample2.exe`.
- **Response**: Created an egress firewall rule blocking `154.35.10.113`.
- **Result**: Prevented communication with adversary infrastructure.

---

### 🌐 **3. Domain-Based Detection (Domain Names)**
- **Tool**: DNS Rule Manager
- **Action**: Found suspicious domain `bresonicz.info` from `sample3.exe`.
- **Response**: Added DNS filter rule, flagged as spyware.
- **Result**: C2 domain communication blocked.

---

### 🧠 **4. Host Artifact Detection (Registry Changes)**
- **Tool**: Sigma Rule Builder (SIEM + Sysmon)
- **Action**: Detected registry tampering by `sample4.exe`.
- **Response**: Wrote a Sigma rule targeting:
  - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender\Real-Time Protection`
  - `DisableRealtimeMonitoring = 1`
  - **MITRE ATT&CK ID**: TA0005 (Defense Evasion)
- **Result**: Malicious Defender modification detected.

---

### 📡 **5. Behavioral Detection (Beaconing)**
- **Tool**: Sigma Rule Builder (Network Connections via Sysmon)
- **Action**: Analyzed beaconing from `sample5.exe` (97 bytes every 1800s).
- **Response**: Created Sigma rule detecting this network pattern.
  - **MITRE ATT&CK ID**: TA0011 (Command & Control)
- **Result**: Detected low-noise persistent C2 channel.

---

### 🎯 **6. TTP-Level Detection (File Creation)**
- **Tool**: Sigma Rule Builder (File Events via Sysmon)
- **Action**: Studied adversary behavior across all samples.
- **Response**: Created a Sigma rule to detect:
  - File: `exfiltr8.log`
  - Path: `%temp%`
  - **MITRE ATT&CK ID**: TA0010 (Exfiltration)
- **Result**: Detected attacker's exfiltration preparation process.

---

## 🔁 Methodology

**Detection Engineering Progression**:
- `Hash Blocking` → `IP Deny` → `DNS Filtering`  
- `Registry Artifact Detection` → `Network Behavior Detection` → `TTP Signature Creation`

---

## 📚 Frameworks & Tools Used

- **Pyramid of Pain** – Threat detection maturity model
- **MITRE ATT&CK** – Threat behavior mapping
- **Sysmon + Sigma Rules** – Detection engineering
- **SIEM** – Log aggregation and alerting
- **Firewall & DNS Filtering** – Network-based prevention
- **Malware Sandbox** – Behavioral file analysis

---

## ✅ Outcome

Through iterative detection engineering, I forced the simulated attacker to abandon the campaign by driving up their operational cost—demonstrating advanced defensive strategy against evolving adversary techniques.

