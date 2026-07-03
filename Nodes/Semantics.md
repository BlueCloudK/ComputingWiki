# Semantics

Aliases: meaning of programs, ngữ nghĩa chương trình

Type: Computer Foundation

## Context / Ngữ cảnh

Semantics xuất hiện khi cần hiểu code thật sự làm gì sau khi đã đúng syntax. Đây là phần phân biệt "code nhìn hợp lệ" với "behavior đúng như mong muốn".

## Boundary / Ranh giới

### Nó là gì

Semantics là nghĩa của construct trong language: expression được evaluate ra sao, scope/name binding hoạt động thế nào, state thay đổi khi nào, error được tạo và lan truyền ra sao.

### Nó không phải là gì

Nó không phải là syntax, không phải style, và không phải ý định của developer nếu behavior thực tế của language khác với ý định đó.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là rule biến construct thành behavior: evaluation order, binding, type rule, mutation, control flow, exception và interaction với runtime.

## Project Role / Vai trò trong dự án

Semantics giúp debug bug tinh vi như scope nhầm, mutation ngoài ý muốn, async behavior, equality rule hoặc exception propagation. Nó cũng giúp review code theo behavior thay vì hình thức.

## Output / Artifact nên có

- Note về language behavior dễ gây bug
- Test case chứng minh edge semantics quan trọng
- Rule team thống nhất khi construct có nghĩa dễ hiểu nhầm

## Decision Checklist / Câu hỏi kiểm tra

- Expression này được evaluate theo thứ tự nào?
- Name này bind tới scope/value nào?
- Operation này mutate hay tạo value mới?
- Error được throw, return hay propagate thế nào?
- Behavior này do language spec hay do runtime/library?

## Failure Modes / Cách nó gây lỗi

- Code đúng syntax nhưng behavior khác ý định
- Nhầm reference/value semantics làm state bị đổi ngoài ý muốn
- Không hiểu evaluation order gây bug side effect
- Dựa vào behavior implementation-specific rồi vỡ khi đổi runtime/version

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần formal semantics nếu code đơn giản và behavior rõ
- Dễ over-engineer nếu mọi review đều biến thành phân tích language theory

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Syntax]] vì syntax là hình dạng, semantics là nghĩa của hình dạng đó
- [[Type System]] vì type rule là một phần quan trọng của meaning và validity
- [[Runtime]] vì một số semantics chỉ bộc lộ khi code chạy
- [[Interpreter]] vì interpreter thường encode trực tiếp semantic rule

## Liên quan rộng

- Language specification
- Program correctness
- Debugging edge cases

## Keywords / Từ khóa tìm kiếm

- Semantics
- meaning of programs
- ngữ nghĩa chương trình
- Computer Foundation
- ngôn ngữ lập trình

## Source trace

- Types and Programming Languages
- Crafting Interpreters
