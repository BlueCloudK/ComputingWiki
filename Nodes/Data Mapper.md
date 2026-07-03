# Data Mapper

Aliases: data mapper pattern, mẫu data mapper

Type: Code Design / Pattern

## Bản chất

Data Mapper là cách tổ chức responsibility, dependency hoặc variation trong code. Nó chỉ có giá trị khi làm code dễ đổi, dễ test hoặc giảm coupling; nếu dùng vì tên pattern nghe hay thì thường làm code khó đọc hơn. Nó nối với nhóm quyết định quanh data mapper.

## Dùng trong dự án để làm gì

Data Mapper ảnh hưởng tới module boundary, interface, testability và nơi đặt business logic. Trong dự án, nó giúp xử lý code đang phình, trùng logic hoặc phụ thuộc chéo giữa layer/object.

## Khi nào cần quan tâm

- Một class/module có quá nhiều trách nhiệm
- Logic bị duplicate giữa nhiều handler/service
- Dependency làm unit test khó viết hoặc mock quá nặng
- Có nhiều biến thể behavior cần thay đổi độc lập

## Output / artifact nên có

- Design decision ngắn ghi pattern/responsibility được chọn
- Interface hoặc module boundary rõ input/output
- Refactor checklist và test regression cho behavior cũ

## Checklist kiểm tra

- Pattern này giải quyết coupling/duplication cụ thể nào?
- Responsibility mới nằm đúng layer chưa?
- Interface có đủ nhỏ và dễ test không?
- Có làm tăng indirection quá mức không?
- Regression test có giữ behavior cũ không?

## Lỗi / rủi ro thường gặp

- Áp pattern máy móc làm code nhiều lớp hơn nhưng không rõ hơn
- Business rule bị giấu sai layer
- Interface quá chung gây leak abstraction
- Refactor thiếu test làm đổi behavior ngoài ý muốn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần pattern khi logic đơn giản và chưa có biến thể thật
- Dễ over-engineer nếu tạo abstraction trước khi thấy duplication hoặc volatility

## Gồm những gì

- Chưa tách nhánh

## Liên quan

- Chưa liên kết thêm

## Source trace

- Fowler Pattern Map / PEAA
