# Computing Foundations

Aliases: computer science foundations, nền tảng computing

Type: Computer Foundation

## Bản chất

Computing Foundations là kiến thức nền giúp hiểu vì sao software chạy đúng, chạy chậm hoặc fail ở một số điều kiện. Nó không phải phần luôn viết vào code, nhưng giúp dev chọn cấu trúc dữ liệu, thuật toán và debug vấn đề sâu hơn. Nó nối với các phần liên quan như [[Algorithms]], [[Operating System]], [[Computer Networks]] và nhóm quyết định quanh computing foundations.

## Dùng trong dự án để làm gì

Computing Foundations là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

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

- [[Algorithms]]
- [[Operating System]]
- [[Computer Networks]]
- [[Data and Database]]
- [[Software Engineering]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- CC2020 Map
- Computer Foundations Map
- Discrete Mathematics Map
