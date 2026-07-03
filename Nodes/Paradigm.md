# Paradigm

Aliases: programming paradigm, mô thức lập trình

Type: Computer Foundation

## Context / Ngữ cảnh

Paradigm xuất hiện khi language hoặc codebase khuyến khích một cách tổ chức suy nghĩ: object, function, data flow, message passing hoặc logic rule. Nó ảnh hưởng cách chia abstraction và đọc code.

## Boundary / Ranh giới

### Nó là gì

Paradigm là phong cách mô hình hóa computation và tổ chức chương trình, ví dụ imperative, object-oriented, functional, declarative hoặc event-driven.

### Nó không phải là gì

Nó không phải là một language cụ thể, không phải design pattern riêng lẻ, và không đảm bảo code tốt nếu áp dụng máy móc.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chọn đơn vị chính để suy nghĩ: state change, object/message, function/composition, rule/query hoặc event. Paradigm định hình abstraction, side effect và flow kiểm soát.

## Project Role / Vai trò trong dự án

Paradigm giúp đọc codebase đúng idiom và tránh thiết kế trái dòng với language/framework. Nó cũng giúp team thống nhất cách module giao tiếp và quản lý state.

## Output / Artifact nên có

- Guideline ngắn về paradigm chính của codebase
- Decision note khi pha trộn nhiều paradigm
- Example nhỏ về cách tổ chức state/behavior theo idiom được chọn

## Decision Checklist / Câu hỏi kiểm tra

- Codebase đang ưu tiên paradigm nào?
- State và side effect được quản lý ở đâu?
- Abstraction này đang theo idiom của language hay chống lại nó?
- Có đang trộn paradigm làm flow khó hiểu không?
- Paradigm này giúp test/refactor dễ hơn hay khó hơn?

## Failure Modes / Cách nó gây lỗi

- Viết OOP giả trong language functional hoặc ngược lại
- Side effect rải rác làm behavior khó đoán
- Áp dụng pattern theo tên nhưng không hợp paradigm
- Team không thống nhất style nên codebase bị nhiều lối suy nghĩ trộn lẫn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tranh luận paradigm cho script nhỏ hoặc module ít state
- Dễ over-engineer nếu ép code đơn giản vào mô hình tư tưởng quá nặng

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Programming Language]] vì nhiều language hỗ trợ hoặc ưu tiên paradigm khác nhau
- [[Semantics]] vì paradigm gắn với cách expression, state và control flow có nghĩa
- [[Design Pattern]] vì pattern thường phụ thuộc paradigm của language/codebase

## Liên quan rộng

- Functional programming
- Object-oriented programming
- Declarative programming
- Event-driven design

## Source trace

- ACM/IEEE Computing Curricula 2020
- Computer Foundations Map Ch09
