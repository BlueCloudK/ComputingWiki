# Cache Stampede

Aliases: cache miss storm, stampede cache

Type: Failure Pattern

## Context / Ngữ cảnh

Cache Stampede xuất hiện khi nhiều request cùng miss cache và cùng tính/gọi backend cho một key nóng.

## Boundary / Ranh giới

### Nó là gì

Cache Stampede là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Cache Stampede là hot key, TTL alignment, request coalescing, lock và stale-while-revalidate.

## Project Role / Vai trò trong dự án

Cache Stampede giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Cache Stampede decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Cache Stampede
- Failure note ghi rõ Cache Stampede ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Cache Stampede đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Cache Stampede không?
- Khi Cache Stampede fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Cache Stampede làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Cache Stampede nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Cache Stampede nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Cache Stampede trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Cache Stampede
- cache miss storm
- stampede cache
- cache stampede debugging
- cache stampede design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Caching pattern references; Cloudflare docs
