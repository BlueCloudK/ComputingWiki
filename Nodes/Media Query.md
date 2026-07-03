# Media Query

Aliases: Media Query, media query, responsive breakpoint, điểm gãy responsive

Type: Web Development

## Context / Ngữ cảnh

Media Query là node bổ sung cho ComputingWiki về CSS rule áp dụng style theo viewport, device hoặc user preference.

## Boundary / Ranh giới

### Nó là gì

Media Query dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới CSS rule áp dụng style theo viewport, device hoặc user preference.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Media Query là hiểu boundary, input/output, state và failure mode riêng của CSS rule áp dụng style theo viewport, device hoặc user preference.

## Project Role / Vai trò trong dự án

Media Query giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Media Query decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Media Query ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Media Query làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Media Query nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Responsive Design]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Media Query
- [[CSS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Media Query

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Media Query
- media query
- responsive breakpoint
- điểm gãy responsive
- media
- query

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
