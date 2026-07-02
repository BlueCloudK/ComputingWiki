# OWASP Map

## Source Info

- Source: `https://owasp.org/www-project-cheat-sheets/`
- Version: link-only
- Type: Application security cheat sheet collection
- Use for: security node coverage

## Extracted Knowledge Tree

- [[Application Security]] - practices for protecting applications and data from abuse. `area` `source: OWASP Cheat Sheet Series`
  - [[Authentication]] - verifying user or system identity. `practice/concept` `source: Authentication Cheat Sheet`
  - [[Authorization]] - deciding what an authenticated actor may do. `practice/concept` `source: Authorization guidance`
  - [[Session Management]] - securely maintaining user sessions. `practice` `source: Session Management Cheat Sheet`
  - [[Input Validation]] - checking input shape, type, range, and rules. `practice` `source: Input Validation Cheat Sheet`
  - [[Output Encoding]] - encoding output to prevent injection into interpreters. `practice` `source: XSS Prevention Cheat Sheet`
  - [[XSS]] - injection of script into web pages viewed by users. `vulnerability` `source: XSS Prevention Cheat Sheet`
  - [[SQL Injection]] - injection into SQL queries. `vulnerability` `source: SQL Injection Prevention Cheat Sheet`
  - [[CSRF]] - forcing an authenticated browser to send unwanted requests. `vulnerability` `source: CSRF Prevention Cheat Sheet`
  - [[File Upload Security]] - controlling risk from uploaded files. `practice` `source: File Upload Cheat Sheet`
  - [[Password Storage]] - safely storing password verifiers. `practice` `source: Password Storage Cheat Sheet`
  - [[Secrets Management]] - protecting tokens, keys, and sensitive config. `practice` `source: Secrets Management Cheat Sheet`
  - [[API Security]] - security controls for APIs. `area` `source: REST/API Security guidance`
  - [[Logging Security]] - logging security events without leaking sensitive data. `practice` `source: Logging Cheat Sheet`
  - [[Transport Layer Protection]] - protecting data in transit. `practice` `source: Transport Layer Protection Cheat Sheet`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Security]] | [[Application Security]] | MOC | application protection concerns | OWASP series | MOC |
| [[Authentication]] | [[Application Security]] | practice/concept | verify identity | Authentication CS | existing node |
| [[Authorization]] | [[Application Security]] | practice/concept | check permission | OWASP access control/authz guidance | existing node |
| [[Input Validation]] | [[Application Security]] | practice | validate untrusted input | Input Validation CS | existing node |
| [[XSS]] | [[Application Security]] | vulnerability | script injection in web context | XSS Prevention CS | candidate node |
| [[SQL Injection]] | [[Application Security]] | vulnerability | malicious SQL manipulation | SQL Injection Prevention CS | candidate node |
| [[Secret]] | [[Secrets Management]] | asset/concept | sensitive token/key/password | Secrets Management CS | existing node |
| [[API Security]] | [[Application Security]] | area | securing API surface | REST/API guidance | candidate node |

## Notes

- Link-only; clone/source local later if security map needs more precision.
