# Google Dorking — Complete Student Notes

---
# Google Dorking — Overview

## What is Google Dorking?
Google Dorking (aka Google Hacking) is the practice of using advanced search operators and crafted queries to find specific information indexed by Google.  
It’s commonly used in:
- OSINT investigations
- Penetration testing
- Defensive security checks

---

## Why is it Important?
- Discover exposed documents, admin portals, or backups.
- Helps organizations fix leaks before attackers exploit them.
- Essential skill for **cybersecurity students and professionals**.

---

## ⚖️ Legal & Ethical Reminder
- Always have **written permission** before testing.
- Only use for authorized security work or research.
- Never misuse discovered data.
- Practice **responsible disclosure**.

---

# Google Dorking — Core Search Operators

## Core Operators
- `site:domain.com` → Restrict results to a domain
- `filetype:pdf` or `ext:xlsx` → Search by file extension
- `inurl:term` / `allinurl:terms` → Terms in URL
- `intitle:term` / `allintitle:terms` → Terms in page title
- `intext:term` → Terms in page body
- `"exact phrase"` → Match exact phrase
- `-term` → Exclude results containing term
- `OR` → Logical OR
- `cache:URL` → View cached copy

---

## Example Queries
```
site:example.com filetype:pdf "employee handbook"
site:example.com inurl:admin
site:example.com intitle:"index of" backup
"confidential" filetype:docx site:example.com
```

---

# Google Dorking — Practical Lab

## Step-by-Step Safe Recon
1. Confirm scope & permission.
2. Start broad → `site:target.com filetype:pdf`.
3. Refine with operators like `intitle:`, `inurl:`.
4. Record findings (URL, query, risk level).
5. Classify risk (High / Medium / Low).
6. Suggest remediation.
7. Re-run queries to confirm fixes.

---

## Hands-On Queries (Use in Lab Domain)
```
site:lab.example.local filetype:pdf
site:lab.example.local inurl:admin OR inurl:login
site:lab.example.local intitle:"index of" backup
site:lab.example.local "confidential" filetype:docx
```

⚠️ Rule: Never access/download sensitive files without permission.

---

## Classroom Exercises
- **Find & classify** 5 exposures in the lab.
- **Remediation task**: fix or suggest fixes.
- **Disclosure writing**: draft a professional report.
- **GHDB review**: explain 3 risky dorks.

---

# Google Dorking — Remediation

## Common Fixes
- Move sensitive files out of webroot.
- Disable directory listing:
  - Apache: `Options -Indexes`
  - Nginx: `autoindex off;`
- Protect admin pages with authentication.
- Set correct permissions on storage.
- Add `noindex` or `X-Robots-Tag: noindex`.
- Use **Google Search Console** to remove from index.
- Rotate any exposed credentials.

---

## Best Practices
- Regularly run defensive dorks on your own domains.
- Automate checks with OSINT tools (theHarvester, SpiderFoot).
- Train devs to avoid pushing secrets into public repos.
- Set up monitoring for leaks.

---

# Google Dorking — Responsible Disclosure Template

## Sample Email

```
Subject: Publicly exposed file on <domain> — action suggested

Hello <Admin>,

During an authorized review I found a publicly accessible file that may contain sensitive data:
URL: https://<domain>/<path>/<file>
Reason: Backup file likely containing DB credentials and PII.

I did not download the file. Recommended actions:
1. Remove file from webroot and move to secure storage.
2. Restrict access (auth/ACLs).
3. Rotate any credentials if exposed.

I’m happy to assist in verification.

Regards,
[Name] — [role/contact]
```

---

## Quick Quiz
1. What does `intitle:` search for?  
2. Give a dork to find Excel files on example.com.  
3. True/False: `robots.txt` is a security measure.  
4. What should you do first before dorking a target domain?  
5. Name two ways to fix exposed backups.

