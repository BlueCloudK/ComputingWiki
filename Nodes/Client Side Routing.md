# Client Side Routing

Aliases: Client Side Routing, client-side routing, Frontend Routing, SPA routing, định tuyến frontend

Type: Web Development

## Context / Ngữ cảnh

Client Side Routing là node bổ sung cho ComputingWiki về routing trong SPA diễn ra trên browser mà không reload toàn trang.

## Boundary / Ranh giới

### Nó là gì

Client Side Routing dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới routing trong SPA diễn ra trên browser mà không reload toàn trang.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Client Side Routing là hiểu boundary, input/output, state và failure mode riêng của routing trong SPA diễn ra trên browser mà không reload toàn trang.

## Project Role / Vai trò trong dự án

Client Side Routing giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Client Side Routing decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Client Side Routing ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Client Side Routing làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Client Side Routing nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[SPA]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Client Side Routing
- [[Route]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Client Side Routing

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Client Side Routing
- client-side routing
- Frontend Routing
- SPA routing
- định tuyến frontend
- client
- side
- routing

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
