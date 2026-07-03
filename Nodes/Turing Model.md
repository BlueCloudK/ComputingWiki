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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Programming Language]] vì language là cách con người mô tả computation
- [[Compiler]] vì compiler xử lý chương trình trong giới hạn computation

## Liên quan rộng

- Computability
- Theory of computation

## Source trace

- Computer Foundations Map Ch01
