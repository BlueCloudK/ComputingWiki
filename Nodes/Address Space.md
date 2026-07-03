# Address Space

Aliases: address space, không gian địa chỉ

Type: Tooling / Implementation Detail

## Context / Ngữ cảnh

Address Space xuất hiện ở tầng implementation hoặc runtime: OS, process, memory, file, environment, tool hoặc platform behavior.

## Boundary / Ranh giới

### Nó là gì

Address Space là chi tiết có thể ảnh hưởng trực tiếp tới cách code chạy trong môi trường thật.

### Nó không phải là gì

Nó không phải abstraction business; nếu dùng sai tầng, team có thể debug nhầm symptom thay vì nguyên nhân.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là behavior của runtime/tool/platform: version, config, resource, scheduling, filesystem hoặc dependency quyết định kết quả thực thi.

## Project Role / Vai trò trong dự án

Address Space giúp debug lỗi environment-specific, performance thấp tầng, concurrency, file/memory hoặc config lệch.

## Output / Artifact nên có

- Troubleshooting note hoặc checklist tái hiện lỗi
- Config/runtime decision nếu ảnh hưởng deploy
- Test hoặc script kiểm tra behavior quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Triệu chứng có phụ thuộc environment/runtime không?
- Config/tool/version nào đang ảnh hưởng behavior?
- Có log/metric đủ chứng minh nguyên nhân không?
- Thay đổi implementation này có ảnh hưởng portability không?
- Có cách kiểm tra tự động để tránh regression không?

## Failure Modes / Cách nó gây lỗi

- Fix symptom ở tầng tool nhưng bỏ sót nguyên nhân hệ thống
- Phụ thuộc behavior riêng của environment
- Config/version lệch làm lỗi khó tái hiện
- Tối ưu thấp tầng làm code khó hiểu mà lợi ích nhỏ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu lỗi nằm rõ ở business logic
- Dễ over-engineer nếu tối ưu chi tiết runtime trước khi có metric hoặc bug thật

## Gồm những gì

- [[Virtual Memory]]

## Nối mạnh

- [[Process]] vì node này thường được kiểm tra cùng khi ra quyết định

## Liên quan rộng

- Runtime behavior
- Developer tooling
- Operating system
- Troubleshooting

## Keywords / Từ khóa tìm kiếm

- Address Space
- Virtual Memory
- Address Space learning keyword
- Address Space debug keyword
- Address Space design keyword
- Address Space khái niệm cần tra cứu

## Source trace

- Operating Systems Map / Ch01.5/Ch03
