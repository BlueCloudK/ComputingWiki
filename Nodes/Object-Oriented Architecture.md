# Object-Oriented Architecture

Aliases: OO architecture, kiến trúc hướng đối tượng

Type: Artifact / Diagram

## Bản chất

Object-Oriented Architecture là artifact dùng để nhìn thấy cấu trúc, luồng hoặc quan hệ mà đọc code/tài liệu chữ khó thấy. Giá trị của nó nằm ở việc làm rõ boundary, actor, component, data flow hoặc state chứ không phải vẽ cho đẹp. Nó nối với các phần liên quan như [[Object and Class Structuring]], [[Class Diagram]] và nhóm quyết định quanh object-oriented architecture.

## Dùng trong dự án để làm gì

Object-Oriented Architecture giúp team thống nhất hình dung trước khi sửa architecture, API, database hoặc workflow. Nó là output để review quyết định, phát hiện dependency ẩn và onboarding người mới nhanh hơn.

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

- [[Object and Class Structuring]]
- [[Class Diagram]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Software Modeling and Design Map / Ch14
