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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

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
