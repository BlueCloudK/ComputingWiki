# Data Validation

Aliases: Data Validation, data validation, validate data, kiểm tra dữ liệu

Type: Application Engineering

## Context / Ngữ cảnh

Data Validation xuất hiện khi xây application thật cần kiểm tra dữ liệu có đúng type, shape, constraint và rule trước khi dùng.

## Boundary / Ranh giới

### Nó là gì

Data Validation là khái niệm giúp đặt đúng boundary, responsibility và artifact trong application engineering.

### Nó không phải là gì

Nó không phải nhãn chung để gắn vào mọi phần code; nếu không chỉ ra responsibility cụ thể thì dễ làm kiến trúc mơ hồ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định kiểm tra dữ liệu có đúng type, shape, constraint và rule trước khi dùng, ai sở hữu quyết định đó, input/output là gì, và failure mode xảy ra ở boundary nào.

## Project Role / Vai trò trong dự án

Data Validation giúp team nối requirement, code, test, deploy và debug bằng cùng một ngôn ngữ thay vì chỉ nhìn từng file rời rạc.

## Output / Artifact nên có

- Decision note hoặc diagram nhỏ cho Data Validation
- Test hoặc checklist cho behavior quan trọng
- Owner/boundary rõ nếu concept ảnh hưởng nhiều module hoặc service

## Decision Checklist / Câu hỏi kiểm tra

- Data Validation đang bảo vệ boundary hoặc responsibility nào?
- Có artifact nào giúp người khác review hoặc debug quyết định này không?
- Nếu behavior thay đổi, test/metric/contract nào sẽ báo sớm?

## Failure Modes / Cách nó gây lỗi

- Dùng Data Validation sai boundary làm code phụ thuộc chéo hoặc khó test
- Không có owner rõ khiến bug bị đẩy qua lại giữa layer/module
- Thiếu test/contract làm lỗi chỉ lộ khi tích hợp hoặc deploy

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Data Validation nếu app nhỏ, behavior đơn giản và chưa có pain thật
- Dễ over-engineer nếu tạo nhiều layer/process trước khi có boundary hoặc failure mode rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Validation]] vì liên quan trực tiếp tới cách áp dụng Data Validation
- [[Schema Validation]] vì liên quan trực tiếp tới cách áp dụng Data Validation

## Liên quan rộng

- Application engineering
- Project architecture
- Software delivery

## Keywords / Từ khóa tìm kiếm

- Data Validation
- data validation
- validate data
- kiểm tra dữ liệu
- data
- validation

## Source trace

- SWEBOK Guide
- Fowler Patterns of Enterprise Application Architecture
- Microsoft Application Architecture Guide
