# phishing-email-investigation

## Lab Objective

Email remains one of the most common entry points for attackers targeting companies and organizations. This project demonstrates a structured approach to investigating phishing emails using real world samples collected from phishing_pot repositories. Each investigation follows a repeatable SOC analyst workflow that includes email header analysis, sender verification, authentication review, IOC extraction, threat intelligence enrichment, and incident reporting.

The objective of this lab is to develop practical phishing analysis skills that are essential for an entry level Security Operations Center (SOC) Analyst role.

---

## Skills Demonstrated

-	Email Header Analysis
-	Sender Verification
-	SPF, DKIM, and DMARC Analysis
-	Received Header Analysis
-	Social Engineering Analysis
-	URL Analysis
- Indicator of Compromise (IOC) Extraction
-	Threat Intelligence Research
-	MITRE ATT&CK Mapping
-	Incident Documentation

---

## Tools Used

- Kali Linux (analysis environment)
- Thunderbird
- VirusTotal
- AbuseIPDB
- CyberChef
- URLScan
- MXToolBox
- WHOIS / DNS Lookup

---

## Investigation Workflow

```text
                    Email Sample
                         │
                         ▼
               Email Header Analysis
                         │
                         ▼
              Sender Verification
                         │
                         ▼
        SPF / DKIM / DMARC Analysis
                         │
                         ▼
             Received Header Analysis
                         │
                         ▼
             Email Body Examination
                         │
                         ▼
           URL & Attachment Analysis
                         │
                         ▼
        IOC Extraction (IP, Domain, URL)
                         │
                         ▼
      Threat Intelligence Enrichment
                         │
                         ▼
          MITRE ATT&CK Mapping
                         │
                         ▼
         Risk Assessment & Verdict
                         │
                         ▼
           Incident Documentation
```


## Learning Goals

- Strengthen phishing detection and investigation skills.
- Practice analyzing real-world email headers.
- Improve the identification of phishing indicators and attacker techniques.
- Gain hands-on experience using threat intelligence platforms.
- Produce professional investigation reports following SOC best practices.

