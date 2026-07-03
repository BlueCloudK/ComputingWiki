# Software Engineering

Aliases: software engineering body of knowledge, kỹ nghệ phần mềm

Type: Architecture / System Design

## Bản chất

Software Engineering là quyết định ở mức system: boundary, dependency, runtime component, failure mode và trade-off. Nó không chỉ là sơ đồ; nó quyết định phần nào sở hữu dữ liệu, phần nào gọi phần nào, và hệ thống chịu tải/lỗi ra sao. Nó nối với các phần liên quan như [[Requirements]], [[Software Architecture]], [[Code Design]] và nhóm quyết định quanh software engineering.

## Dùng trong dự án để làm gì

Software Engineering là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

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

- [[Requirements]]
- [[Software Architecture]]
- [[Code Design]]
- [[Testing and Verification]]
- [[Security]]
- [[Deployment and Operations]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- SWEBOK Map
- CC2020 Map
