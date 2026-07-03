# Layout Engine

Aliases: Layout Engine, layout engine, layout calculation, tính layout

Type: Web Development

## Context / Ngữ cảnh

Layout Engine là node bổ sung cho ComputingWiki về phần browser tính kích thước và vị trí element trước khi paint.

## Boundary / Ranh giới

### Nó là gì

Layout Engine dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới phần browser tính kích thước và vị trí element trước khi paint.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Layout Engine là hiểu boundary, input/output, state và failure mode riêng của phần browser tính kích thước và vị trí element trước khi paint.

## Project Role / Vai trò trong dự án

Layout Engine giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Layout Engine decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Layout Engine ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Layout Engine làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Layout Engine nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CSS Box Model]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Layout Engine
- [[Browser Rendering]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Layout Engine

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Layout Engine
- layout engine
- layout calculation
- tính layout
- layout
- engine

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
