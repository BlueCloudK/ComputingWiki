# Computer Organization

Aliases: computer organization and architecture, tổ chức máy tính

Type: Architecture / System Design

## Context / Ngữ cảnh

Computer Organization xuất hiện ở mức system: component, service, boundary, dependency, deployment shape hoặc failure mode. Nó thường liên quan tới maintainability, scalability và ownership.

## Boundary / Ranh giới

### Nó là gì

Computer Organization là quyết định về cấu trúc và ranh giới hệ thống: phần nào sở hữu dữ liệu, phần nào gọi phần nào, và hệ thống chịu lỗi/tăng tải ra sao.

### Nó không phải là gì

Nó không chỉ là diagram; diagram chỉ là artifact để nói về quyết định architecture.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là boundary + dependency + trade-off. Mỗi boundary tạo ownership và interface; mỗi dependency tạo coupling và failure path; mỗi trade-off đổi simplicity lấy scalability hoặc ngược lại.

## Project Role / Vai trò trong dự án

Computer Organization là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

## Output / Artifact nên có

- Architecture decision record hoặc diagram có boundary rõ
- Danh sách dependency, owner và failure mode chính
- Trade-off note về scalability, maintainability, cost và complexity

## Decision Checklist / Câu hỏi kiểm tra

- Boundary giữa component/service đã rõ chưa?
- Dependency nào là bắt buộc, dependency nào có thể đảo chiều?
- Failure của phần này lan sang phần nào?
- Thiết kế này scale bằng cách nào và tốn cost gì?
- Có cách đơn giản hơn đủ dùng cho giai đoạn hiện tại không?

## Failure Modes / Cách nó gây lỗi

- Boundary sai làm team ownership và data ownership rối
- Coupling cao khiến một thay đổi kéo theo nhiều service
- Không nghĩ failure mode nên incident khó khoanh vùng
- Thiết kế quá lớn so với nhu cầu hiện tại

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách service/layer phức tạp khi một module đơn giản đủ kiểm soát
- Dễ over-engineer nếu tối ưu scalability chưa có traffic hoặc team vận hành tương ứng

## Gồm những gì

- [[Computer Organization and Architecture]]
- [[Computer Components]]
- [[CPU]]
- [[Processor]]
- [[Memory System]]
- [[Cache]]
- [[Cache Memory]]
- [[Input Output]]
- [[Instruction Set]]
- [[Computer Performance]]
- [[Embedded Systems]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- System design
- Backend
- Operations
- Technical decision

## Source trace

- Computer Organization Map
- Computer Foundations Map
