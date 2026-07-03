# POSIX

Aliases: POSIX, Portable Operating System Interface, chuẩn POSIX

Type: Linux / Server Admin

## Context / Ngữ cảnh

POSIX xuất hiện khi vận hành Linux/server cần hiểu chuẩn interface hệ điều hành giúp program/script portable giữa Unix-like systems.

## Boundary / Ranh giới

### Nó là gì

POSIX là khái niệm thực hành giúp đọc, cấu hình, debug hoặc bảo vệ Linux server đúng layer.

### Nó không phải là gì

Nó không phải lệnh cần học thuộc máy móc; giá trị chính là hiểu boundary, signal và failure mode khi hệ thống chạy thật.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định chuẩn interface hệ điều hành giúp program/script portable giữa Unix-like systems, command/config nào quan sát hoặc thay đổi nó, và impact nằm ở process, file, network hay security boundary.

## Project Role / Vai trò trong dự án

POSIX giúp developer/operator deploy, debug incident, đọc log, quản lý quyền và giữ server ổn định hơn.

## Output / Artifact nên có

- Command hoặc config liên quan tới POSIX
- Runbook/debug note khi concept này nằm trên production path
- Metric/log/checklist nếu behavior ảnh hưởng availability hoặc security

## Decision Checklist / Câu hỏi kiểm tra

- POSIX ảnh hưởng process, filesystem, network hay security boundary?
- Có command nào kiểm tra trạng thái hiện tại trước khi sửa không?
- Nếu thay đổi config/service, rollback hoặc restart path là gì?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai POSIX làm sửa nhầm layer hoặc restart sai service
- Thiếu log/metric khiến sự cố Linux phải đoán thay vì quan sát
- Cấu hình quyền hoặc network sai có thể gây downtime hoặc lộ access

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu POSIX nếu chỉ chạy local đơn giản và chưa vận hành server thật
- Dễ over-engineer nếu thêm hardening/tool phức tạp trước khi hiểu risk và recovery path

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Shell]] vì liên quan trực tiếp tới cách dùng hoặc debug POSIX

## Liên quan rộng

- Operating System
- Linux operations
- Server administration
- Production debugging

## Keywords / Từ khóa tìm kiếm

- POSIX
- Portable Operating System Interface
- chuẩn POSIX
- posix

## Source trace

- Linux man-pages project
- The Linux Documentation Project
- systemd documentation
- Debian Administrator's Handbook
