# Copy Semantics

Aliases: Copy Semantics, copy behavior

Type: Programming Languages Deep

## Context / Ngữ cảnh

Copy Semantics xuất hiện khi cần hiểu việc gán, truyền tham số, clone object hoặc return value tạo bản sao mới hay chỉ chia sẻ reference/ownership.

## Boundary / Ranh giới

### Nó là gì

Copy Semantics là rule của ngôn ngữ/runtime về việc một value/object được copy như thế nào: shallow copy, deep copy, move, clone hoặc reference sharing.

### Nó không phải là gì

Copy Semantics không chỉ là syntax `=`. Cùng một cú pháp có thể copy value, copy reference, move ownership hoặc trigger custom copy tùy ngôn ngữ/type.

## Core Mechanism / Cơ chế lõi

Khi value được assign/pass/return, runtime/compiler áp rule theo type và language semantics. Primitive/value type có thể copy dữ liệu trực tiếp; object/reference type có thể copy pointer/reference; một số ngôn ngữ có move/clone rõ.

## Project Role / Vai trò trong dự án

Dùng node này khi debug mutation ngoài ý muốn, performance do copy lớn, ownership/lifetime, data race hoặc bug vì object bị share thay vì clone.

## Output / Artifact nên có

- Value/reference ownership note
- Shallow vs deep copy decision
- Mutation side effect test
- Performance note cho copy lớn
- API contract: copy, clone, borrow hay move

## Decision Checklist / Câu hỏi kiểm tra

- Operation này copy data hay copy reference?
- Mutation ở bản copy có ảnh hưởng object gốc không?
- Copy này shallow hay deep?
- Object lớn có bị copy nhiều lần không?
- API có nói rõ caller sở hữu gì không?

## Failure Modes / Cách nó gây lỗi

- Tưởng copy độc lập nhưng thực tế share nested object.
- Deep copy quá nhiều gây performance cost.
- Move/copy ownership hiểu sai làm object không còn dùng được.
- Mutable object bị share qua nhiều module.
- Clone thiếu field hoặc copy resource handle sai.

## Khi nào chưa cần hoặc dễ over-engineer

- Code chỉ dùng immutable primitive đơn giản thường chưa cần đào sâu.
- Không nên clone/deep copy mọi thứ để né hiểu ownership vì dễ tốn memory/time.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Memory Management]] vì copy ảnh hưởng ownership, allocation và lifetime.
- [[Ownership]] vì copy/move/borrow liên quan cách value được sở hữu.
- [[Runtime]] vì runtime/language quyết định behavior object/reference.
- [[Performance Optimization]] vì copy lớn có thể thành bottleneck.

## Liên quan rộng

- Shallow copy
- Deep copy
- Move semantics
- Reference sharing

## Keywords / Từ khóa tìm kiếm

- Copy Semantics
- copy behavior
- shallow copy
- deep copy
- move semantics
- clone
- reference sharing
- copy semantics debugging

## Source trace

- Types and Programming Languages
- Rust documentation
- C++ reference documentation
