# GNU Coreutils

Aliases: GNU Coreutils, coreutils, GNU coreutils, lệnh Linux cơ bản

Type: Linux / Server Admin

## Context / Ngữ cảnh

GNU Coreutils xuất hiện khi vận hành Linux/server cần hiểu bộ command cơ bản như ls, cp, mv, cat, sort, chmod trên GNU/Linux.

## Boundary / Ranh giới

### Nó là gì

GNU Coreutils là khái niệm thực hành giúp đọc, cấu hình, debug hoặc bảo vệ Linux server đúng layer.

### Nó không phải là gì

Nó không phải lệnh cần học thuộc máy móc; giá trị chính là hiểu boundary, signal và failure mode khi hệ thống chạy thật.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định bộ command cơ bản như ls, cp, mv, cat, sort, chmod trên GNU/Linux, command/config nào quan sát hoặc thay đổi nó, và impact nằm ở process, file, network hay security boundary.

## Project Role / Vai trò trong dự án

GNU Coreutils giúp developer/operator deploy, debug incident, đọc log, quản lý quyền và giữ server ổn định hơn.

## Output / Artifact nên có

- Command hoặc config liên quan tới GNU Coreutils
- Runbook/debug note khi concept này nằm trên production path
- Metric/log/checklist nếu behavior ảnh hưởng availability hoặc security

## Decision Checklist / Câu hỏi kiểm tra

- GNU Coreutils ảnh hưởng process, filesystem, network hay security boundary?
- Có command nào kiểm tra trạng thái hiện tại trước khi sửa không?
- Nếu thay đổi config/service, rollback hoặc restart path là gì?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai GNU Coreutils làm sửa nhầm layer hoặc restart sai service
- Thiếu log/metric khiến sự cố Linux phải đoán thay vì quan sát
- Cấu hình quyền hoặc network sai có thể gây downtime hoặc lộ access

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu GNU Coreutils nếu chỉ chạy local đơn giản và chưa vận hành server thật
- Dễ over-engineer nếu thêm hardening/tool phức tạp trước khi hiểu risk và recovery path

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Command Line]] vì liên quan trực tiếp tới cách dùng hoặc debug GNU Coreutils
- [[File Permission]] vì liên quan trực tiếp tới cách dùng hoặc debug GNU Coreutils

## Liên quan rộng

- Linux operations
- Server administration
- Production debugging

## Keywords / Từ khóa tìm kiếm

- GNU Coreutils
- coreutils
- GNU coreutils
- lệnh Linux cơ bản

## Source trace

- Linux man-pages project
- The Linux Documentation Project
- systemd documentation
- Debian Administrator's Handbook
