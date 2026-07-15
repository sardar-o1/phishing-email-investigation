# Microsoft Account Unusual Sign-in Activity – Phishing Email Investigation

## Summary

A suspicious email claiming to be from 'Microsoft' was analyzed to determine whether it was a legitimate security notification or a phishing attempt. The email alleged that unusual sign-in activity had been detected on the recipient's Microsoft account and attempted to create a sense of urgency through brand impersonation and security-themed messaging.

---

# Email Overview

| Field              | Value                                                      |
| ------------------ | ---------------------------------------------------------- |
| **Subject**        | Microsoft account unusual sign-in activity                 |
| **Claimed Sender** | Microsoft                                                  |
| **Sender Address** | Microsoft Account Team <no-reply@access-accsecurity[.]com> |
| **Reply-To**       | solutionteamrecognizd02@gmail[.]com                        |
| **Return-Path**    | bounce@nonkfrgr[.]co[.]uk                                  |
| **Authentication** | SPF=None, DKIM=None, DMARC=PermError                       |
| **Email Format**   | Text/HTML                                                  |

---

# Header Analysis

## Subject Analysis

The subject line references the **Microsoft** brand, a trusted and widely used service.

The phrase **"unusual sign-in activity"** is intended to create concern that the recipient's account may have been compromised. This is a common social engineering technique that exploits **fear** and **urgency** to encourage the recipient to interact with the email.

---

## Sender Analysis

**Sender Address**

`no-reply@access-accsecurity[.]com`

Although the email claims to originate from Microsoft, the sender domain (**access-accsecurity[.]com**) is unrelated to Microsoft's official domains. This mismatch is a strong indicator of brand impersonation.

**Return-Path**

`bounce@nonkfrgr[.]co[.]uk`

The Return-Path domain is also unrelated to Microsoft. The discrepancy between the claimed sender and the Return-Path further strengthens the phishing assessment.

---

## Reply-To Analysis

**Reply-To**

`solutionteamrecognizd02@gmail[.]com`

The Reply-To address differs from the sender address and uses a free Gmail account. Legitimate Microsoft security notifications would not normally direct replies to a personal email account, making this another strong phishing indicator.

---

## Email Authentication

| Authentication | Result                                           |
| -------------- | ------------------------------------------------ |
| **SPF**        | None (`smtp.mailfrom=nonkfrgr.co.uk`)            |
| **DKIM**       | None (message not signed)                        |
| **DMARC**      | PermError (`header.from=access-accsecurity.com`) |

No valid SPF or DKIM authentication was present, meaning the recipient could not verify that the sender was authorized to send email on behalf of the claimed domain.

The DMARC result returned **PermError**, indicating a permanent error while evaluating the sender's DMARC policy. Although this result alone does not confirm phishing, when combined with the sender mismatch and other indicators it increases confidence that the email is malicious.

---

## Sender IP Reputation

**Sender IP**

`89[.]144[.]9[.]87`

The sender IP address was checked using **AbuseIPDB** and had multiple reports associated with suspicious activity.

The IP address is associated with infrastructure unrelated to Microsoft, further supporting the phishing assessment.

---

# Email Body Analysis

The email claims that unusual sign-in activity has been detected on the recipient's Microsoft account. The message attempts to persuade the recipient to interact with the email by responding to the alert or following attacker-controlled content.

### Observed Social Engineering Techniques

* Brand impersonation
* Fear
* Urgency
* Security alert theme
* Credential theft lure

These techniques are designed to pressure recipients into acting before verifying the legitimacy of the message.

---

# Embedded Content Analysis

The email contains the following embedded URL:

`hxxp://thebandalisty[.]com/track/o39473XgziG18708448HxBA1821750yoR33736gMed176`

The HTML source references the URL as a hidden image:

```html
<img alt="" src="http://thebandalisty.com/track/o39473XgziG18708448HxBA1821750yoR33736gMed176" width="1px" height="1px" style="visibility:hidden">
```

This appears to be a 1×1 tracking pixel (web beacon). Tracking pixels are commonly used to determine whether a recipient has opened an email and may collect metadata such as:

* Email open status
* Time of access
* Public IP address
* Email client information

While tracking pixels are also used in legitimate marketing campaigns, their presence within this phishing email contributes to the overall suspicion.

**Threat Intelligence**

VirusTotal identified the embedded URL as suspicious.

---

# Indicators of Compromise (IOCs)

| IOC Type           | Value                               |
| ------------------ | ----------------------------------- |
| Sender Domain      | access-accsecurity[.]com            |
| Reply-To Address   | solutionteamrecognizd02@gmail[.]com |
| Return-Path Domain | nonkfrgr[.]co[.]uk                  |
| Sender IP          | 89[.]144[.]9[.]87                   |
| Tracking Domain    | thebandalisty[.]com                 |

---

# MITRE ATT&CK Mapping

| Tactic         | Technique | ID        |
| -------------- | --------- | --------- |
| Initial Access | Phishing  | T1566 |


---

# Risk Assessment

| Category   | Rating |
| ---------- | ------ |
| Impact     | High   |
| Severity   | High   |
| Confidence | High   |

---

# Containment Recommendations

* Block the sender domain.
* Block the sender IP address.
* Block the tracking domain or URL where appropriate.
* Search the mail environment for similar messages.
* Notify potentially affected users.
  
---

# Detection Opportunities

* Alert when Microsoft display names are used with non-Microsoft sender domains.
* Detect Reply-To addresses that use free email providers while impersonating trusted organizations.
* Flag emails with missing SPF and DKIM authentication.
* Identify hidden external tracking pixels within HTML emails.
* Monitor for sender domains that do not match the claimed organization.

---

# Final Verdict

**Classification:** Phishing

**Confidence:** High

The investigation determined that the email is a phishing attempt impersonating Microsoft through brand abuse and social engineering.

Multiple independent indicators—including sender domain mismatch, Reply-To mismatch, unrelated Return-Path, missing email authentication, suspicious sender IP reputation, hidden tracking pixel, and threat intelligence findings—collectively provide high confidence that the email is malicious.
