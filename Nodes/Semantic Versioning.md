# Semantic Versioning

Aliases: Semantic Versioning, semantic versioning, SemVer, phiên bản ngữ nghĩa

Type: Application Engineering

## Context / Ngữ cảnh

Semantic Versioning xuất hiện khi xây application thật cần quy ước version MAJOR.MINOR.PATCH theo mức độ thay đổi compatibility.

## Boundary / Ranh giới

### Nó là gì

Semantic Versioning là khái niệm giúp đặt đúng boundary, responsibility và artifact trong application engineering.

### Nó không phải là gì

Nó không phải nhãn chung để gắn vào mọi phần code; nếu không chỉ ra responsibility cụ thể thì dễ làm kiến trúc mơ hồ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định quy ước version MAJOR.MINOR.PATCH theo mức độ thay đổi compatibility, ai sở hữu quyết định đó, input/output là gì, và failure mode xảy ra ở boundary nào.

## Project Role / Vai trò trong dự án

Semantic Versioning giúp team nối requirement, code, test, deploy và debug bằng cùng một ngôn ngữ thay vì chỉ nhìn từng file rời rạc.

## Output / Artifact nên có

- Decision note hoặc diagram nhỏ cho Semantic Versioning
- Test hoặc checklist cho behavior quan trọng
- Owner/boundary rõ nếu concept ảnh hưởng nhiều module hoặc service

## Decision Checklist / Câu hỏi kiểm tra

- Semantic Versioning đang bảo vệ boundary hoặc responsibility nào?
- Có artifact nào giúp người khác review hoặc debug quyết định này không?
- Nếu behavior thay đổi, test/metric/contract nào sẽ báo sớm?

## Failure Modes / Cách nó gây lỗi

- Dùng Semantic Versioning sai boundary làm code phụ thuộc chéo hoặc khó test
- Không có owner rõ khiến bug bị đẩy qua lại giữa layer/module
- Thiếu test/contract làm lỗi chỉ lộ khi tích hợp hoặc deploy

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Semantic Versioning nếu app nhỏ, behavior đơn giản và chưa có pain thật
- Dễ over-engineer nếu tạo nhiều layer/process trước khi có boundary hoặc failure mode rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Backward Compatibility]] vì liên quan trực tiếp tới cách áp dụng Semantic Versioning
- [[Release Engineering]] vì liên quan trực tiếp tới cách áp dụng Semantic Versioning

## Liên quan rộng

- Application engineering
- Project architecture
- Software delivery

## Keywords / Từ khóa tìm kiếm

- Semantic Versioning
- semantic versioning
- SemVer
- phiên bản ngữ nghĩa
- semantic
- versioning

## Source trace

- SWEBOK Guide
- Fowler Patterns of Enterprise Application Architecture
- Microsoft Application Architecture Guide
