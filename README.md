# SAFEPASS
SafePass — a privacy-first web password manager (Django) that secures credentials with AES-256-GCM, offers 2FA (email OTP), NIST-compliant password generation, breach scanning via k-anonymity (HIBP), secure RSA-based sharing, trusted-device controls, sign-in monitoring and recovery kit.
afePass is a research-grade, privacy-first web password manager built with security and usability in mind. Designed as a final-year project, SafePass combines practical features (password generation, secure sharing, breach scanning) with strong cryptography and monitoring tools to help individuals and small teams manage credentials safely and confidently.

Key highlights

AES-256-GCM for encrypted password storage and RSA for secure sharing.

Two-factor authentication (email OTP) and trusted-device controls for safer logins.

Real-time breach scanning using the Have I Been Pwned (HIBP) model and password-health checks that follow NIST guidance.

Recovery kit, sign-in activity monitoring, and secure vault sharing — features often missing from many consumer tools.

Built with Django (Python) and SQLite — modular design for easy extension and cloud deployment.

Features

Encrypted credential storage — master-password derived keys with AES-256-GCM.

Password generator — NIST-compliant strong password creation with options (length, special/ambiguous chars).

Password health & reuse detection — automatic scoring and recommendations.

Data breach scanner — k-anonymity style hash prefix checks against breach datasets.

Secure sharing — decrypt with sender’s key, re-encrypt with receiver’s public key for safe transfer.

Two-Factor Authentication (2FA) — OTP via email for robust account protection.

Trusted devices & session monitoring — approve devices and view login history.

Recovery kit — exportable recovery key to regain access if master password is lost.

Admin console — user management and activity monitoring for small deployments.

Tech stack

Backend: Python 3, Django

Frontend: HTML, CSS, JavaScript (bootstrap-ready)

Database: SQLite3 (dev) — easily swappable with PostgreSQL for production

Cryptography: pycryptodome / cryptography primitives (AES-256-GCM, RSA)

Auth & utilities: pyotp, hashlib, secure email (SMTP + TLS)

APIs: HIBP-style breach checking (k-anonymity prefix checking model)

Security & design principles

Minimal trusted surface: only encrypted data stored — secrets are protected client-side/right before storage using keys derived from the master password.

Defense in depth: encryption at rest, 2FA, trusted devices, and sign-in monitoring.

Privacy-first breach checks: only hashed prefixes are sent for breach scanning (k-anonymity).

Tested against common scenarios and OWASP guidance — unit/manual test cases included.

Quick start (local development)

Clone the repo

Create & activate a Python 3 virtual env

Install requirements: pip install -r requirements.txt

Apply migrations: python manage.py migrate

Run server: python manage.py runserver

Open http://127.0.0.1:8000/ and sign up (confirm via email OTP in dev SMTP logs)

Notes: currently configured for local development (localhost + SQLite). For production, switch to PostgreSQL, configure a production SMTP service, and host the app behind HTTPS.

Research & evaluation

Comparative gap analysis against Passbolt, Bitwarden, LastPass, etc., informed feature choices (security kit, trusted devices, sign-in monitoring).

Evaluation included functional test cases for 2FA, breach scanning, password storage/encryption, and password sharing — all tested successfully in controlled scenarios.

Roadmap / future work

Deploy to cloud with managed DB and hardened server config (AWS/GCP/Azure).

Add password-less authentication, dark/web monitoring, and optional enterprise SSO integration.

Harden crypto key lifecycle management using HSM/KMS for production.
