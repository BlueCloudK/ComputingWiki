# Security Attack Patterns

Aliases: application security attacks, web security attack patterns, mẫu tấn công bảo mật

Type: MOC

## Context / Ngữ cảnh

Security Attack Patterns là vùng điều hướng cho các attack path, control và failure mode bảo mật thường gặp trong web, API, cloud và software supply chain.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC dùng để review phòng thủ: nhận diện attack pattern, asset bị ảnh hưởng, boundary bị vượt và control cần có.

### Nó không phải là gì

Nó không phải bộ hướng dẫn khai thác. Nội dung chỉ dùng cho threat modeling, secure design, testing và incident readiness.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đi từ asset, entry point, trust boundary, attack path, mitigation, logging và regression test.

## Project Role / Vai trò trong dự án

MOC này giúp nối Security Path với API, backend, cloud, Linux, dependency và monitoring khi làm project thật.

## Output / Artifact nên có

- Threat model notes
- Security review checklist
- Abuse cases
- Regression tests
- Detection and response notes

## Decision Checklist / Câu hỏi kiểm tra

- Attack pattern này chạm asset nào?
- Control nằm ở frontend, backend, data, infra hay process?
- Nếu control fail thì log/alert nào phát hiện được?

## Failure Modes / Cách nó gây lỗi

- Xem security như checklist chung nên bỏ sót attack path cụ thể
- Link attack rộng không nối được với control/test/runbook
- Thiếu source trace làm node trở thành lời khuyên mơ hồ

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần đào sâu mọi attack cho prototype nội bộ không có dữ liệu nhạy
- Dễ over-engineer nếu thêm tool scan trước khi biết asset và boundary

## Gồm những gì

- [[Broken Access Control]]
- [[Privilege Escalation]]
- [[Horizontal Privilege Escalation]]
- [[Vertical Privilege Escalation]]
- [[Forced Browsing]]
- [[Mass Assignment]]
- [[Parameter Tampering]]
- [[Business Logic Abuse]]
- [[Race Condition Attack]]
- [[TOCTOU]]
- [[Authentication Bypass]]
- [[Credential Stuffing]]
- [[Password Spraying]]
- [[Brute Force Attack]]
- [[MFA Bypass]]
- [[Session Hijacking]]
- [[Session Replay]]
- [[Replay Attack]]
- [[Nonce]]
- [[Token Leakage]]
- [[JWT Confusion]]
- [[JWT Expiration]]
- [[Insecure Direct Object Reference]]
- [[Cross Site Scripting]]
- [[HTML Injection]]
- [[JavaScript Injection]]
- [[Template Injection]]
- [[Server Side Template Injection]]
- [[Client Side Template Injection]]
- [[SQL Injection Blind]]
- [[NoSQL Injection]]
- [[LDAP Injection]]
- [[XPath Injection]]
- [[Command Execution]]
- [[OS Command Injection]]
- [[Code Injection]]
- [[Eval Injection]]
- [[File Inclusion]]
- [[Local File Inclusion]]
- [[Remote File Inclusion]]
- [[Directory Traversal]]
- [[Arbitrary File Read]]
- [[Arbitrary File Write]]
- [[Unrestricted File Upload]]
- [[Malicious File Upload]]
- [[MIME Sniffing]]
- [[Content Type Validation]]
- [[Open Redirect]]
- [[Phishing]]
- [[Social Engineering]]
- [[Security Awareness]]
- [[Clickjacking Protection]]
- [[CSP Bypass]]
- [[Cross Origin Data Leak]]
- [[XS Leak]]
- [[CORS Preflight]]
- [[CSRF SameSite Defense]]
- [[SSRF Metadata Access]]
- [[SSRF Egress Control]]
- [[URL Validation]]
- [[DNS Rebinding]]
- [[Deserialization Gadget]]
- [[Object Injection]]
- [[Prototype Pollution]]
- [[Regular Expression Denial of Service]]
- [[Denial of Service]]
- [[Distributed Denial of Service]]
- [[Resource Exhaustion Attack]]
- [[Rate Limit Bypass]]
- [[Bot Abuse]]
- [[Scraping Abuse]]
- [[Spam Abuse]]
- [[Abuse Monitoring]]
- [[Security Alert Triage]]
- [[Indicator of Compromise]]
- [[Compromise Assessment]]
- [[Containment]]
- [[Eradication]]
- [[Recovery]]
- [[Secret Scanning]]
- [[Hardcoded Secret]]
- [[Secret Exposure]]
- [[Key Rotation]]
- [[Certificate Rotation]]
- [[Certificate Pinning]]
- [[TLS Misconfiguration]]
- [[Man in the Middle]]
- [[Downgrade Attack]]
- [[Dependency Confusion]]
- [[Typosquatting Package]]
- [[Malicious Dependency]]
- [[Transitive Dependency Risk]]
- [[Vulnerable Dependency]]
- [[Build Pipeline Compromise]]
- [[Artifact Integrity]]
- [[Provenance]]
- [[Container Image Scanning]]
- [[Container Escape]]
- [[Privileged Container]]
- [[Kubernetes Misconfiguration]]
- [[Kubernetes Secret Exposure]]
- [[RBAC Misconfiguration]]
- [[Public Bucket Exposure]]
- [[Cloud IAM Misconfiguration]]
- [[Metadata Service Exposure]]
- [[Network Segmentation]]
- [[Lateral Movement]]
- [[Persistence]]
- [[Defense in Depth]]
- [[Secure by Default]]
- [[Fail Secure]]
- [[Security Regression]]
- [[Abuse Case]]
- [[Trust Boundary]]
- [[Entry Point]]
- [[Asset Inventory]]
- [[Threat Actor]]
- [[Mitigation]]
- [[Security Requirement]]
- [[Threat Model Review]]

## Nối mạnh

- [[Threat Modeling]] vì threat model cần attack path và mitigation
- [[API Security]] vì nhiều attack đi qua API boundary

## Liên quan rộng

- Security vì attack patterns là phần thực hành của application security
- Linux and Server Admin vì server/infra misconfig mở rộng attack surface
- Web security
- API security
- Cloud security
- Supply chain security

## Keywords / Từ khóa tìm kiếm

- Security Attack Patterns
- OWASP
- application security attacks
- web security
- API attack
- threat modeling
- abuse case
- secure design
- mẫu tấn công bảo mật
- bảo mật ứng dụng

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
