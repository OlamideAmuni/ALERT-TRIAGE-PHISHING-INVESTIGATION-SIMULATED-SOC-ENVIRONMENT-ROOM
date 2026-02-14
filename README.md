## SOC ALERT TRIAGE AND PHISHING INVESTIGATION-SIMULATED SOC ENVIRONMENT
# Environment Overview
This investigation was conducted within a simulated SOC dashboard environment consisting of:
- Alert Queue (Real-time alerts)
- SIEM Log Management Interface
- Firewall Logs
- Email Logs
- Threat Intelligence Platform (IOC validation)
- Analyst Virtual Machine

The environment simulated real-time log ingestion from multiple data sources including firewall and email security systems.

# Objective
To triage multiple alerts, determine True Positives vs False Positives, perform correlation across data sources, enrich indicators using threat intelligence feeds, and document findings with recommendations.

# Alert Overview:
Total Alerts: 5
1 High Severity (Firewall data source)
4 Medium Severity (Email data source)

I Followed standard SOC prioritization procedures:
"High to Medium to Low"
The High severity alert was investigated first.
## Investigation Workflow
 # High Severity Firewall Alert
 - Alert Type: Suspicious outbound connection
 - Data Source: Firewall Logs
   
The firewall detected an internal system attempting to establish a connection with an external IP address.

Findings:
- Destination IP was already listed in the organization’s Threat Intelligence blacklist.
- The firewall successfully blocked the connection.
- Correlated timestamp revealed that the connection attempt occurred shortly after a phishing email was received and accessed.
- 
# Correlation Identified:
Email Log to User Clicked Malicious URL to Firewall Block Event
- Verdict:
True Positive
- Escalation:
Escalated to Tier 2 for:
Endpoint validation
Confirmation of no credential compromise
Further investigation of potential payload execution

# Phishing Email Analysis
1. Indicators Observed:
- Urgency-based language (“Complete within 48 hours”)
- Brand impersonation (Amazon / Microsoft themes)
- Lookalike domains (typosquatting techniques)
- Suspicious sender domains (e.g., m1crosoft.support.co)
- Character substitution (e.g., M1cro instead of Micro)

2. URL Validation:
  The attached URL in the email content was checked against the threat intelligence platform and returned as clean. and this same url is found in the firewall logs, it is the url creating the connection between the internal system and the external malicious IP address 
Assessment: Likely newly registered or previously unreported phishing infrastructure.

3. Actions Taken:
- Recommended adding URL and associated IP address to IOC blacklist
- Suggested blocking sender infrastructure
- Recommended user awareness notification
- Escalated confirmed phishing alerts
  
## False Positive Handling
Two alerts were investigated and determined to be legitimate communications from verified sources.
Justification included:
- Legitimate domain validation
- No malicious indicators observed
These were documented and closed as False Positives.

## Tools & Techniques Used
- SIEM Log Filtering & Search Queries
- Firewall Log Analysis
- Email Content & Sender Analysis
- Threat Intelligence Enrichment
- IOC Correlation
- Alert Prioritization Workflow
- Manual Event Log Validation

# Key Skills Demonstrated
- Alert prioritization under simulated SOC workflow
- Cross-source log correlation
- Alert enrichment
- Detection of typosquatting and phishing tactics
- Escalation decision-making
- Structured Reporting
  
## Challenges Faced
This was my first interaction with a full SOC dashboard environment and it is tryhackme hands on room.

Initial challenges included:

- Navigating between alert queue and log sources
- Understanding workflow between SIEM, Threat Intel, and Analyst VM
- Determining optimal triage starting point
  
Approximately 3 hours were spent thoroughly investigating and validating alerts, ensuring accurate classification and documentation.

## Lessons Learned

- Correlation across data sources is critical in phishing investigations.
- “Not flagged” does not mean “Not malicious.” this is very important
- Alert context is as important as detection output.
- Clear documentation strengthens incident response effectiveness.

## MITRE ATT&CK Mapping
ATTACK tactics: initial access (phishing) T1566
ATTACK.Technique: Spearphishing Link T1566.002
  
## Conclusion
This exercise provided practical experience in SOC operations, alert triage, phishing investigation, and cross-log correlation within a simulated enterprise environment.
It reinforced the importance of structured analysis, enrichment validation, and escalation discipline in blue team operations.
