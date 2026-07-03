# Systems of Systems

Aliases: system of systems, hệ thống của nhiều hệ thống

Type: Tooling / Implementation Detail

## Bản chất

Systems of Systems là chi tiết triển khai hoặc tầng runtime ảnh hưởng tới cách code chạy trong môi trường thật. Nó thường nằm dưới lớp feature, nhưng khi lỗi xảy ra thì có thể quyết định performance, concurrency, memory, file hoặc platform behavior. Nó nối với các phần liên quan như [[Enterprise Systems Engineering]] và nhóm quyết định quanh systems of systems.

## Dùng trong dự án để làm gì

Systems of Systems giúp debug và ra quyết định ở tầng implementation: config, runtime, OS, memory, thread, file, tool hoặc framework boundary. Trong dự án, nó nên được quan tâm khi triệu chứng đã chạm tới tầng chạy thật.

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

- [[Enterprise Systems Engineering]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- SEBoK Map / Part 4
