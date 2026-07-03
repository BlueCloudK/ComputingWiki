# Array

Aliases: array, mảng

Type: Computer Foundation

## Context / Ngữ cảnh

Array xuất hiện như nền tảng giúp hiểu correctness, complexity, data structure, algorithm hoặc mô hình tính toán phía dưới phần mềm.

## Boundary / Ranh giới

### Nó là gì

Array là kiến thức nền để giải thích vì sao code chạy đúng, chậm, sai ở edge case hoặc không scale khi input tăng.

### Nó không phải là gì

Nó không phải thứ luôn cần formalize trong mọi feature; giá trị nằm ở lúc constraint, correctness hoặc performance thật sự quan trọng.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là reasoning: input constraint, invariant, complexity, representation và edge case. Khi hiểu cơ chế, dev chọn được algorithm/data structure phù hợp hơn.

## Project Role / Vai trò trong dự án

Array ảnh hưởng tới lựa chọn thuật toán, cấu trúc dữ liệu, test edge case và debug lỗi performance/correctness.

## Output / Artifact nên có

- Decision note về thuật toán/cấu trúc dữ liệu được chọn
- Complexity hoặc invariant ngắn nếu ảnh hưởng performance/correctness
- Test case cho edge case nền tảng

## Decision Checklist / Câu hỏi kiểm tra

- Input size và constraint thật là gì?
- Complexity worst-case/average-case có chấp nhận được không?
- Edge case nào dễ làm thuật toán sai?
- Data structure hiện tại có phù hợp pattern truy cập không?
- Có test chứng minh invariant/correctness quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Chọn cấu trúc dữ liệu sai làm query/update chậm
- Nhầm complexity khiến hệ thống vỡ khi data tăng
- Bỏ sót edge case nền tảng
- Tối ưu thuật toán nhưng làm code khó bảo trì không cần thiết

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Array nếu input nhỏ, bounded và không ảnh hưởng trực tiếp tới correctness hoặc latency người dùng
- Dễ over-engineer nếu tối ưu thuật toán trước khi đo bottleneck thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Algorithms
- Data structures
- Debugging
- Performance reasoning

## Source trace

- Algorithms Map / Ch02
