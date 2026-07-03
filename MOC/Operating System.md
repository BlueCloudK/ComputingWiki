# Operating System

Aliases: OS, operating systems, hệ điều hành

Type: Tooling / Implementation Detail

## Bản chất

Operating System là chi tiết triển khai hoặc tầng runtime ảnh hưởng tới cách code chạy trong môi trường thật. Nó thường nằm dưới lớp feature, nhưng khi lỗi xảy ra thì có thể quyết định performance, concurrency, memory, file hoặc platform behavior. Nó nối với các phần liên quan như [[Operating System Concepts]], [[System Call]], [[Operating System Structure]] và nhóm quyết định quanh operating system.

## Dùng trong dự án để làm gì

Operating System là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

## Khi nào cần quan tâm

- Bug chỉ xảy ra ở một environment hoặc runtime cụ thể
- Có lỗi memory, file, process, thread hoặc config
- Performance/debug cần nhìn dưới tầng business logic
- Tool/framework behavior khác giả định của team

## Output / artifact nên có

- Troubleshooting note hoặc checklist tái hiện lỗi
- Config/runtime decision nếu ảnh hưởng deploy
- Test hoặc script kiểm tra behavior quan trọng

## Checklist kiểm tra

- Triệu chứng có phụ thuộc environment/runtime không?
- Config/tool/version nào đang ảnh hưởng behavior?
- Có log/metric đủ chứng minh nguyên nhân không?
- Thay đổi implementation này có ảnh hưởng portability không?
- Có cách kiểm tra tự động để tránh regression không?

## Lỗi / rủi ro thường gặp

- Fix symptom ở tầng tool nhưng bỏ sót nguyên nhân hệ thống
- Phụ thuộc behavior riêng của environment
- Config/version lệch làm lỗi khó tái hiện
- Tối ưu thấp tầng làm code khó hiểu mà lợi ích nhỏ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu lỗi nằm rõ ở business logic
- Dễ over-engineer nếu tối ưu chi tiết runtime trước khi có metric hoặc bug thật

## Gồm những gì

- [[Operating System Concepts]]
- [[System Call]]
- [[Operating System Structure]]
- [[Process]]
- [[Thread]]
- [[Processes and Threads]]
- [[Interprocess Communication]]
- [[Scheduling]]
- [[Memory Management]]
- [[Virtual Memory]]
- [[File System]]
- [[Deadlock]]
- [[Virtualization]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Operating Systems Map
- Computer Foundations Map
