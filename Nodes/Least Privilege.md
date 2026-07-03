# Least Privilege

Aliases: principle of least privilege, quyền tối thiểu

Type: Security

## Context / Ngữ cảnh

Least Privilege xuất hiện khi user, service hoặc process chỉ nên có quyền cần thiết để làm nhiệm vụ.

## Boundary / Ranh giới

### Nó là gì

Least Privilege là nguyên tắc giới hạn permission ở mức tối thiểu hợp lý.

### Nó không phải là gì

Nó không phải deny mọi thứ bất tiện và không thay thế monitoring/audit.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là scope permission theo role, resource, action và lifetime rồi review định kỳ.

## Project Role / Vai trò trong dự án

Node này giảm blast radius khi account/token/service bị lộ hoặc bug bị khai thác.

## Output / Artifact nên có

- Permission matrix: principal, action, resource
- Role/policy review note
- Temporary access/rotation rule

## Decision Checklist / Câu hỏi kiểm tra

- Principal này thật sự cần action nào?
- Policy có wildcard/resource all không?
- Access có expiry hoặc review định kỳ không?

## Failure Modes / Cách nó gây lỗi

- Admin role dùng cho service thường
- Token quá rộng làm blast radius lớn
- Permission chồng chéo không biết ai có quyền gì

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần policy matrix nặng cho prototype local
- Dễ over-engineer nếu quyền quá vụn khiến vận hành nghẹt mà không giảm risk

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authorization]] vì least privilege là nguyên tắc thiết kế quyền
- [[IAM]] vì cloud IAM cần least privilege rất rõ

## Liên quan rộng

- Access control
- Blast radius

## Source trace

- OWASP Authorization Cheat Sheet
- AWS Well-Architected Security Pillar
