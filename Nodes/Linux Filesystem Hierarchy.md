# Linux Filesystem Hierarchy

Aliases: Linux Filesystem Hierarchy, FHS, filesystem hierarchy, cây thư mục Linux

Type: Linux / Server Admin

## Context / Ngữ cảnh

Linux Filesystem Hierarchy xuất hiện khi vận hành Linux/server cần hiểu quy ước thư mục như bin, etc, var, home, proc, sys trên Linux.

## Boundary / Ranh giới

### Nó là gì

Linux Filesystem Hierarchy là khái niệm thực hành giúp đọc, cấu hình, debug hoặc bảo vệ Linux server đúng layer.

### Nó không phải là gì

Nó không phải lệnh cần học thuộc máy móc; giá trị chính là hiểu boundary, signal và failure mode khi hệ thống chạy thật.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định quy ước thư mục như bin, etc, var, home, proc, sys trên Linux, command/config nào quan sát hoặc thay đổi nó, và impact nằm ở process, file, network hay security boundary.

## Project Role / Vai trò trong dự án

Linux Filesystem Hierarchy giúp developer/operator deploy, debug incident, đọc log, quản lý quyền và giữ server ổn định hơn.

## Output / Artifact nên có

- Command hoặc config liên quan tới Linux Filesystem Hierarchy
- Runbook/debug note khi concept này nằm trên production path
- Metric/log/checklist nếu behavior ảnh hưởng availability hoặc security

## Decision Checklist / Câu hỏi kiểm tra

- Linux Filesystem Hierarchy ảnh hưởng process, filesystem, network hay security boundary?
- Có command nào kiểm tra trạng thái hiện tại trước khi sửa không?
- Nếu thay đổi config/service, rollback hoặc restart path là gì?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Linux Filesystem Hierarchy làm sửa nhầm layer hoặc restart sai service
- Thiếu log/metric khiến sự cố Linux phải đoán thay vì quan sát
- Cấu hình quyền hoặc network sai có thể gây downtime hoặc lộ access

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Linux Filesystem Hierarchy nếu chỉ chạy local đơn giản và chưa vận hành server thật
- Dễ over-engineer nếu thêm hardening/tool phức tạp trước khi hiểu risk và recovery path

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[File System]] vì liên quan trực tiếp tới cách dùng hoặc debug Linux Filesystem Hierarchy
- [[Root Directory]] vì liên quan trực tiếp tới cách dùng hoặc debug Linux Filesystem Hierarchy

## Liên quan rộng

- Linux operations
- Server administration
- Production debugging

## Keywords / Từ khóa tìm kiếm

- Linux Filesystem Hierarchy
- FHS
- filesystem hierarchy
- cây thư mục Linux
- linux
- filesystem
- hierarchy

## Source trace

- Linux man-pages project
- The Linux Documentation Project
- systemd documentation
- Debian Administrator's Handbook
