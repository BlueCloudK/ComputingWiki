# Discrete Mathematics

Aliases: discrete math, toán rời rạc

Type: Computer Foundation

## Bản chất

Discrete Mathematics là kiến thức nền giúp hiểu vì sao software chạy đúng, chạy chậm hoặc fail ở một số điều kiện. Nó không phải phần luôn viết vào code, nhưng giúp dev chọn cấu trúc dữ liệu, thuật toán và debug vấn đề sâu hơn. Nó nối với các phần liên quan như [[Logic and Proofs]], [[Sets Functions Sequences and Matrices]], [[Counting]] và nhóm quyết định quanh discrete mathematics.

## Dùng trong dự án để làm gì

Discrete Mathematics là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

## Khi nào cần quan tâm

- Cần phân tích complexity hoặc correctness
- Dữ liệu tăng làm cách làm đơn giản bị chậm
- Bug liên quan edge case, ordering, recursion, graph hoặc state
- Cần chọn data structure/algorithm trước khi tối ưu

## Output / artifact nên có

- Decision note về thuật toán/cấu trúc dữ liệu được chọn
- Complexity hoặc invariant ngắn nếu ảnh hưởng performance/correctness
- Test case cho edge case nền tảng

## Checklist kiểm tra

- Input size và constraint thật là gì?
- Complexity worst-case/average-case có chấp nhận được không?
- Edge case nào dễ làm thuật toán sai?
- Data structure hiện tại có phù hợp pattern truy cập không?
- Có test chứng minh invariant/correctness quan trọng không?

## Lỗi / rủi ro thường gặp

- Chọn cấu trúc dữ liệu sai làm query/update chậm
- Nhầm complexity khiến hệ thống vỡ khi data tăng
- Bỏ sót edge case nền tảng
- Tối ưu thuật toán nhưng làm code khó bảo trì không cần thiết

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu input nhỏ và không nằm trên critical path
- Dễ over-engineer nếu tối ưu thuật toán trước khi đo bottleneck thật

## Gồm những gì

- [[Logic and Proofs]]
- [[Sets Functions Sequences and Matrices]]
- [[Counting]]
- [[Discrete Probability]]
- [[Relations]]
- [[Graph]]
- [[Tree]]
- [[Boolean Algebra]]
- [[Number Theory and Cryptography]]
- [[Induction and Recursion]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Discrete Mathematics Map
