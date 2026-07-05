# Bastion Host

Aliases: Bastion Host, jump host

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Bastion Host xuất hiện khi private server/database/cluster không mở trực tiếp ra internet nhưng vẫn cần một điểm truy cập quản trị có kiểm soát.

## Boundary / Ranh giới

### Nó là gì

Bastion Host là máy trung gian được harden và audit để admin/operator SSH hoặc tunnel vào tài nguyên private network.

### Nó không phải là gì

Bastion Host không phải nơi chạy workload application chính. Nó là access boundary cho operations và phải có quyền tối thiểu, logging và lifecycle rõ.

## Core Mechanism / Cơ chế lõi

Operator kết nối tới bastion qua SSH/VPN/SSM theo policy. Từ bastion, họ truy cập resource private qua network route nội bộ. Security rule chỉ cho private resource nhận kết nối từ bastion hoặc access path được phép.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế private subnet access, SSH audit, database admin access, break-glass operation hoặc debug vì sao không vào được server private.

## Output / Artifact nên có

- Bastion access policy
- Allowed source IP/user/group
- Private target list
- SSH/session audit log
- Rotation/patching/hardening checklist

## Decision Checklist / Câu hỏi kiểm tra

- Bastion được phép truy cập resource nào?
- Ai được login và qua cơ chế nào?
- Có MFA/session logging không?
- Bastion có public IP thật sự cần không?
- Key/credential có rotation và revocation không?

## Failure Modes / Cách nó gây lỗi

- Bastion thành điểm single point of compromise.
- Mở SSH quá rộng ra internet.
- Dùng chung key admin không audit được ai làm gì.
- Bastion không patch nên thành cửa vào hệ thống.
- Private resource vẫn mở public nên bastion mất ý nghĩa.

## Khi nào chưa cần hoặc dễ over-engineer

- Hệ thống nhỏ có VPN/managed session access đủ có thể không cần bastion riêng.
- Không nên dùng bastion thay thế IAM, least privilege và audit logging.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Public Subnet]] vì bastion thường nằm ở public subnet hoặc edge access subnet.
- [[Network ACL]] vì ACL/firewall quyết định traffic tới bastion và private target.
- [[Least Privilege]] vì bastion access phải giới hạn tối thiểu.
- [[Secret]] vì SSH key/token cần quản lý như secret.

## Liên quan rộng

- Jump host
- Private subnet access
- SSH hardening

## Keywords / Từ khóa tìm kiếm

- Bastion Host
- jump host
- SSH bastion
- private subnet access
- bastion hardening
- bastion audit
- bastion host debugging

## Source trace

- AWS VPC documentation
- Google Cloud VPC documentation
- Linux server administration references
