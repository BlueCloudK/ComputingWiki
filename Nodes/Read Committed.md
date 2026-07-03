# Read Committed

Aliases: read committed isolation, cô lập read committed

Type: Database Systems

## Context / Ngữ cảnh

Read Committed xuất hiện khi query chỉ nên đọc dữ liệu đã commit tại thời điểm statement chạy.

## Boundary / Ranh giới

### Nó là gì

Read Committed là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Read Committed là statement snapshot, committed data visibility và anomaly còn có thể xảy ra.

## Project Role / Vai trò trong dự án

Read Committed giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Read Committed decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Read Committed
- Failure note ghi rõ Read Committed ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Read Committed đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Read Committed không?
- Khi Read Committed fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Read Committed làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Read Committed nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Read Committed nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Read Committed trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Read Committed
- read committed isolation
- cô lập read committed
- read committed debugging
- read committed design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL transaction isolation docs
