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

- Stored-program diagram: CPU, memory, instruction stream, IO
- Fetch-decode-execute note khi giải thích runtime thấp tầng
- Boundary note giữa architecture model và CPU hiện đại có cache/pipeline

## Decision Checklist / Câu hỏi kiểm tra

- Chương trình và data có đang được hiểu là cùng nằm trong memory không?
- Vấn đề này cần model CPU-memory hay chỉ cần OS/runtime abstraction?
- Cache/pipeline/concurrency có làm model đơn giản này không đủ không?

## Failure Modes / Cách nó gây lỗi

- Giải thích performance hiện đại chỉ bằng fetch-decode-execute
- Bỏ qua memory hierarchy khi nói về tốc độ
- Nhầm model nền với layout phần cứng cụ thể

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần cho phần lớn logic backend/frontend
- Dễ over-engineer nếu dùng mô hình này thay cho profiling hoặc OS/runtime metric

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Instruction Set]] vì instruction là đơn vị CPU thực thi
- [[Memory Model]] vì chương trình và data cùng sống trên memory abstraction

## Liên quan rộng

- Computer architecture
- Machine organization

## Keywords / Từ khóa tìm kiếm

- Von Neumann Model
- stored-program model
- mô hình Von Neumann
- von
- neumann
- model
- Computer Foundation
- mô hình
- kiến trúc hệ thống

## Source trace

- Computer Foundations Map Ch01
