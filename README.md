# **Incident Response Capstone: Comprehensive Investigation and Remediation Report**
## **Table of Contents**
- [Overview](#overview)
- [Steps Taken](#steps-taken)
  - [1. Initial Identification of File Inaccessibility](#1-initial-identification-of-file-inaccessibility)
  - [2. Tracing the Initial Infection Vector](#2-tracing-the-initial-infection-vector)
  - [3. Investigating Lateral Movement](#3-investigating-lateral-movement)
  - [4. Investigating Website Defacement](#4-investigating-website-defacement)
  - [5. Incident Response and Remediation](#5-incident-response-and-remediation)
- [Tools Used](#tools-used)
- [Conclusion](#conclusion)
- [How to Use](#how-to-use)
- [Contact](#contact)

## **Overview**
This project demonstrates a detailed incident response process during a simulated ransomware attack. The steps include identification, investigation, lateral movement analysis, website defacement recovery, and final incident remediation. It was conducted in a RangeForce virtual environment and showcased both technical skills and analytical expertise required for incident response roles.

---

## **Steps Taken**

### **1. Initial Identification of File Inaccessibility**
The investigation began with a user reporting file inaccessibility issues. The following actions were taken:

![file explore](https://github.com/user-attachments/assets/4234e427-0e68-46de-b22d-c13fbb5ac20a)

- **Symptoms Observed:** User unable to open files; error messages indicated encryption.
- **Logs Inspected:** Reviewed endpoint and server logs for potential malware-related activity.
- **Findings:**
  - File extensions had been altered.
  - Presence of a ransom note in encrypted directories.

---

### **2. Tracing the Initial Infection Vector**
The source of the infection was identified through log analysis and Splunk queries.

<img width="1728" alt="Screenshot 2025-01-02 at 10 59 47 AM" src="https://github.com/user-attachments/assets/bc6656de-6116-435f-86c7-2e2fbadad6ba" />

- **File Executable:** `Emoji Downloader.exe`
- **Path to Executable:** `C:\Users\emmanueltoller\Downloads\Emoji Downloader.exe`
- **Downloaded URL:** `http://kindofwelcomepersective.com`
- **Browser Used:** Chrome
- **IP Address of Source Domain:** `11.0.178.14`
- **Technique Used:** Drive-by Compromise

---

### **3. Investigating Lateral Movement**
The malware leveraged lateral movement techniques to spread across the network.

- **Host Targeted:** `windows10-2`
- **Port Used:** `445`
- **Account Leveraged:** `DomainAdmin`
- **Analysis of Logs:**
  - EventID `4648` was observed indicating malicious logon attempts.
  - Maintained persistence across compromised devices using the domain administrator account.
<img width="1728" alt="Screenshot 2025-01-04 at 11 32 46 AM" src="https://github.com/user-attachments/assets/0c2015fb-65ac-4419-8cc1-32edd4ebb2ce" />

---

### **4. Investigating Website Defacement**
![hacked img](https://github.com/user-attachments/assets/e86158e6-0381-4084-8e9d-4cb3e33d10d8)

The attacker used credentials obtained from the compromised host to access the company's web server.
- **Evidence of Defacement:** Website homepage was replaced with a "Hacked" banner.
- **Backdoor Planted:** `profiles.php`
- **Malicious Image Used:** `hacked.png`
- **Command Used to Replace Images:** `for i in /var/www/www.commensuratetechnology.com/`
- **Persistence Mechanism:** Cron job
- **URI Path:** `/index.php`
- **URL Parameter:** `cmd`
- 
<img width="1728" alt="Screenshot 2025-01-04 at 11 32 36 AM" src="https://github.com/user-attachments/assets/bd917f49-1614-4ea1-a098-7783ea293051" />
<img width="1728" alt="Screenshot 2025-01-04 at 11 32 31 AM" src="https://github.com/user-attachments/assets/796bec29-fd30-42d4-a004-df9f5857f393" />

---

### **5. Incident Response and Remediation**
The remediation phase involved the following steps:
1. **Isolated Infected Systems:** Quarantined compromised devices to prevent further spread.
2. **Removed Persistence Mechanisms:**
   - Deleted malicious cron jobs.
   - Removed registry keys associated with persistence.
3. **Changed All Credentials:** Reset passwords for all compromised accounts.
4. **Restored Defaced Website:**
   - Used backups to restore the original web pages.
   - Increased security protocols on the web server.
5. **Enabled Additional Security Measures:**
   - Multi-factor authentication (MFA) for all accounts.
   - Increased password complexity requirements.
6. **Verified Systems:** Conducted a thorough review of logs and performed an antivirus scan to ensure all malware traces were removed.

---

## **Tools Used**
- **Splunk:** For log analysis and query execution.
- **RangeForce Virtual Environment:** Simulated the enterprise environment.
- **Browser and URL Analysis:** Verified domains and executables.
- **Linux Commands:** For cron job and malicious file removal.

---

## **Conclusion**
This investigation and remediation showcase the complete incident response lifecycle, including:
1. Identifying and tracing the infection vector.
2. Investigating the spread through lateral movement.
3. Recovering from a website defacement.
4. Applying security controls to prevent future attacks.

This project demonstrates expertise in:
- Malware analysis.
- Network traffic analysis.
- Forensic investigation.
- Incident remediation and recovery.

---

## **How to Use**
This repository can serve as a reference for:
- Incident response training.
- Preparing for cybersecurity certifications (e.g., CEH, CompTIA Security+, CISSP).
- Demonstrating cybersecurity expertise during interviews or technical assessments.

---

### **Contact**
For more information or queries, feel free to reach out:
- **Name:** Osamudiamen Eweka
- **Email:** oseweka2@gmail.com
- **LinkedIn:** https://www.linkedin.com/in/osamudiamen-eweka/

---
