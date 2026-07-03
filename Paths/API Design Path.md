# API Design Path

## Mục tiêu

Path này giúp người đọc thiết kế API rõ contract, dễ dùng, dễ version, có auth, error và vận hành được trong production.

## Khi nào dùng path này

- Khi thiết kế REST/API cho client hoặc service khác dùng.
- Khi chuẩn hóa error, pagination, auth hoặc versioning.
- Khi review API contract trước khi implement.

## 1. Nền giao tiếp

- [[HTTP]] — nền của phần lớn web API.
- [[Request]] — input client gửi tới server.
- [[Response]] — output server trả về client.
- [[REST]] — style API dựa trên resource và HTTP semantics.
- [[API Endpoint]] — operation cụ thể mà client gọi.

## 2. Contract

- [[API Contract]] — schema, behavior và error được thỏa thuận rõ.
- [[OpenAPI]] — format mô tả API machine-readable.
- [[API Documentation]] — tài liệu giúp client tích hợp đúng.
- [[Request Validation]] — đảm bảo input đúng shape/rule.
- [[Response Serialization]] — đảm bảo output ổn định và đúng format.

## 3. Query, list và lỗi

- [[Pagination]] — tránh trả danh sách quá lớn.
- [[Cursor Pagination]] — phù hợp dữ liệu thay đổi hoặc danh sách lớn.
- [[Offset Pagination]] — đơn giản nhưng có giới hạn khi dữ liệu lớn.
- [[Filtering]] — cho client lấy đúng subset cần dùng.
- [[Sorting]] — cho client kiểm soát thứ tự kết quả.
- [[Error Response]] — format lỗi nhất quán.
- [[API Error Code]] — mã lỗi ổn định cho client xử lý.

## 4. Auth và abuse control

- [[Authentication]] — biết caller là ai.
- [[Authorization]] — kiểm tra caller được phép làm gì.
- [[API Key]] — định danh client/service đơn giản.
- [[OAuth2]] — authorization flow cho access delegated.
- [[Rate Limiting]] — hạn chế abuse và bảo vệ capacity.
- [[API Security]] — nhìn API như attack surface.

## 5. Evolution và integration

- [[API Versioning]] — thay đổi API mà không phá client cũ.
- [[Backward Compatibility]] — giữ behavior cũ đủ để client không vỡ.
- [[Webhook]] — server gọi ngược client khi có event.
- [[Webhook Signature]] — xác minh webhook thật từ provider.
- [[Idempotency]] — retry an toàn với operation nhạy cảm.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Backward Compatibility
- API deprecation policy
- Resource naming
- HTTP status code taxonomy
- Problem details JSON

## Related paths

- [[Backend Engineering Path]]
- [[Web Application Path]]
- [[Security Engineering Path]]
- [[Database Engineering Path]]
