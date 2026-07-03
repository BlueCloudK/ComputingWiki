# Memory Model

Aliases: program memory model, mô hình bộ nhớ

Type: Computer Foundation

## Context / Ngữ cảnh

Memory Model xuất hiện khi cần hiểu value, reference, mutation, sharing và concurrency của chương trình. Nó đặc biệt quan trọng khi bug liên quan state, thread, async hoặc performance.

## Boundary / Ranh giới

### Nó là gì

Memory Model là rule mô tả chương trình nhìn và thao tác memory như thế nào: stack/heap, object/reference, ownership, visibility, ordering hoặc garbage collection.

### Nó không phải là gì

Nó không phải là sơ đồ RAM vật lý, không phải database storage model, và không thay thế memory management của OS dù có liên hệ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định khi nào data được tạo, chia sẻ, thay đổi, giải phóng và nhìn thấy bởi execution context khác. Rule này quyết định class bug như race, leak, dangling reference hoặc stale state.

## Project Role / Vai trò trong dự án

Memory Model giúp debug bug state khó lặp lại và chọn pattern phù hợp cho concurrency/performance. Nó cũng ảnh hưởng cách thiết kế immutable data, ownership và cache.

## Output / Artifact nên có

- Note về ownership, mutability hoặc sharing rule quan trọng
- Guideline cho state/concurrency trong codebase
- Test hoặc review checklist cho race/leak/stale state

## Decision Checklist / Câu hỏi kiểm tra

- Value này được copy, share hay reference?
- Ai sở hữu lifecycle của object/resource?
- Mutation này có visible cho thread/task khác không?
- Memory được giải phóng tự động hay cần cleanup?
- Có invariant nào cần bảo vệ khi state được share không?

## Failure Modes / Cách nó gây lỗi

- Race condition do shared mutable state
- Memory leak vì resource lifecycle không rõ
- Stale data do visibility/order rule bị hiểu sai
- Performance thấp vì copy hoặc allocation không cần thiết

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu code single-thread, state đơn giản và runtime quản lý tốt
- Dễ over-engineer nếu tối ưu allocation khi bottleneck chưa nằm ở memory

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Runtime]] vì runtime thường thực thi memory allocation/collection rule
- [[Operating System]] vì memory cuối cùng chạy trên process/address space của OS
- [[Concurrency]] vì shared memory và ordering là nguồn bug concurrency lớn
- [[Race Condition]] vì race thường bắt nguồn từ memory sharing/mutation không kiểm soát

## Liên quan rộng

- Garbage collection
- Ownership
- Immutability
- Resource lifecycle

## Source trace

- Computer Foundations Map Ch09
- Crafting Interpreters
