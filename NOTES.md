# Technical Notes: Phishing Simulation Concepts

## 1. Bypassing DMARC with SPF/DKIM

During this engagement, emails were sent from a domain I controlled (`yourdomain.com`) and configured 
with valid SPF and DKIM records.

### Key Points:
- SPF passed because the sending IP matched the `yourdomain.com` SPF record.
- DKIM passed because emails were signed with my domain’s private key.
- DMARC alignment may fail if the `From:` header uses a different domain (e.g., 
`it-support@targetdomain.com`), but delivery may still occur if the target’s DMARC policy is weak 
(`p=none` or `p=quarantine`).

This technique relies on:
- Visual deception using a mismatched `From:` address
- Lenient DMARC policy on the recipient server
- Proper SPF/DKIM configuration on the sender's domain

In this campaign, emails passed SPF and DKIM from `yourdomain.com`, while impersonating a support account 
at `yourcompany.com`.

## 2. Importance of HTTPS and SSL Certificates

Using HTTPS with a valid SSL certificate (via Let’s Encrypt) is essential in phishing simulations to 
enhance credibility and avoid detection.

### Benefits:
- Avoids browser security warnings that could alert users
- Increases deliverability by avoiding filters that flag non-secure links
- Makes phishing links appear more legitimate, especially with a professional domain
- Enables secure proxying via Nginx

This project used Let's Encrypt TLS certificates on a Vultr VPS to securely serve phishing pages at 
`https://yourdomain.com/portal`.

## Summary

By combining domain control, properly configured SPF/DKIM records, and HTTPS encryption, a phishing 
simulation can bypass basic security filters and accurately test both user awareness and email 
infrastructure—while remaining ethical and controlled.

