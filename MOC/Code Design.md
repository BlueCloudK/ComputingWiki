# Code Design

Aliases: software design, detailed design, thiết kế code

Type: Code Design / Pattern

## Bản chất

Code Design là vùng quyết định cách chia trách nhiệm, dependency, interface và pattern trong code. Nó không nhằm làm code trông học thuật hơn; mục tiêu là giảm coupling, giảm duplicate logic, tăng testability và làm refactor ít vỡ hơn.

## Dùng trong dự án để làm gì

Code Design là MOC để tìm các node phục vụ refactor, chọn pattern, đặt boundary trong code và kiểm tra responsibility. Khi code bắt đầu khó đổi hoặc test khó viết, trang này giúp chọn hướng đào sâu thay vì thêm abstraction theo cảm tính.

## Khi nào cần quan tâm

- Code có class/module quá nhiều trách nhiệm
- Logic bị duplicate giữa handler/service/repository
- Dependency làm unit test khó viết hoặc mock quá nặng
- Có nhiều biến thể behavior cần thay đổi độc lập

## Output / artifact nên có

- Design decision ngắn ghi responsibility/pattern được chọn
- Interface hoặc module boundary rõ input/output
- Refactor checklist và regression test cho behavior cũ

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

- [[State Machine]]
- [[Design Pattern]]
- [[Refactor]]
- [[Error Handling]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- SWEBOK Map
- Software Modeling and Design Map
- Design Pattern Map
