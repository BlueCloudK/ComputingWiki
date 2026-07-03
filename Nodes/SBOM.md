# SBOM

Aliases: SBOM

Type: Security

## Context / Ngữ cảnh

SBOM là node bổ sung cho ComputingWiki về danh sách thành phần phần mềm và dependency trong artifact.

## Boundary / Ranh giới

### Nó là gì

SBOM dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới danh sách thành phần phần mềm và dependency trong artifact.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của SBOM là hiểu boundary, input/output, state và failure mode riêng của danh sách thành phần phần mềm và dependency trong artifact.

## Project Role / Vai trò trong dự án

SBOM giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- SBOM control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi SBOM?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai SBOM sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho SBOM nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Supply Chain Security]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng SBOM

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- SBOM
- software bill of materials
- bảng kê thành phần phần mềm
- sbom

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
