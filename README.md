📌 SOC Alert Triage & Phishing Investigation – Simulated SOC Environment
🏢 Environment Overview
This investigation was conducted within a simulated SOC dashboard environment consisting of:
Alert Queue (Real-time alerts)
SIEM Log Management Interface
Firewall Logs
Email Logs
Threat Intelligence Platform (IOC validation)
Analyst Virtual Machine
The environment simulated real-time log ingestion from multiple data sources including firewall and email security systems.
🎯 Objective
To triage multiple alerts, determine True Positives vs False Positives, perform correlation across data sources, enrich indicators using threat intelligence feeds, and document findings with recommendations.
🚦 Alert Overview
Total Alerts: 5
1 High Severity (Firewall)
4 Medium Severity (Email-related)
Following standard SOC prioritization procedures:
High → Medium → Low
The High severity alert was investigated first.
🔎 Investigation Workflow
1️⃣ High Severity Firewall Alert
Alert Type: Suspicious outbound connection
Data Source: Firewall Logs
The firewall detected an internal host attempting to establish a connection with an external IP address.
Findings:
Destination IP was already listed in the organization’s Threat Intelligence blacklist.
The firewall successfully blocked the connection.
Correlated timestamp revealed that the connection attempt occurred shortly after a phishing email was received and accessed.
Correlation Identified:
Email Log → User Clicked Malicious URL → Firewall Block Event
Verdict:
True Positive
Escalation:
Escalated to Tier 2 for:
Endpoint validation
Confirmation of no credential compromise
Further investigation of potential payload execution
📧 Phishing Email Analysis
Indicators Observed:
Urgency-based language (“Complete within 24 hours”)
Brand impersonation (Amazon / Microsoft themes)
Lookalike domains (typosquatting techniques)
Suspicious sender domains (e.g., microsoft.support.co)
Character substitution (e.g., M1cru instead of MICRU)
URL Validation:
One malicious URL was checked against the threat intelligence platform and returned as clean.
Assessment: Likely newly registered or previously unreported phishing infrastructure.
Actions Taken:
Recommended adding URL and associated IP address to IOC blacklist
Suggested blocking sender infrastructure
Recommended user awareness notification
Escalated confirmed phishing alerts
⚖ False Positive Handling
Two alerts were investigated and determined to be legitimate communications from verified sources.
Justification included:
Legitimate domain validation
Expected business context
No malicious indicators observed
These were documented and closed as False Positives.
🛠 Tools & Techniques Used
SIEM Log Filtering & Search Queries
Firewall Log Analysis
Email Content & Sender Analysis
Threat Intelligence Enrichment
IOC Correlation
Alert Prioritization Workflow
Manual Event Log Validation
🔄 Key Skills Demonstrated
Alert prioritization under simulated SOC workflow
Cross-source log correlation
IOC validation and enrichment
Detection of typosquatting and phishing tactics
Escalation decision-making
Structured case documentation
🧠 Challenges Faced
This was my first interaction with a full SOC dashboard environment.
Initial challenges included:
Navigating between alert queue and log sources
Understanding workflow between SIEM, Threat Intel, and Analyst VM
Determining optimal triage starting point
Approximately 3 hours were spent thoroughly investigating and validating alerts, ensuring accurate classification and documentation.
📌 Lessons Learned
Correlation across data sources is critical in phishing investigations.
“Not flagged” does not mean “Not malicious.”
Alert context is as important as detection output.
Clear documentation strengthens incident response effectiveness.
🏁 Conclusion
This exercise provided practical experience in SOC operations, alert triage, phishing investigation, and cross-log correlation within a simulated enterprise environment.
It reinforced the importance of structured analysis, enrichment validation, and escalation discipline in blue team operations.
