# Von Neumann Model

Aliases: stored-program model, mô hình Von Neumann

Type: Computer Foundation

## Context / Ngữ cảnh

Von Neumann Model xuất hiện khi cần hiểu máy tính hiện đại chạy chương trình lưu trong memory như data.

## Boundary / Ranh giới

### Nó là gì

Von Neumann Model là mô hình máy tính có CPU, memory, input/output và chương trình được lưu trong memory.

### Nó không phải là gì

Nó không mô tả hết cache, pipeline, parallelism hoặc kiến trúc CPU hiện đại.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là fetch-decode-execute: CPU đọc instruction từ memory và thao tác data qua memory.

## Project Role / Vai trò trong dự án

Node này giúp nối instruction, CPU, memory, runtime và OS khi debug behavior thấp tầng.

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

- [[Instruction Set]] vì instruction là đơn vị CPU thực thi
- [[Memory Model]] vì chương trình và data cùng sống trên memory abstraction

## Liên quan rộng

- Computer architecture
- Machine organization

## Source trace

- Computer Foundations Map Ch01
