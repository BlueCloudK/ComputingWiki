# Architecture Diagrams

Aliases: architecture views, sơ đồ kiến trúc

Type: Artifact / Diagram

## Bản chất

Architecture Diagrams là artifact dùng để nhìn thấy cấu trúc, luồng hoặc quan hệ mà đọc code/tài liệu chữ khó thấy. Giá trị của nó nằm ở việc làm rõ boundary, actor, component, data flow hoặc state chứ không phải vẽ cho đẹp. Nó nối với các phần liên quan như [[Architecture Diagram]], [[C4 Model]], [[System Context Diagram]] và nhóm quyết định quanh architecture diagrams.

## Dùng trong dự án để làm gì

Architecture Diagrams là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

## Khi nào cần quan tâm

- Team giải thích hệ thống bằng lời nhưng mỗi người hiểu một kiểu
- Một thay đổi chạm nhiều component, service, table hoặc actor
- Cần review boundary, data flow, state transition hoặc dependency
- Người mới cần hiểu hệ thống mà đọc code quá lâu

## Output / artifact nên có

- Diagram hoặc artifact có tên version/date và phạm vi rõ
- Legend hoặc note ngắn giải thích ký hiệu quan trọng
- Decision/link tới node liên quan nếu diagram dẫn đến thay đổi thiết kế

## Checklist kiểm tra

- Diagram có nói rõ scope và mức abstraction không?
- Các node/edge quan trọng có khớp hệ thống thật không?
- Có bỏ sót external system, actor, database hoặc failure path không?
- Diagram có còn đúng sau thay đổi gần nhất không?
- Người đọc có biết dùng diagram này để ra quyết định gì không?

## Lỗi / rủi ro thường gặp

- Diagram đẹp nhưng không khớp production/code thật
- Quá nhiều chi tiết làm mất insight chính
- Thiếu boundary làm người đọc hiểu sai trách nhiệm
- Không version nên dùng nhầm diagram cũ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần vẽ riêng nếu thay đổi nhỏ và code đã đủ rõ
- Dễ over-engineer khi vẽ nhiều view nhưng không view nào phục vụ decision cụ thể

## Gồm những gì

- [[Architecture Diagram]]
- [[C4 Model]]
- [[System Context Diagram]]
- [[Container Diagram]]
- [[Component Diagram]]
- [[Code Diagram]]
- [[Supplementary Diagram]]
- [[System Landscape Diagram]]
- [[Dynamic Diagram]]
- [[Deployment Diagram]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- C4 Model Map
