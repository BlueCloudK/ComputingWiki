# WebSocket

Aliases: WebSocket, real-time web, kết nối realtime

Type: Web Development

## Context / Ngữ cảnh

WebSocket là node bổ sung cho ComputingWiki về giao thức kết nối hai chiều lâu dài giữa browser và server.

## Boundary / Ranh giới

### Nó là gì

WebSocket dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới giao thức kết nối hai chiều lâu dài giữa browser và server.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của WebSocket là hiểu boundary, input/output, state và failure mode riêng của giao thức kết nối hai chiều lâu dài giữa browser và server.

## Project Role / Vai trò trong dự án

WebSocket giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- WebSocket decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- WebSocket ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai WebSocket làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu WebSocket nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTP]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng WebSocket
- [[API and Integration]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng WebSocket

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- WebSocket
- real-time web
- kết nối realtime
- websocket

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
