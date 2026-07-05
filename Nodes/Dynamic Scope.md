# Dynamic Scope

Aliases: Dynamic Scope, dynamic scoping

Type: Programming Languages Deep

## Context / Ngữ cảnh

Dynamic Scope xuất hiện khi tên biến/hàm được resolve theo call stack runtime thay vì theo vị trí lexical trong source code.

## Boundary / Ranh giới

### Nó là gì

Dynamic Scope là scoping rule trong đó binding của tên được tìm theo chuỗi caller đang chạy tại runtime.

### Nó không phải là gì

Dynamic Scope không giống lexical/static scope. Lexical scope nhìn vào nơi code được viết; dynamic scope nhìn vào ai gọi ai khi chương trình chạy.

## Core Mechanism / Cơ chế lõi

Khi code cần resolve một name, runtime tìm binding trong activation/call stack hiện tại. Function có thể thấy binding từ caller dù binding đó không nằm trong lexical environment của function.

## Project Role / Vai trò trong dự án

Dùng node này khi học language semantics, debug context implicit, dynamic variable, thread-local/context-local behavior hoặc hiểu vì sao name resolution phụ thuộc call path.

## Output / Artifact nên có

- Scope resolution example
- Call stack example
- Binding lookup rule
- Contrast với lexical scope
- Failure case khi caller thay đổi

## Decision Checklist / Câu hỏi kiểm tra

- Binding được tìm theo source structure hay call stack?
- Function behavior có đổi khi caller đổi không?
- Dynamic binding có thread/context boundary không?
- Có cách truyền dependency tường minh hơn không?
- Test có cover call path khác nhau không?

## Failure Modes / Cách nó gây lỗi

- Function phụ thuộc caller ngầm nên khó reuse.
- Đổi call path làm behavior đổi bất ngờ.
- Dynamic context leak giữa request/task.
- Debug khó vì dependency không hiện trong parameter list.
- Concurrency làm context dynamic bị lẫn nếu implementation yếu.

## Khi nào chưa cần hoặc dễ over-engineer

- Hầu hết app code hiện đại dùng lexical scope; chỉ cần đào sâu khi gặp dynamic/context-local behavior.
- Không nên dùng dynamic scope để che dependency đáng ra nên truyền tường minh.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Runtime]] vì dynamic scope phụ thuộc call stack/runtime context.
- [[Module System]] vì module/name boundary khác với dynamic binding.
- [[Function]] vì function behavior có thể phụ thuộc caller runtime.
- [[Thread Starvation]] vì context-local trong concurrent runtime dễ có failure riêng khi task/thread bị quản lý sai.

## Liên quan rộng

- Name resolution
- Call stack
- Context local
- Lexical scope

## Keywords / Từ khóa tìm kiếm

- Dynamic Scope
- dynamic scoping
- dynamic binding
- lexical scope
- call stack lookup
- context local
- dynamic scope debugging

## Source trace

- Types and Programming Languages
- Crafting Interpreters
