# Turing Model

Aliases: Turing machine, mô hình Turing

Type: Computer Foundation

## Context / Ngữ cảnh

Turing Model xuất hiện khi cần hiểu giới hạn nền tảng của computation: cái gì có thể được tính bằng một quy trình cơ học.

## Boundary / Ranh giới

### Nó là gì

Turing Model là mô hình trừu tượng gồm state, tape, head và rule để mô tả computation từng bước.

### Nó không phải là gì

Nó không phải máy tính vật lý, CPU thật, hay công cụ tối ưu performance ứng dụng.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đọc ký hiệu, ghi ký hiệu, đổi state và di chuyển head theo rule cho tới khi halt hoặc chạy mãi.

## Project Role / Vai trò trong dự án

Node này đặt nền cho programming language, compiler và thuật toán bằng câu hỏi chương trình có thể tính được gì.

## Output / Artifact nên có

- Turing machine sketch: state set, alphabet, tape convention, transition rule
- Computability note: problem is decidable, semi-decidable, or outside this model
- Short warning when a claim about 'can compute' is theoretical rather than practical

## Decision Checklist / Câu hỏi kiểm tra

- Bài toán đang hỏi khả năng tính được hay chỉ hỏi performance/implementation?
- Có mô tả input, state transition và halt condition đủ rõ không?
- Có đang nhầm Turing-complete với usable hoặc efficient không?

## Failure Modes / Cách nó gây lỗi

- Dùng Turing-complete như bằng chứng hệ thống đủ tốt
- Bàn computability cho bug app-level không liên quan
- Bỏ qua halting/non-termination khi nói về chương trình tổng quát

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần khi chỉ debug feature, API hoặc database bình thường
- Dễ over-engineer nếu kéo theory of computation vào mọi quyết định design

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Programming Language]] vì language là cách con người mô tả computation
- [[Compiler]] vì compiler xử lý chương trình trong giới hạn computation

## Liên quan rộng

- Computability
- Theory of computation

## Keywords / Từ khóa tìm kiếm

- Turing Model
- Turing machine
- computation model
- tape machine
- computability
- mô hình Turing

## Source trace

- Computer Foundations Map Ch01
