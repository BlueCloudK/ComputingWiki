# Feature Flag

Aliases: Feature Flag, feature flag, feature toggle, cờ tính năng

Type: Backend Engineering

## Context / Ngữ cảnh

Feature Flag là node bổ sung cho ComputingWiki về cờ cấu hình bật/tắt feature mà không cần deploy code mới.

## Boundary / Ranh giới

### Nó là gì

Feature Flag dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cờ cấu hình bật/tắt feature mà không cần deploy code mới.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Backend Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Feature Flag là hiểu boundary, input/output, state và failure mode riêng của cờ cấu hình bật/tắt feature mà không cần deploy code mới.

## Project Role / Vai trò trong dự án

Feature Flag giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Feature Flag contract hoặc design note
- Test case cho request/response hoặc failure path
- Log/metric liên quan khi chạy production

## Decision Checklist / Câu hỏi kiểm tra

- Feature Flag nằm ở boundary client, service, data hay third-party?
- Failure path có response/log/rollback rõ không?
- Có test kiểm tra behavior quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Thiết kế Feature Flag mơ hồ làm client/backend hiểu khác nhau
- Không xử lý edge case làm lỗi chỉ lộ khi traffic thật
- Thiếu metric/log khiến incident khó trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Feature Flag nếu app nhỏ và chưa có nhiều client/service
- Dễ over-engineer nếu tạo abstraction trước khi có repeated behavior thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Deployment Strategy]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Feature Flag
- [[Rollback]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Feature Flag

## Liên quan rộng

- Backend architecture
- API design
- Production service

## Keywords / Từ khóa tìm kiếm

- Feature Flag
- feature flag
- feature toggle
- cờ tính năng
- feature
- flag

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- Fowler Patterns of Enterprise Application Architecture
