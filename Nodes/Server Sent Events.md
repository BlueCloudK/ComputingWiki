# Server Sent Events

Aliases: Server Sent Events, SSE, server-sent events, stream event

Type: Web Development

## Context / Ngữ cảnh

Server Sent Events là node bổ sung cho ComputingWiki về cơ chế server stream event một chiều tới browser qua HTTP.

## Boundary / Ranh giới

### Nó là gì

Server Sent Events dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cơ chế server stream event một chiều tới browser qua HTTP.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Server Sent Events là hiểu boundary, input/output, state và failure mode riêng của cơ chế server stream event một chiều tới browser qua HTTP.

## Project Role / Vai trò trong dự án

Server Sent Events giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Server Sent Events decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Server Sent Events ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Server Sent Events làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Server Sent Events nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTP]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Server Sent Events
- [[Event Driven Architecture]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Server Sent Events

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Server Sent Events
- SSE
- server-sent events
- stream event
- server
- sent
- events

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
