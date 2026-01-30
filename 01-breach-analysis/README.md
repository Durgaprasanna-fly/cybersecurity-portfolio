# Data Breach Analysis Project

## 📋 Project Overview

Analyzed three major cybersecurity breaches to understand attack vectors, identify security failures, and document prevention strategies. This project demonstrates threat intelligence analysis and risk assessment skills.

**Date Completed:** January 29, 2026  
**Time Invested:** 2 hours  
**Difficulty:** ⭐⭐⭐☆☆

---

## 🎯 Objectives

1. Understand real-world breach attack vectors
2. Apply CIA Triad to actual incidents
3. Identify root causes and prevention strategies
4. Develop security analyst mindset

---

## 🔍 Breaches Analyzed

### 1. Equifax Data Breach (2017)

**Impact:** 147 million people affected

**Data Compromised:**
- Social Security Numbers
- Birth dates
- Addresses
- Driver's license numbers
- 209,000 credit card numbers

**Attack Vector:**
- Exploited unpatched Apache Struts vulnerability (CVE-2017-5638)
- Vulnerability patch was available 2 months before breach
- Attackers maintained access for 3 months (May-July 2017)

**CIA Triad Violation:**
- ✅ Confidentiality (data exposed)
- ❌ Integrity (no modification)
- ❌ Availability (services remained up)

**Root Cause:**
1. Failed patch management process
2. Expired security certificate prevented detection
3. Inadequate network segmentation
4. Lack of proper monitoring

**Prevention Strategies:**
1. **Timely Patching:** Apply critical patches within 48 hours
2. **Automated Vulnerability Scanning:** Weekly scans for known CVEs
3. **Network Segmentation:** Limit database access
4. **Certificate Management:** Monitor certificate expiration
5. **Enhanced Monitoring:** IDS/IPS for exploitation attempts

**Key Lesson:** Patch management is critical. Known vulnerabilities WILL be exploited.

---

### 2. Target Data Breach (2013)

**Impact:** 40 million credit cards, 70 million customer records

**Data Compromised:**
- Credit/debit card numbers
- Customer names, addresses, phone numbers
- Email addresses

**Attack Chain:**
1. **Initial Compromise:** Phishing attack on HVAC vendor (Fazio Mechanical)
2. **Credential Theft:** Stole vendor VPN credentials
3. **Network Access:** Used vendor access to enter Target network
4. **Lateral Movement:** Moved from vendor network to POS systems
5. **Malware Installation:** Deployed Kaptoxa RAM scraper on POS terminals
6. **Data Exfiltration:** Collected and transmitted card data to external servers

**CIA Triad Violation:**
- ✅ Confidentiality (card data stolen)
- ❌ Integrity
- ❌ Availability

**Root Cause:**
1. Excessive vendor network access
2. No network segmentation between vendor and POS networks
3. Ignored security alerts (alerts DID fire but weren't investigated)
4. Lack of endpoint detection on POS systems

**Prevention Strategies:**
1. **Network Segmentation:** Vendors should NEVER access production systems
2. **Least Privilege:** HVAC vendor needed zero access to payment systems
3. **Third-Party Risk Management:** Audit vendor security practices
4. **Zero Trust Architecture:** Don't trust based on network location
5. **Alert Response Procedures:** Every alert must be investigated
6. **EDR/Malware Detection:** Deploy on all endpoints including POS

**Key Lesson:** Trust no one. Segment everything. Act on alerts immediately.

---

### 3. SolarWinds Supply Chain Attack (2020)

**Impact:** 18,000+ organizations including US government agencies

**Attack Method:**
- Nation-state APT (attributed to Russia - Nobelium/APT29)
- Compromised SolarWinds software build environment
- Injected "SUNBURST" backdoor into Orion platform updates
- Malicious updates were digitally signed (appeared legitimate)
- Customers unknowingly downloaded trojanized updates
- Backdoor activated only for select high-value targets

**CIA Triad Violation:**
- ✅ Confidentiality (data stolen from victims)
- ✅ Integrity (software updates modified)
- ❌ Availability

**Why This Was Catastrophic:**
1. **Supply Chain Attack:** Victims trusted the source
2. **Scale:** Single compromise affected thousands
3. **Stealth:** Backdoor was highly sophisticated and selective
4. **Digital Signatures:** Updates appeared completely legitimate
5. **Trust Exploitation:** Violated fundamental security assumption
6. **Persistent Access:** Backdoor provided long-term access

**Root Cause:**
1. Inadequate build environment security
2. Insufficient code review processes
3. Lack of behavioral monitoring
4. Over-reliance on digital signatures
5. No additional integrity checks on updates

**Prevention Strategies:**
1. **Secure Build Pipeline:** Isolated, monitored build environments
2. **Zero Trust for Updates:** Verify even "trusted" sources
3. **Code Signing + Verification:** Multi-layer signing process
4. **Behavioral Monitoring:** Detect unusual software behavior
5. **Supply Chain Audits:** Regular vendor security assessments
6. **Network Segmentation:** Limit blast radius
7. **Update Staging:** Test updates before production deployment

**Key Lesson:** Supply chain attacks are the future. Trust must be earned continuously, not assumed.

---

## 📊 Comparative Analysis

| Breach | Year | # Affected | Attack Type | Primary Failure |
|--------|------|------------|-------------|-----------------|
| Equifax | 2017 | 147M people | Web exploitation | Patch management |
| Target | 2013 | 110M records | Third-party compromise | Network segmentation |
| SolarWinds | 2020 | 18,000+ orgs | Supply chain | Build security |

---

## 🎯 Common Patterns Identified

### 1. Human/Process Failures Over Technology
- All three had security tools available
- Failure was in execution, not technology
- Processes weren't followed consistently

### 2. Significant Detection Delays
- Equifax: 3 months undetected
- Target: Weeks despite alerts firing
- SolarWinds: 9 months undetected
- **Attackers had plenty of time to operate**

### 3. Trust Exploitation
- Equifax: Trusted their patching process
- Target: Trusted vendors with excessive access
- SolarWinds: Customers trusted signed updates
- **"Trust but don't verify" consistently fails**

### 4. Defense in Depth Failures
- Single point of failure led to total compromise
- No compensating controls
- Lack of proper segmentation
- **One breach = full access**

### 5. Known Attack Vectors
- Nothing revolutionary in these attacks
- Equifax: Known CVE, patch available
- Target: Classic vendor → victim path
- SolarWinds: Supply chain risks are documented
- **Attackers use what works**

---

## 🛡️ What I Would Do as a Security Analyst

### 1. Proactive Monitoring
- **Don't just collect alerts - ACT on them**
- Create alert triage procedures
- Escalate unusual patterns immediately
- Target ignored alerts - I won't make that mistake

### 2. Vendor Risk Management
- Audit third-party security quarterly
- Grant minimum necessary access only
- Monitor all vendor connections
- Segment vendor network access completely
- No HVAC vendor should reach POS systems

### 3. Aggressive Patch Management
- Critical patches within 24-48 hours
- Automated vulnerability scanning
- Clear escalation path for unpatched systems
- Regular reporting to management
- Equifax waited 2 months - unacceptable

### 4. Network Segmentation
- Assume breach will happen
- Limit lateral movement
- Segment by function and trust level
- Monitor all east-west traffic
- All three breaches spread due to flat networks

### 5. Behavioral Analysis
- Don't rely only on signatures
- Baseline normal behavior
- Alert on deviations
- Monitor for anomalies in connections and data flows
- Could have detected SolarWinds' unusual activity

### 6. Incident Response Readiness
- Maintain updated playbooks
- Practice incident response regularly
- Know escalation procedures
- Preserve evidence properly
- Fast response when breach occurs

### 7. Security Culture
- Security is everyone's responsibility
- Communicate risk in business terms
- Get buy-in for security investments
- Make secure practices easy
- All three had organizational culture problems

---

## 🚩 Red Flags to Watch For

### 1. Unpatched Known Vulnerabilities
**Indicator:** CVE published 30+ days ago, still not patched  
**Why it matters:** Equifax breach was 100% preventable  
**Action:** Escalate immediately, track to resolution  
**My role:** Weekly vulnerability scans, report critical findings

### 2. Third-Party Access Without Segmentation
**Indicator:** Vendors have production network access  
**Why it matters:** Target breach started with HVAC vendor  
**Action:** Audit vendor access rights quarterly  
**My role:** Monitor all vendor VPN connections

### 3. Ignored Security Alerts
**Indicator:** Alerts fire but no investigation happens  
**Why it matters:** Target HAD alerts but didn't act  
**Action:** Document triage for every alert  
**My role:** Create alert handling playbook

### 4. Flat Network Architecture
**Indicator:** Compromised system can reach sensitive data  
**Why it matters:** All three breaches spread via lateral movement  
**Action:** Push for network segmentation projects  
**My role:** Monitor for unexpected lateral traffic

### 5. Implicit Trust
**Indicator:** Automatic trust of signed software, vendor access, insiders  
**Why it matters:** SolarWinds exploited implicit trust  
**Action:** Implement zero trust principles  
**My role:** Question everything, verify trusted sources

---

## 💡 Skills Demonstrated

- ✅ Threat Intelligence Analysis
- ✅ CIA Triad Application
- ✅ Attack Vector Identification
- ✅ Root Cause Analysis
- ✅ Risk Assessment
- ✅ Prevention Strategy Development
- ✅ Pattern Recognition
- ✅ Security Analyst Mindset
- ✅ Technical Documentation

---

## 📚 Resources Used

- Equifax breach analysis (KrebsOnSecurity)
- Target breach congressional report
- SolarWinds attack analysis (FireEye, Microsoft)
- CVE database (cve.mitre.org)
- Various security vendor reports

---

## 🎓 Lessons Learned

1. **Patch management is non-negotiable** - Known vulnerabilities will be exploited
2. **Network segmentation saves organizations** - Limits blast radius
3. **Act on alerts immediately** - Don't ignore your security tools
4. **Third-party risk is YOUR risk** - Audit vendors rigorously
5. **Supply chain attacks are sophisticated** - Trust must be continuously verified
6. **Defense in depth is critical** - Multiple layers prevent total compromise
7. **Security is a process, not a product** - Technology alone isn't enough

---

## 🔄 How This Applies to Security+ Exam

**Domain 1 - General Security Concepts:**
- CIA Triad violations in every breach
- Defense in depth failures

**Domain 2 - Threats, Vulnerabilities, and Mitigations:**
- Threat actors (APT, cybercriminals)
- Attack vectors (phishing, exploitation, supply chain)
- Vulnerability management importance

**Domain 3 - Security Architecture:**
- Network segmentation critical
- Zero trust principles
- Secure software development

**Domain 4 - Security Operations:**
- Monitoring and detection
- Incident response procedures
- Patch management

**Domain 5 - Security Program Management:**
- Third-party risk management
- Risk assessment and prioritization
- Security policies and procedures

---

## 📈 Next Steps

- Continue analyzing recent breaches
- Build threat intelligence database
- Study MITRE ATT&CK framework
- Practice incident response procedures

---

*This analysis demonstrates my ability to research security incidents, identify root causes, and develop prevention strategies - core skills for a SOC Analyst role.*
