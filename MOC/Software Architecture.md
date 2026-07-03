# Software Architecture

Aliases: architecture, architectural design, kiến trúc phần mềm

Type: Architecture / System Design

## Bản chất

Software Architecture là vùng quyết định boundary, component, dependency, data ownership và failure mode của hệ thống. Nó không chỉ là diagram; nó quyết định hệ thống scale, deploy, debug và maintain như thế nào khi dự án lớn dần.

## Dùng trong dự án để làm gì

Software Architecture là MOC để đi tới các node phục vụ architecture decision, C4 diagram, quality attribute và trade-off. Khi một thay đổi ảnh hưởng nhiều phần, dùng trang này để kiểm tra boundary, dependency và rủi ro trước khi code.

## Khi nào cần quan tâm

- Một thay đổi ảnh hưởng nhiều module/service/database
- Team cần chốt boundary hoặc ownership
- Có failure mode, scalability hoặc maintainability risk
- Cần giải thích architecture cho review/onboarding

## Output / artifact nên có

- Architecture decision record hoặc diagram có boundary rõ
- Danh sách dependency, owner và failure mode chính
- Trade-off note về scalability, maintainability, cost và complexity

## Checklist kiểm tra

- Boundary giữa component/service đã rõ chưa?
- Dependency nào là bắt buộc, dependency nào có thể đảo chiều?
- Failure của phần này lan sang phần nào?
- Thiết kế này scale bằng cách nào và tốn cost gì?
- Có cách đơn giản hơn đủ dùng cho giai đoạn hiện tại không?

## Lỗi / rủi ro thường gặp

- Boundary sai làm team ownership và data ownership rối
- Coupling cao khiến một thay đổi kéo theo nhiều service
- Không nghĩ failure mode nên incident khó khoanh vùng
- Thiết kế quá lớn so với nhu cầu hiện tại

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách service/layer phức tạp khi một module đơn giản đủ kiểm soát
- Dễ over-engineer nếu tối ưu scalability chưa có traffic hoặc team vận hành tương ứng

## Gồm những gì

- [[Architectural Design]]
- [[Software Architecture Concept]]
- [[Quality Attribute]]
- [[Architecture Pattern]]
- [[Subsystem Architecture]]
- [[Object-Oriented Architecture]]
- [[Client Server Architecture]]
- [[Service Oriented Architecture]]
- [[Component Based Architecture]]
- [[C4 Model]]
- [[Architecture Diagram]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- SWEBOK Map
- Software Modeling and Design Map
- C4 Model Map
