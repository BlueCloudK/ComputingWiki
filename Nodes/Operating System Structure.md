# Operating System Structure

Aliases: OS structure, cấu trúc hệ điều hành

## Dùng trong dự án để làm gì

Operating System Structure ảnh hưởng tới cách chương trình dùng tài nguyên máy như process, memory, file và concurrency. Khi gặp lỗi hiệu năng, race condition, deadlock hoặc vấn đề runtime, node này là nơi nên mở lại.

## Khi nào cần quan tâm

- Ứng dụng lỗi do memory, process, thread hoặc file
- Hiệu năng phụ thuộc tài nguyên runtime
- Cần hiểu behavior thấp tầng của môi trường chạy

## Lỗi / rủi ro thường gặp

- Race condition hoặc deadlock khó tái hiện
- Memory/file/resource leak làm hệ thống xuống dần
- Giả định sai về scheduling hoặc filesystem

## Gồm những gì

- [[Monolithic System]]
- [[Microkernel]]
- [[Virtual Machine]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Operating Systems Map / Ch01.7
