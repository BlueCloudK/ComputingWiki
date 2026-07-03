# Threat Modeling

Aliases: threat model, mô hình đe dọa

Type: Security

## Context / Ngữ cảnh

Threat Modeling xuất hiện khi cần hiểu attacker có thể lạm dụng hệ thống như thế nào trước khi chọn control.

## Boundary / Ranh giới

### Nó là gì

Threat Modeling là hoạt động xác định asset, actor, entry point, threat và mitigation.

### Nó không phải là gì

Nó không phải checklist security chung chung và không thay thế test/pentest.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là model hệ thống, hỏi cái gì có thể sai, ưu tiên threat theo impact/likelihood và ghi mitigation.

## Project Role / Vai trò trong dự án

Node này giúp security control đặt đúng chỗ thay vì thêm ngẫu nhiên.

## Output / Artifact nên có

- Threat model diagram hoặc table
- Asset list, trust boundary, entry point
- Abuse case và mitigation list

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào cần bảo vệ?
- Trust boundary nằm ở đâu?
- Attacker có capability và goal gì?
- Mitigation nào được test hoặc monitor?

## Failure Modes / Cách nó gây lỗi

- Thiếu asset/trust boundary nên bỏ sót attack path
- Chỉ liệt kê control mà không map threat
- Không update threat model khi architecture/API đổi

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho script nội bộ ít rủi ro
- Dễ over-engineer nếu workshop dài nhưng không tạo mitigation cụ thể

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Security]] vì threat modeling định hướng control security
- [[API Security]] vì API boundary thường là attack surface lớn

## Liên quan rộng

- STRIDE
- Abuse cases

## Keywords / Từ khóa tìm kiếm

- Threat Modeling
- threat model
- mô hình đe dọa
- threat
- modeling
- Security
- mô hình hóa
- bảo mật phần mềm
- kiến trúc hệ thống

## Source trace

- OWASP Threat Modeling
- NIST SSDF
