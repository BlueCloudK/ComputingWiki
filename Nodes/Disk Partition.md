# Disk Partition

Aliases: Disk Partition, partition, disk partition, phân vùng ổ đĩa

Type: Linux / Server Admin

## Context / Ngữ cảnh

Disk Partition xuất hiện khi vận hành Linux/server cần hiểu phần chia logic của disk dùng để tạo filesystem hoặc volume.

## Boundary / Ranh giới

### Nó là gì

Disk Partition là khái niệm thực hành giúp đọc, cấu hình, debug hoặc bảo vệ Linux server đúng layer.

### Nó không phải là gì

Nó không phải lệnh cần học thuộc máy móc; giá trị chính là hiểu boundary, signal và failure mode khi hệ thống chạy thật.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định phần chia logic của disk dùng để tạo filesystem hoặc volume, command/config nào quan sát hoặc thay đổi nó, và impact nằm ở process, file, network hay security boundary.

## Project Role / Vai trò trong dự án

Disk Partition giúp developer/operator deploy, debug incident, đọc log, quản lý quyền và giữ server ổn định hơn.

## Output / Artifact nên có

- Command hoặc config liên quan tới Disk Partition
- Runbook/debug note khi concept này nằm trên production path
- Metric/log/checklist nếu behavior ảnh hưởng availability hoặc security

## Decision Checklist / Câu hỏi kiểm tra

- Disk Partition ảnh hưởng process, filesystem, network hay security boundary?
- Có command nào kiểm tra trạng thái hiện tại trước khi sửa không?
- Nếu thay đổi config/service, rollback hoặc restart path là gì?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Disk Partition làm sửa nhầm layer hoặc restart sai service
- Thiếu log/metric khiến sự cố Linux phải đoán thay vì quan sát
- Cấu hình quyền hoặc network sai có thể gây downtime hoặc lộ access

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Disk Partition nếu chỉ chạy local đơn giản và chưa vận hành server thật
- Dễ over-engineer nếu thêm hardening/tool phức tạp trước khi hiểu risk và recovery path

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Block Device]] vì liên quan trực tiếp tới cách dùng hoặc debug Disk Partition
- [[Filesystem Mount]] vì liên quan trực tiếp tới cách dùng hoặc debug Disk Partition

## Liên quan rộng

- Linux operations
- Server administration
- Production debugging

## Keywords / Từ khóa tìm kiếm

- Disk Partition
- partition
- disk partition
- phân vùng ổ đĩa
- disk

## Source trace

- Linux man-pages project
- The Linux Documentation Project
- systemd documentation
- Debian Administrator's Handbook
