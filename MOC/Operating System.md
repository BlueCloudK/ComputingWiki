# Operating System

Aliases: OS, operating systems, hệ điều hành

Type: Tooling / Implementation Detail

## Context / Ngữ cảnh

Operating System xuất hiện ở tầng implementation hoặc runtime: OS, process, memory, file, environment, tool hoặc platform behavior.

## Boundary / Ranh giới

### Nó là gì

Operating System là chi tiết có thể ảnh hưởng trực tiếp tới cách code chạy trong môi trường thật.

### Nó không phải là gì

Nó không phải abstraction business; nếu dùng sai tầng, team có thể debug nhầm symptom thay vì nguyên nhân.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là behavior của runtime/tool/platform: version, config, resource, scheduling, filesystem hoặc dependency quyết định kết quả thực thi.

## Project Role / Vai trò trong dự án

Operating System là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

## Output / Artifact nên có

- Troubleshooting note hoặc checklist tái hiện lỗi
- Config/runtime decision nếu ảnh hưởng deploy
- Test hoặc script kiểm tra behavior quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Triệu chứng có phụ thuộc environment/runtime không?
- Config/tool/version nào đang ảnh hưởng behavior?
- Có log/metric đủ chứng minh nguyên nhân không?
- Thay đổi implementation này có ảnh hưởng portability không?
- Có cách kiểm tra tự động để tránh regression không?

## Failure Modes / Cách nó gây lỗi

- Fix symptom ở tầng tool nhưng bỏ sót nguyên nhân hệ thống
- Phụ thuộc behavior riêng của environment
- Config/version lệch làm lỗi khó tái hiện
- Tối ưu thấp tầng làm code khó hiểu mà lợi ích nhỏ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu lỗi nằm rõ ở business logic
- Dễ over-engineer nếu tối ưu chi tiết runtime trước khi có metric hoặc bug thật

## Gồm những gì

- [[Operating System Concepts]]
- [[System Call]]
- [[Operating System Structure]]
- [[Process]]
- [[Thread]]
- [[Processes and Threads]]
- [[Interprocess Communication]]
- [[Scheduling]]
- [[Memory Management]]
- [[Virtual Memory]]
- [[File System]]
- [[Deadlock]]
- [[Virtualization]]
- [[Kernel]]
- [[User Mode]]
- [[Kernel Mode]]
- [[Interrupt]]
- [[Paging]]
- [[Process State]]
- [[Context Switch]]
- [[Device Driver]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Runtime behavior
- Developer tooling
- Operating system
- Troubleshooting

## Source trace

- Operating Systems Map
- Computer Foundations Map
