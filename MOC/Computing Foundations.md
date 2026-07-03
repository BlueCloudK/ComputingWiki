# Computing Foundations

Aliases: computer science foundations, nền tảng computing

Type: Computer Foundation

## Context / Ngữ cảnh

Computing Foundations xuất hiện như nền tảng giúp hiểu correctness, complexity, data structure, algorithm hoặc mô hình tính toán phía dưới phần mềm.

## Boundary / Ranh giới

### Nó là gì

Computing Foundations là kiến thức nền để giải thích vì sao code chạy đúng, chậm, sai ở edge case hoặc không scale khi input tăng.

### Nó không phải là gì

Nó không phải thứ luôn cần formalize trong mọi feature; giá trị nằm ở lúc constraint, correctness hoặc performance thật sự quan trọng.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là reasoning: input constraint, invariant, complexity, representation và edge case. Khi hiểu cơ chế, dev chọn được algorithm/data structure phù hợp hơn.

## Project Role / Vai trò trong dự án

Computing Foundations là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

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

- Chưa cần đào sâu Computing Foundations nếu input nhỏ, bounded và không ảnh hưởng trực tiếp tới correctness hoặc latency người dùng
- Dễ over-engineer nếu tối ưu thuật toán trước khi đo bottleneck thật

## Gồm những gì

- [[Algorithms]]
- [[Programming Languages]]
- [[Compiler and Interpreter]]
- [[Operating System]]
- [[Computer Networks]]
- [[Data and Database]]
- [[Software Engineering]]
- [[Turing Model]]
- [[Von Neumann Model]]
- [[Number System]]
- [[Data Representation]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Algorithms
- Data structures
- Debugging
- Performance reasoning

## Keywords / Từ khóa tìm kiếm

- Computing Foundations
- computer science foundations
- nền tảng computing
- computing
- foundations
- Computer Foundation
- điện toán
- nền tảng
- mục lục kiến thức
- nhánh kiến thức

## Source trace

- CC2020 Map
- Computer Foundations Map
- Discrete Mathematics Map
