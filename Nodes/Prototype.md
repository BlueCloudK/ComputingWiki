# Prototype

Aliases: prototype pattern, mẫu prototype

Type: Code Design / Pattern

## Context / Ngữ cảnh

Prototype xuất hiện trong codebase khi team phải chia trách nhiệm, dependency, interface hoặc biến thể behavior. Nó nằm gần refactor, testability và maintainability.

## Boundary / Ranh giới

### Nó là gì

Prototype là cách tổ chức code để một phần thay đổi không kéo theo quá nhiều phần khác.

### Nó không phải là gì

Nó không phải nhãn pattern để làm code trông chuyên nghiệp; nếu không giảm coupling, duplication hoặc volatility thì nó chỉ thêm indirection.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đặt boundary và responsibility: ai sở hữu logic, ai gọi ai, dependency đi hướng nào, interface nào được expose và behavior nào có thể thay thế.

## Project Role / Vai trò trong dự án

Prototype tạo object mới bằng clone object mẫu, hữu ích khi chi phí khởi tạo hoặc cấu hình ban đầu phức tạp.

## Output / Artifact nên có

- Design decision ngắn ghi responsibility/pattern được chọn
- Interface hoặc module boundary rõ input/output
- Refactor checklist và regression test cho behavior cũ

## Decision Checklist / Câu hỏi kiểm tra

- Pattern này giải quyết coupling/duplication cụ thể nào?
- Responsibility mới nằm đúng layer chưa?
- Interface có đủ nhỏ và dễ test không?
- Có làm tăng indirection quá mức không?
- Regression test có giữ behavior cũ không?

## Failure Modes / Cách nó gây lỗi

- Áp pattern máy móc làm code nhiều lớp hơn nhưng không rõ hơn
- Business rule bị giấu sai layer
- Interface quá chung gây leak abstraction
- Refactor thiếu test làm đổi behavior ngoài ý muốn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần pattern khi logic đơn giản và chưa có biến thể thật
- Dễ over-engineer nếu tạo abstraction trước khi thấy duplication hoặc volatility

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Codebase
- Refactoring
- Unit testing
- Maintainability

## Source trace

- Design Pattern Map / catalog
