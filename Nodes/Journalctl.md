# Journalctl

Aliases: Journalctl, journalctl, systemd journal, xem log systemd

Type: Linux / Server Admin

## Context / Ngữ cảnh

Journalctl xuất hiện khi vận hành Linux/server cần hiểu command đọc systemd journal để debug service và boot logs.

## Boundary / Ranh giới

### Nó là gì

Journalctl là khái niệm thực hành giúp đọc, cấu hình, debug hoặc bảo vệ Linux server đúng layer.

### Nó không phải là gì

Nó không phải lệnh cần học thuộc máy móc; giá trị chính là hiểu boundary, signal và failure mode khi hệ thống chạy thật.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định command đọc systemd journal để debug service và boot logs, command/config nào quan sát hoặc thay đổi nó, và impact nằm ở process, file, network hay security boundary.

## Project Role / Vai trò trong dự án

Journalctl giúp developer/operator deploy, debug incident, đọc log, quản lý quyền và giữ server ổn định hơn.

## Output / Artifact nên có

- Command hoặc config liên quan tới Journalctl
- Runbook/debug note khi concept này nằm trên production path
- Metric/log/checklist nếu behavior ảnh hưởng availability hoặc security

## Decision Checklist / Câu hỏi kiểm tra

- Journalctl ảnh hưởng process, filesystem, network hay security boundary?
- Có command nào kiểm tra trạng thái hiện tại trước khi sửa không?
- Nếu thay đổi config/service, rollback hoặc restart path là gì?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Journalctl làm sửa nhầm layer hoặc restart sai service
- Thiếu log/metric khiến sự cố Linux phải đoán thay vì quan sát
- Cấu hình quyền hoặc network sai có thể gây downtime hoặc lộ access

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Journalctl nếu chỉ chạy local đơn giản và chưa vận hành server thật
- Dễ over-engineer nếu thêm hardening/tool phức tạp trước khi hiểu risk và recovery path

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Systemd]] vì liên quan trực tiếp tới cách dùng hoặc debug Journalctl
- [[Logging]] vì liên quan trực tiếp tới cách dùng hoặc debug Journalctl

## Liên quan rộng

- Linux operations
- Server administration
- Production debugging

## Keywords / Từ khóa tìm kiếm

- Journalctl
- journalctl
- systemd journal
- xem log systemd

## Source trace

- Linux man-pages project
- The Linux Documentation Project
- systemd documentation
- Debian Administrator's Handbook
