# API Versioning

Aliases: API compatibility, phiên bản API, versioned API

Type: API / Integration

## Context / Ngữ cảnh

API Versioning xuất hiện khi API cần thay đổi mà vẫn giữ consumer cũ chạy được hoặc có migration path rõ.

## Boundary / Ranh giới

### Nó là gì

API Versioning là cách quản lý thay đổi contract theo thời gian: breaking change, additive change, deprecation và compatibility.

### Nó không phải là gì

Nó không phải chỉ thêm `/v1` vào URL, không thay thế contract design, và không nên dùng để che việc thay đổi API tùy tiện.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là phân loại change: field mới, field đổi nghĩa, response/error đổi shape, behavior đổi hoặc endpoint bị deprecate. Mỗi loại cần compatibility rule.

## Project Role / Vai trò trong dự án

API Versioning giúp release server không phá client/mobile/third-party đang dùng contract cũ. Nó rất quan trọng khi consumer deploy chậm hơn provider.

## Output / Artifact nên có

- Compatibility policy
- Deprecation/migration note
- Versioned API contract hoặc changelog

## Decision Checklist / Câu hỏi kiểm tra

- Change này có breaking với consumer hiện tại không?
- Consumer có thể migrate trong bao lâu?
- Version nằm ở URL, header, media type hay contract doc?
- Có test backward compatibility không?
- Deprecated field/endpoint được monitor usage chưa?

## Failure Modes / Cách nó gây lỗi

- Thêm change tưởng nhỏ nhưng làm client cũ crash
- Có version number nhưng behavior vẫn đổi ngầm
- Không biết consumer nào còn dùng version cũ
- Deprecation không có migration path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần versioning nặng cho API prototype một consumer
- Dễ over-engineer nếu tạo nhiều version trước khi contract ổn định

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Contract]] vì versioning quản lý thay đổi của contract
- [[OpenAPI]] vì spec có thể ghi rõ version, deprecation và schema evolution
- [[Integration Test]] vì compatibility cần được kiểm tra với consumer path

## Liên quan rộng

- Backward compatibility
- Deprecation policy
- Consumer migration

## Keywords / Từ khóa tìm kiếm

- API Versioning
- API compatibility
- phiên bản API
- versioned API
- api
- versioning
- Integration

## Source trace

- Microsoft REST API Guidelines
- Google API Design Guide
