# Anti Corruption Layer

Aliases: Anti Corruption Layer, anti-corruption layer, ACL pattern, lớp chống nhiễm model

Type: Application Engineering

## Context / Ngữ cảnh

Anti Corruption Layer xuất hiện khi xây application thật cần layer dịch model bên ngoài sang model nội bộ để tránh nhiễm domain.

## Boundary / Ranh giới

### Nó là gì

Anti Corruption Layer là khái niệm giúp đặt đúng boundary, responsibility và artifact trong application engineering.

### Nó không phải là gì

Nó không phải nhãn chung để gắn vào mọi phần code; nếu không chỉ ra responsibility cụ thể thì dễ làm kiến trúc mơ hồ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định layer dịch model bên ngoài sang model nội bộ để tránh nhiễm domain, ai sở hữu quyết định đó, input/output là gì, và failure mode xảy ra ở boundary nào.

## Project Role / Vai trò trong dự án

Anti Corruption Layer giúp team nối requirement, code, test, deploy và debug bằng cùng một ngôn ngữ thay vì chỉ nhìn từng file rời rạc.

## Output / Artifact nên có

- Decision note hoặc diagram nhỏ cho Anti Corruption Layer
- Test hoặc checklist cho behavior quan trọng
- Owner/boundary rõ nếu concept ảnh hưởng nhiều module hoặc service

## Decision Checklist / Câu hỏi kiểm tra

- Anti Corruption Layer đang bảo vệ boundary hoặc responsibility nào?
- Có artifact nào giúp người khác review hoặc debug quyết định này không?
- Nếu behavior thay đổi, test/metric/contract nào sẽ báo sớm?

## Failure Modes / Cách nó gây lỗi

- Dùng Anti Corruption Layer sai boundary làm code phụ thuộc chéo hoặc khó test
- Không có owner rõ khiến bug bị đẩy qua lại giữa layer/module
- Thiếu test/contract làm lỗi chỉ lộ khi tích hợp hoặc deploy

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Anti Corruption Layer nếu app nhỏ, behavior đơn giản và chưa có pain thật
- Dễ over-engineer nếu tạo nhiều layer/process trước khi có boundary hoặc failure mode rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Integration Boundary]] vì liên quan trực tiếp tới cách áp dụng Anti Corruption Layer
- [[DTO Mapper]] vì liên quan trực tiếp tới cách áp dụng Anti Corruption Layer

## Liên quan rộng

- Application engineering
- Project architecture
- Software delivery

## Keywords / Từ khóa tìm kiếm

- Anti Corruption Layer
- anti-corruption layer
- ACL pattern
- lớp chống nhiễm model
- anti
- corruption
- layer

## Source trace

- SWEBOK Guide
- Fowler Patterns of Enterprise Application Architecture
- Microsoft Application Architecture Guide
