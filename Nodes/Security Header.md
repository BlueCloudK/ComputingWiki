# Security Header

Aliases: Security Header, security headers, HTTP security header, header bảo mật

Type: Security

## Context / Ngữ cảnh

Security Header xuất hiện khi web app/API muốn dùng browser-enforced policy để giảm rủi ro XSS, clickjacking, MIME sniffing, insecure transport, referrer leak hoặc cross-origin abuse. Nó thường được set ở reverse proxy, CDN, API gateway, web server hoặc app middleware.

## Boundary / Ranh giới

### Nó là gì

Security Header là HTTP response header yêu cầu browser áp policy bảo mật. Ví dụ gồm `Content-Security-Policy`, `X-Content-Type-Options`, `Strict-Transport-Security`, `Referrer-Policy`, `Permissions-Policy`, `X-Frame-Options` hoặc `Cross-Origin-*` headers tùy nhu cầu.

### Nó không phải là gì

Security Header không thay thế fix gốc như output encoding, authorization, input validation hoặc TLS đúng. Header là guardrail/defense-in-depth. Nếu policy quá lỏng, sai context hoặc chỉ set ở vài route, nó dễ tạo false sense of security.

## Core Mechanism / Cơ chế lõi

Server gửi response header. Browser đọc header và enforce behavior: chặn script source lạ, không sniff MIME, ép HTTPS, giới hạn referrer, chặn iframe, hoặc giới hạn browser feature. Một số header cần rollout bằng report-only trước để tránh làm vỡ frontend hoặc third-party integration.

## Project Role / Vai trò trong dự án

Security Header là node cần mở khi harden frontend/backend, cấu hình Nginx/CDN/API gateway, debug CSP block, mixed content, clickjacking, file download hoặc production security scan. Nó giúp team quyết định header nào cần cho từng route/domain và test browser behavior thật.

## Output / Artifact nên có

- Header policy per app/domain: CSP, HSTS, nosniff, Referrer-Policy, Permissions-Policy
- Rollout plan: report-only, monitor violation, enforce
- Exception list cho third-party script/frame/image/font nếu cần
- Test checklist: header present, route coverage, browser behavior, CDN/proxy override
- Monitoring/report endpoint cho CSP violation nếu dùng

## Decision Checklist / Câu hỏi kiểm tra

- Header này bảo vệ attack path nào?
- Header được set ở app, proxy, CDN hay gateway và có phủ mọi route cần thiết không?
- Policy có quá lỏng như `unsafe-inline`, wildcard source hoặc frame all không?
- Có third-party dependency nào bị chặn khi enforce không?
- HSTS có an toàn để bật dài hạn cho domain/subdomain chưa?
- `nosniff` có được set cho file/script/style path không?
- Có test bằng browser thật sau deploy không?

## Failure Modes / Cách nó gây lỗi

- CSP quá lỏng không giảm XSS impact đáng kể.
- CSP quá chặt làm frontend/analytics/payment script hỏng production.
- Header chỉ set ở HTML route nhưng thiếu ở download/static/API path cần bảo vệ.
- CDN/proxy override hoặc strip header làm local/staging khác production.
- HSTS bật dài hạn khi subdomain chưa sẵn HTTPS, gây outage khó rollback.
- Thiếu `nosniff` cho file upload/download làm MIME sniffing risk tăng.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype local không public có thể bắt đầu header tối thiểu.
- Không nên copy policy từ internet mà không map với asset và frontend dependency thật.
- Không nên xem security header là “đã an toàn” nếu app vẫn có XSS/IDOR/SQLi gốc.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTP]] vì security header là HTTP response header.
- [[CSP]] vì CSP là security header quan trọng chống XSS defense-in-depth.
- [[MIME Sniffing]] vì `nosniff` là header phòng thủ trực tiếp.
- [[HTTPS]] vì HSTS/security transport header phụ thuộc HTTPS đúng.
- [[Reverse Proxy]] vì header thường được set/override ở proxy hoặc CDN.

## Liên quan rộng

- Browser security
- Web hardening
- Defense in depth
- CDN/proxy configuration

## Keywords / Từ khóa tìm kiếm

- Security Header
- security headers
- HTTP security header
- header bảo mật
- Content-Security-Policy
- X-Content-Type-Options
- Strict-Transport-Security
- Referrer-Policy
- Permissions-Policy
- X-Frame-Options
- HSTS
- nosniff
- CSP report only
- security header debugging

## Source trace

- OWASP Secure Headers Project
- MDN Web Docs / HTTP security headers
