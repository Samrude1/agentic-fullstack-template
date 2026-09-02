# Security Audit & Vulnerability Report (SECURITY_AUDIT.md)

This document tracks security assessments, vulnerability scans, OWASP Top 10 compliance audits, and remediation steps. Update this file whenever running `/security` (`app-security`).

---

## 1. Security Scorecard & Health Summary

| Category | Status | Assessment |
| :--- | :--- | :--- |
| **Authentication & Session Security** | ⬜ Pending | Token storage, cookie flags (`httpOnly`, `secure`, `sameSite`) |
| **Authorization & Access Control** | ⬜ Pending | Route middleware, object-level permissions |
| **Injection Defense** | ⬜ Pending | Parameterized SQL/ORM queries, input sanitization |
| **XSS & Content Security** | ⬜ Pending | Output escaping, CSP headers, dangerouslySetInnerHTML checks |
| **CSRF Protection** | ⬜ Pending | CSRF tokens / SameSite cookie enforcement |
| **Secrets & Credentials** | ⬜ Pending | Git leak detection, `.env` file management |
| **Dependency Vulnerabilities** | ⬜ Pending | `npm audit` / dependency CVE scan |
| **CORS & Network Policy** | ⬜ Pending | Allowed origins, methods, headers |

*Status Legend: 🟩 Passed / Secure | 🟨 Warning / Action Needed | 🟥 Critical Vulnerability | ⬜ Pending Audit*

---

## 2. Vulnerability Log

| Date | Severity | Component | Description | Remediation | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| — | — | — | — | — | — |

---

## 3. Dependency Audit Summary
*Run `/security` to execute `npm audit` and parse vulnerabilities.*

---

## 4. Hardcoded Secrets Scan
*Run `/security` to check for leaked API keys, tokens, or credentials in source code.*
