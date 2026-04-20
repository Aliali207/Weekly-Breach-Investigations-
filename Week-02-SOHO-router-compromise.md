# Forest Blizzard (APT28) exploit routers to enable DNS hijacking operations

## 1) Executive Summary:
Forest Blizzard (APT28), a threat actor, has been compromising insecure home and small-office internet equipment like routers (MikroTik and TP-Link). 
Microsoft Threat Intelligence has identified over 200 organizations and 5,000 consumer devices impacted by Forest Blizzard’s malicious DNS infrastructure, 
which could lead to unauthorized information and credential collection.

---

## 2) Attack Timeline:

**Initial Access:**  
Achieved via public vulnerabilities in network devices, such as [T1190].

**Infrastructure Preparation:**  
The actor attempted to conduct adversary-in-the-middle (AiTM) attacks against follow-on connections with the aim of harvesting user account credentials.

**Ongoing Activity:**  
Microsoft Threat Intelligence has observed sustained AiTM attacks related to this initial access campaign.

---

## 3) MITRE ATT&CK Mapping:

| Tactic            | Technique                                   | ID       |
|------------------|---------------------------------------------|----------|
| Initial Access    | Exploit Public-Facing Application           | T1190    |
| Resource Development | Compromise Infrastructure: Network Devices | T1584.008 |
| Credential Access | Adversary-in-the-Middle                     | T1557    |

---

## 4) Detection Opportunities:

**Log Source:**  
Application Log Content (networkdevice:controlplane), Network Traffic Content.

**Detection Logic:**  
Identifying unusual or unauthorized modifications to DNS settings on SOHO devices.

**IOCs:**
- VPS Banner Patterns: SSH on TCP port 56777, SSH on TCP port 35681.
- Targeted Domains: autodiscover-s.outlook[.]com, outlook.office[.]com.
- Infrastructure IPs: 5.226.137[.]151, 5.226.137[.]230, 37.221.64[.]77.

---

## 5) Recommended Mitigations:

**Patch Management:**  
Keep all network devices and firmware up to date to close known vulnerabilities.

**Access Control:**  
Change default administrative credentials and disable remote management (WAN-side) access.

**Monitoring:**  
Set up security monitoring capabilities to collect and analyze network telemetry for signs of DNS hijacking.

---

## 6) Analysis Note:

This incident is a large-scale operation; the adversaries work silently for years to build a vast network of compromised devices for targeted strikes.
Analyzing this case made me realize the complexity of maintaining a high level of security against such persistent and silent threats, 
and the importance of securing even the smallest nodes in a network.
