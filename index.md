# Phishing Simulation Engagement Summary

**Client:** [Redacted Organization]  
**Operator:** Cyrus Lomibao  
**Date:** April 1–2, 2025
**Status:** ✅ Completed  
**Playbook:** [View on GitHub](https://github.com/cylosec/phishing-campaign)


---

## Objective

Simulate a real-world phishing campaign to evaluate:

- Email server filtering capabilities
- End-user security awareness
- Potential for credential theft or link-click exploitation

---

## Tools & Infrastructure

| Component        | Details                                |
|------------------|----------------------------------------|
| Framework        | GoPhish                                |
| VPS Hosting      | Vultr (Ubuntu 22.04 LTS)               |
| Reverse Proxy    | Nginx (TLS via Let's Encrypt)          |
| Domain           | yourdomain.com (DNS via Namecheap)     |
| Email            | Namecheap Private Mailbox (SPF, DKIM, DMARC 
| Campaign Hosting | Vultr VPS serving https://yourdomain.com/portal |

---

##  Campaign Summary

| Detail           | Info                                        |
|------------------|---------------------------------------------|
| Target Audience  | Internal staff at [REDACTED]          |
| Phishing Email   | Spoofed IT support alert with a "Review Activity" 
| Landing Page     | Custom awareness page: “Portal Login” |
| Data Collected   | Link clicks only (input fields harvested) |
| Authorization    | ✅ Fully approved test engagement            |

---

##  Results

| Metric           | Result              |
|------------------|---------------------|
| Emails Delivered | X (e.g., 25)        |
| Open Rate        | X% (e.g., 76%)      |
| Click Rate       | X% (e.g., 48%)      |
| Repeat Clickers  | X (e.g., 3)         |
| False Positives  | None / Low / High   |


---

##  Observations & Lessons

-  SPF/DKIM/DMARC were bypassed successfully due to aliasing
-  Some users clicked immediately with no link hovering or scrutiny
-  No internal alert was triggered (could improve detection stack)

---

##  Recommendations

- Train users to hover over links and verify senders
- Configure advanced link scanning or sandboxing
- Add mailbox rules to flag similar spoofed emails
- Expand SOC monitoring to include phishing indicators

---

##  Notes

- This was a **harmless** engagement with no credential theft
- Email link resolved to an internal awareness page, not a live exploit
- Results have been anonymized for public documentation

---

> Want the full toolkit? See [`configs/`](https://github.com/cylosec/phishing-campaign/tree/main/configs) and 
[`campaigns/`](https://github.com/cylosec/phishing-campaign/tree/main/campaigns)


