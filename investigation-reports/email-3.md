# Your Account Will be Temporary Suspended And Hold All Your Subscription, Thursday 07 September 2023. ID-2610355057 -- Email Investigation

### Summary

This investigation analyzes a phishing email using an account-suspension and subscription-related lure. The message creates urgency and fear by claiming that the recipient's account and subscriptions will be temporarily suspended.

The email contains several suspicious indicators, including Apple brand impersonation, an unusual sender address, a randomly generated-looking ID in the subject, weak email authentication, a sender IP associated with reported malicious activity, and a malicious PDF attachment.

### Email Overview

| Field          | Value                                                             |
| -------------- | ----------------------------------------------------------------- |
| Subject        | Your Account Will be Temporary Suspended And Hold All Your Subscription, Thursday 07 September 2023. ID-2610355057 |
| Sender Address | =?UTF-8?Q?Ap=DC=BFpl=DC=BFe_ID?= <auth-replyP8YjBYJqsq@lynnswig[.]com> |
| Recipient      | math[.]kichuu@hotmail[.]com   |
| Date           | Thu, 07 Sep 2023 16:40:21 +0000  |       
| Attachment     | Support-1923819248-67889.pdf |

### Header Analysis

#### Subject Analysis

Subject: Your Account Will be Temporary Suspended And Hold All Your Subscription, Thursday 07 September 2023. ID-2610355057

The subject contains several social-engineering indicators:
-	Urgency: The message suggests immediate account action is required.
-	Fear: The recipient is warned that their account and subscriptions may be suspended.
-	Random identifier: ID-2610355057 gives the message an appearance of legitimacy or an official case/reference number.
-	Unnatural wording: The phrase "Your Account Will be Temporary Suspended" is grammatically unusual and may indicate that the message was not written as a normal official notification.

#### Return-Path Analysis
The supplied analysis indicates that the From address and Reply-To/return-path information are consistent. No sender/return-path mismatch was identified from the available evidence.


#### Sender Analysis
From: =?UTF-8?Q?Ap=DC=BFpl=DC=BFe_ID?= <auth-replyP8YjBYJqsq@lynnswig[.]com>
The display name contains encoded/non-ASCII characters and appears designed to resemble Apple ID branding. 

The sender domain is `lynnswig[.]com`. The domain does not correspond to Apple's official domain. The combination of an Apple-related display name with an unrelated domain is a significant impersonation indicator.

### Email Authentication

| Authentication | Result                                         |
| -------------- | ---------------------------------------------- |
| SPF            | spf=pass (sender IP is 40[.]107[.]94[.]65)smtp.mailfrom=lynnswig[.]com |
| DKIM           | none (message not signed)                      |
| DMARC          | bestguesspass action=none                      |

The authentication results do not independently prove that the email is legitimate. SPF passed, but DKIM was absent and the DMARC result was bestguesspass.

### Sender IP Reputation

Sender IP:  40[.]107[.]94[.]65

Threat-intelligence checks identified reports associated with this IP involving phishing, spam, and malicious activity. According to AbuseIPDB, the IP address has been reported 26 times in connection with phishing, spam, and other malicious activity. VirusTotal also showed malicious files referring to this IP.

### Email Body Analysis

The empty email body is suspicious because the message provides no explanatory content and appears to rely primarily on the attachment to deliver the phishing content.

The absence of a normal email body also makes the PDF attachment particularly important to the investigation.

### Embedded Attachment Analysis

| Item          | Value                                                              |
| ------------- | ------------------------------------------------------------------ |
| Attachment    | Support-1923819248-67889.pdf                                                      |
| SHA-256       | `5a4bca6bba94940a13312f3030dcc9e0f9533dde6282aea31f82ee7f7be5ec4b` |

VirusTotal detections indicate that the PDF can automatically initiate navigation to an external web resource designed to harvest user credentials through a fraudulent website. This provides strong evidence that the attachment was intended to facilitate phishing and credential theft.

### Indicators of Compromise (IOCs)

| IOC Type      | Value                                                              |
| ------------- | ------------------------------------------------------------------ |
| Sender Email  | `auth-replyP8YjBYJqsq@lynnswig[.]com`                                        |
| Sender Domain | `lynnswig[.]com`                                                        |
| Subject       | `Your Account Will be Temporary Suspended And Hold All Your Subscription, Thursday 07 September 2023. ID-2610355057`    |
| IP Address    | `40[.]107[.]94[.]65`                                             |
| Attachment    | `Support-1923819248-67889.pdf`                                                    |
| SHA-256       | `5a4bca6bba94940a13312f3030dcc9e0f9533dde6282aea31f82ee7f7be5ec4b` |

### Risk Assessment

| Category    | Rating                           |
| ----------- | -------------------------------- |
| Confidence  | High                             |
| Severity    | High                             |
| Threat Type | Phishing – Credential Harvesting |

### Recommended Containment Actions

*	Quarantine the email and prevent further delivery.
*	Identify users who received or opened the attachment.
*	Block confirmed malicious domains/IPs based on threat-intelligence findings.
*	Preserve the original email and attachment as forensic evidence.

### MITRE ATT&CK Mapping

| Technique     | ID    |
| ------------- | ----------------------------------- |
| Phishing: Spearphishing Attachment   | T1566.001   |

## Final Verdict

The email demonstrates multiple phishing indicators, including Apple brand impersonation, an unrelated sender domain, account-suspension and subscription-related urgency, a random-looking reference ID, and a suspicious PDF attachment.

SPF authentication passed, but DKIM was not present and the DMARC result was bestguesspass. Therefore, the authentication results do not independently establish the legitimacy of the message. The sender IP also has reputation indicators associated with phishing, spam, and malicious activity. The email is assessed as a high-confidence phishing attempt involving a suspicious/malicious PDF attachment. VirusTotal analysis identified indicators associated with credential theft and URL redirection, providing additional evidence that the attachment was intended to support a phishing attack. 

