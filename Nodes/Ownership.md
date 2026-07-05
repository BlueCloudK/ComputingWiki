# Ownership

Aliases: Ownership, ownership model

Type: Programming Languages Deep

## Context / Ngữ cảnh

Ownership xuất hiện khi cần biết phần code nào chịu trách nhiệm sở hữu, mutate, free, clone hoặc truyền một value/resource qua boundary.

## Boundary / Ranh giới

### Nó là gì

Ownership là mô hình xác định ai sở hữu một value/resource tại một thời điểm, ai được đọc/mutate, và khi nào resource được giải phóng hoặc chuyển giao.

### Nó không phải là gì

Ownership không chỉ là quyền truy cập tên biến. Nó liên quan lifetime, mutation, aliasing, memory/resource safety và API contract.

## Core Mechanism / Cơ chế lõi

Ngôn ngữ/runtime hoặc convention của project quy định value được move, borrow, copy, clone hay share reference. Khi ownership không rõ, mutation và cleanup dễ xảy ra ở sai nơi.

## Project Role / Vai trò trong dự án

Dùng node này khi debug memory/resource leak, data race, mutation ngoài ý muốn, API contract mơ hồ hoặc khi thiết kế boundary giữa module/service/object.

## Output / Artifact nên có

- Owner của resource/value
- Read/mutate permission
- Lifetime/cleanup rule
- Copy/move/borrow/clone decision
- API contract về ownership

## Decision Checklist / Câu hỏi kiểm tra

- Ai sở hữu value/resource này?
- Ai được mutate và ai chỉ được đọc?
- Resource được cleanup ở đâu?
- Khi truyền qua function/module, ownership chuyển hay mượn?
- Có alias nào có thể mutate ngoài ý muốn không?

## Failure Modes / Cách nó gây lỗi

- Nhiều nơi cùng nghĩ mình là owner.
- Không ai chịu cleanup resource.
- Shared mutable state bị mutate ngoài dự kiến.
- Clone/copy quá nhiều để né ownership làm tốn memory/time.
- API không nói rõ caller còn được dùng value sau khi truyền không.

## Khi nào chưa cần hoặc dễ over-engineer

- Code immutable đơn giản có thể chỉ cần convention nhẹ.
- Không nên áp mô hình ownership phức tạp nếu language/runtime đã che phần lớn lifecycle và resource không critical.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Memory Management]] vì ownership quyết định lifetime và cleanup resource.
- [[Copy Semantics]] vì copy/move/clone ảnh hưởng ownership.
- [[Runtime]] vì runtime/language hỗ trợ hoặc giới hạn ownership model.
- [[Memory Leak]] vì ownership mơ hồ thường dẫn tới resource bị giữ quá lâu.

## Liên quan rộng

- Borrowing
- Aliasing
- Lifetime
- Resource ownership

## Keywords / Từ khóa tìm kiếm

- Ownership
- ownership model
- memory ownership
- resource lifetime
- borrow
- move semantics
- shared mutable state
- ownership debugging

## Source trace

- Rust documentation
- Types and Programming Languages
