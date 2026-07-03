# Domain Service

Aliases: Domain Service, domain service, service miền, business service

Type: Application Engineering

## Context / Ngữ cảnh

Domain Service xuất hiện khi xây application thật cần logic nghiệp vụ không thuộc tự nhiên về một entity/value object cụ thể.

## Boundary / Ranh giới

### Nó là gì

Domain Service là khái niệm giúp đặt đúng boundary, responsibility và artifact trong application engineering.

### Nó không phải là gì

Nó không phải nhãn chung để gắn vào mọi phần code; nếu không chỉ ra responsibility cụ thể thì dễ làm kiến trúc mơ hồ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định logic nghiệp vụ không thuộc tự nhiên về một entity/value object cụ thể, ai sở hữu quyết định đó, input/output là gì, và failure mode xảy ra ở boundary nào.

## Project Role / Vai trò trong dự án

Domain Service giúp team nối requirement, code, test, deploy và debug bằng cùng một ngôn ngữ thay vì chỉ nhìn từng file rời rạc.

## Output / Artifact nên có

- Decision note hoặc diagram nhỏ cho Domain Service
- Test hoặc checklist cho behavior quan trọng
- Owner/boundary rõ nếu concept ảnh hưởng nhiều module hoặc service

## Decision Checklist / Câu hỏi kiểm tra

- Domain Service đang bảo vệ boundary hoặc responsibility nào?
- Có artifact nào giúp người khác review hoặc debug quyết định này không?
- Nếu behavior thay đổi, test/metric/contract nào sẽ báo sớm?

## Failure Modes / Cách nó gây lỗi

- Dùng Domain Service sai boundary làm code phụ thuộc chéo hoặc khó test
- Không có owner rõ khiến bug bị đẩy qua lại giữa layer/module
- Thiếu test/contract làm lỗi chỉ lộ khi tích hợp hoặc deploy

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Domain Service nếu app nhỏ, behavior đơn giản và chưa có pain thật
- Dễ over-engineer nếu tạo nhiều layer/process trước khi có boundary hoặc failure mode rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Domain Model]] vì liên quan trực tiếp tới cách áp dụng Domain Service
- [[Business Rule]] vì liên quan trực tiếp tới cách áp dụng Domain Service

## Liên quan rộng

- Application engineering
- Project architecture
- Software delivery

## Keywords / Từ khóa tìm kiếm

- Domain Service
- domain service
- service miền
- business service
- domain
- service

## Source trace

- SWEBOK Guide
- Fowler Patterns of Enterprise Application Architecture
- Microsoft Application Architecture Guide
