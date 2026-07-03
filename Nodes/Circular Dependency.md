# Circular Dependency

Aliases: dependency cycle, cyclic dependency, vòng phụ thuộc

Type: Code Design / Failure Pattern

## Context / Ngữ cảnh

Circular Dependency xuất hiện khi hai hoặc nhiều module, class, package hoặc service phụ thuộc ngược lại nhau làm boundary thiết kế bị khóa cứng.

## Boundary / Ranh giới

### Nó là gì

Nó là dependency graph có chu trình, khiến thứ tự build, import, khởi tạo hoặc deploy trở nên khó kiểm soát.

### Nó không phải là gì

Nó không phải mọi quan hệ hai chiều trong domain; vấn đề chính là dependency thực thi hoặc compile-time bị vòng.

## Core Mechanism / Cơ chế lõi

Một node A cần B, B lại cần A hoặc chuỗi dài hơn quay về A. Khi runtime hoặc compiler resolve dependency, chu trình này có thể tạo undefined value, init order bug hoặc coupling quá chặt.

## Project Role / Vai trò trong dự án

Node này giúp review kiến trúc module, service layer, package boundary và dependency injection khi code bắt đầu khó test hoặc khó deploy riêng.

## Output / Artifact nên có

- Dependency graph hoặc import graph cho vùng bị lỗi
- Refactor note tách interface, event, mediator hoặc shared abstraction
- Test chứng minh init/build không còn phụ thuộc vòng

## Decision Checklist / Câu hỏi kiểm tra

- Cycle nằm ở import/module, runtime object hay service call?
- Có thể đảo dependency bằng interface hoặc port không?
- Có shared utility/domain concept nào đang bị đặt sai layer không?
- Cycle có làm test hoặc build phải mock quá nhiều không?

## Failure Modes / Cách nó gây lỗi

- Import trả undefined hoặc partial module trong JavaScript/TypeScript
- Dependency injection container không tạo được object graph
- Service gọi vòng nhau làm deploy và ownership mơ hồ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách mạnh nếu dependency chỉ là dữ liệu tĩnh và không gây init/build issue
- Dễ over-engineer nếu tạo abstraction cho mọi import thay vì chỉ xử lý cycle gây đau thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dependency Injection]] vì DI container thường làm cycle lộ rõ lúc khởi tạo
- [[Architecture Pattern]] vì pattern layer/port giúp phá dependency cycle

## Liên quan rộng

- Module design
- Package boundary
- Refactoring
- Testability

## Keywords / Từ khóa tìm kiếm

- Circular Dependency
- dependency cycle
- cyclic dependency
- circular import
- module cycle
- dependency graph
- vòng phụ thuộc
- import vòng

## Source trace

- Martin Fowler / Patterns of Enterprise Application Architecture
- TypeScript and JavaScript module documentation
