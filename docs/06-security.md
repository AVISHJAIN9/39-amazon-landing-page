# Security Audit & Hardening Matrix: Amazon Clone

## OWASP Top 10 Evaluation for E-Commerce

| Threat Category | Severity | Implemented Protection | Recommended Hardening |
|---|---|---|---|
| **A01: Broken Access Control** | Critical | Orders queried per user UID (`doc(user.uid)`). | Enforce strict Firestore Security Rules (`allow read, write: if request.auth.uid == userId`). |
| **A02: Payment & PCI Compliance** | Critical | Stripe `CardElement` tokenization prevents raw card storage. | Ensure all requests are served over HTTPS with TLS 1.3. |
| **A07: Identification & Auth** | High | Firebase Auth enforces encrypted password storage. | Enable Firebase Multi-Factor Authentication (MFA) via SMS/TOTP. |
