# API Versioning

Aliases: API compatibility, phiên bản API, versioned API

Type: API / Integration

## Context / Ngữ cảnh

API Versioning xuất hiện khi API cần thay đổi mà không làm hỏng consumer cũ như frontend, mobile app, partner integration, SDK hoặc service nội bộ deploy chậm hơn provider. Nó quan trọng khi contract đã có người dùng thật và thay đổi API cần migration path rõ.

## Boundary / Ranh giới

### Nó là gì

API Versioning là cách quản lý thay đổi API contract theo thời gian: phân loại breaking/additive change, giữ backward compatibility, deprecate endpoint/field cũ, phát hành version mới và theo dõi consumer migration. Version có thể nằm ở URL, header, media type, domain hoặc spec/changelog.

### Nó không phải là gì

API Versioning không chỉ là thêm `/v1` vào URL. Nếu behavior vẫn đổi ngầm, version number không giúp consumer. Nó cũng không thay thế thiết kế contract tốt; versioning là cơ chế quản lý thay đổi, không phải giấy phép để phá API tùy tiện.

## Core Mechanism / Cơ chế lõi

Mỗi thay đổi API được phân loại: thêm field optional thường backward compatible; đổi nghĩa field, đổi type, đổi required field, đổi error shape, xóa endpoint hoặc đổi behavior thường là breaking. Versioning tốt cần compatibility policy, deprecation window, usage monitoring, migration guide và test để đảm bảo version cũ vẫn chạy.

## Project Role / Vai trò trong dự án

API Versioning giúp release backend mà không phá client đang ngoài quyền kiểm soát của team. Khi review API change, team phải hỏi consumer nào bị ảnh hưởng, spec/version nào đổi, có migration path không, và có thể deploy server trước client hay không.

## Output / Artifact nên có

- Compatibility policy: change nào allowed, change nào breaking
- Versioning strategy: URL/header/media type/spec version
- Deprecation policy: timeline, warning, usage monitoring, removal criteria
- Migration guide/changelog cho consumer
- Backward compatibility test hoặc contract test cho version cũ
- OpenAPI/spec version ghi rõ deprecated field/endpoint nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Change này có breaking với consumer hiện tại không?
- Consumer nào đang dùng endpoint/field/version cũ?
- Có thể thêm field optional thay vì đổi/xóa field cũ không?
- Version nằm ở đâu: URL, header, media type hay spec/release tag?
- Có deprecation period và migration guide không?
- Có monitor usage của endpoint/field deprecated không?
- Contract test có bắt server phá version cũ trước release không?

## Failure Modes / Cách nó gây lỗi

- Thay đổi field từ optional thành required làm client cũ fail.
- Đổi error response shape làm frontend/mobile không xử lý được lỗi.
- Có `/v1` nhưng behavior đổi ngầm sau deploy, consumer không có cách biết.
- Không biết consumer nào còn dùng endpoint cũ nên xóa nhầm.
- Deprecation không có migration guide làm partner/client không chuyển kịp.
- Generated SDK không pin spec version làm consumer update và nhận breaking change bất ngờ.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype một consumer có thể dùng changelog nhẹ trước khi versioning nặng.
- Không nên tạo nhiều version trước khi API có contract ổn định và consumer thật.
- Không nên giữ version cũ vô hạn nếu không có usage hoặc business reason rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Contract]] vì versioning quản lý thay đổi của contract.
- [[OpenAPI]] vì spec có thể ghi version, deprecated field và breaking-change check.
- [[Integration Test]] vì compatibility cần được kiểm tra với consumer path.
- [[API Endpoint]] vì versioning thường áp dụng theo endpoint/operation.
- [[Backward Compatibility]] vì mục tiêu chính là không phá consumer cũ.

## Liên quan rộng

- Backward compatibility
- Deprecation policy
- Consumer migration
- SDK release management

## Keywords / Từ khóa tìm kiếm

- API Versioning
- versioned API
- API compatibility
- phiên bản API
- backward compatibility
- breaking change
- additive change
- deprecation policy
- migration guide
- consumer compatibility
- API changelog
- OpenAPI version
- URL versioning
- header versioning
- contract compatibility

## Source trace

- Microsoft REST API Guidelines
- Google API Design Guide
