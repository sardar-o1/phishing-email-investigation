# FW: Due Invoice Payment - protonmail.com - Wire Transfer Document - Email Investigation

### Summary

This email uses a financial payment theme and urgency to pressure the recipient into processing an overdue invoice payment. The “FW:” prefix attempts to make the message appear as part of an existing business conversation. The email contains an attached ISO file (`quotation.iso`), which was analyzed to determine whether the message was legitimate or intended to deliver malware.

### Email Overview

| Field          | Value                                                             |
| -------------- | ----------------------------------------------------------------- |
| Subject        | FW: Due Invoice Payment - protonmail.com - Wire Transfer Document |
| Sender Address | Paolo Reggiani <Paol[.]Reggiani@moss[.]it>                        |
| Recipient      | wpx@protonmail[.]com                                              |
| Date           | 14 Jan 2020 00:06:05 -0800                                        |
| Attachment     | quotation.iso                                                     |

### Header Analysis

#### Subject Analysis

* The “FW:” prefix attempts to make the email appear as part of an ongoing conversation.
* “Due Invoice Payment” creates urgency and financial pressure.
* “Wire Transfer Document” is a common Business Email Compromise (BEC) and invoice phishing lure.

#### Sender Analysis

The sender address `Paol[.]Reggiani@moss[.]it` does not clearly align with the referenced `protonmail.com` invoice payment request, which is suspicious in the context of a financial payment email.

### Email Authentication

| Authentication | Result                                         |
| -------------- | ---------------------------------------------- |
| SPF            | spf=fail smtp.mailfrom=Paol[.]Reggiani@moss[.]it |
| DKIM           | none                                         |
| DMARC          | none (p=none dis=none)                       |

The sender failed SPF authentication for the `moss.it` domain, and both DKIM and DMARC validation were absent. These authentication failures are strong indicators that the email may have been spoofed or sent from unauthorized infrastructure.

### Received Header Analysis

`from moss.it (unknown [213[.]227[.]154[.]65]) by mailin004.protonmail.ch`

The Received header indicates that the email originated from a server identifying itself as `moss.it` with the IP address `213[.]227[.]154[.]65`. The hostname was reported as `unknown`, suggesting that the SMTP connection did not present a recognized reverse DNS hostname.

#### Threat Intelligence

VirusTotal research showed that the IP address `213[.]227[.]154[.]65` has been referenced in multiple email samples associated with phishing activity, increasing suspicion around the sending infrastructure.

### Return-Path Analysis

`Return-Path: Paolo Reggiani <Paol[.]Reggiani@moss[.]it>`

The Return-Path matched the From address; therefore, no mismatch was identified between these fields.

### Email Body Analysis

The message uses a business-themed financial payment pressure, claiming that overdue invoices require immediate settlement. The attacker attempts to manipulate the recipient using the following social engineering techniques:

* Financial invoice/payment theme
* Urgency (“today”, “urgent”)
* Reference to a colleague or prior discussion
* Request to verify bank details
* Malicious attachment disguised as a transfer slip

### Embedded Attachment Analysis

| Item          | Value                                                              |
| ------------- | ------------------------------------------------------------------ |
| Attachment    | quotation.iso                                                      |
| File Type     | ISO 9660 CD-ROM filesystem data 'makave (2)_protected_68A4BB0'                                    |
| SHA-256       | `75fdb848eac332b4ca7d88f497e7ba7ebbb9a798d825b28cf1f87b9d7149e87f` |

The ISO attachment contains a Windows executable file (`makave (2)_protected_68A4BB0.exe`). VirusTotal detections indicate that the file hash is associated with malware, providing strong evidence that the attachment was intended to deliver malware to the recipient.

### Indicators of Compromise (IOCs)

| IOC Type      | Value                                                              |
| ------------- | ------------------------------------------------------------------ |
| Sender Email  | `Paol[.]Reggiani@moss[.]it`                                        |
| Sender Domain | `moss[.]it`                                                        |
| Subject       | `Due Invoice Payment - protonmail.com - Wire Transfer Document`    |
| IP Address    | `213[.]227[.]154[.]65`                                             |
| Attachment    | `quotation.iso`                                                    |
| SHA-256       | `75fdb848eac332b4ca7d88f497e7ba7ebbb9a798d825b28cf1f87b9d7149e87f` |

### Risk Assessment

| Category    | Rating                           |
| ----------- | -------------------------------- |
| Confidence  | High                             |
| Threat Type | Phishing with malware attachment |
| Severity    | High                             |

### Recommended Containment Actions

* Block the sender domain `moss.it`.
* Block the IP address `213[.]227[.]154[.]65`.
* Search the environment for similar emails and related IOCs.
* Quarantine the email and prevent attachment execution.
* Isolate affected systems if the attachment was opened.
* Confirm whether any user interaction occurred.
  
### MITRE ATT&CK Mapping

| Technique     | ID    |
| ------------- | ----------------------------------- |
| Phishing: Spearphishing Attachment   | T1566.001   |

### Final Verdict

**Classification:** Phishing email delivering malware via ISO attachment

This email is a high-confidence phishing attempt using a financial payment pressure to mislead the recipient into downloading and opening the attached ISO file (`quotation.iso`). The “FW:” prefix attempts to make the message appear as part of an existing business conversation, while the invoice and wire transfer theme creates urgency. SPF authentication failed, and both DKIM and DMARC validation were absent, preventing verification of sender authenticity. The ISO attachment contained a Windows executable file (`makave (2)_protected_68A4BB0.exe`), and VirusTotal detections indicate that the file hash is associated with malware. Based on the authentication failures, social engineering tactics, suspicious attachment type, and malware detection, the email should be classified as a phishing email attempting malware delivery.
