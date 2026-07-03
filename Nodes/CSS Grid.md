# CSS Grid

Aliases: CSS Grid, CSS grid, display grid, layout lưới

Type: Web Development

## Context / Ngữ cảnh

CSS Grid là node bổ sung cho ComputingWiki về layout hai chiều trong CSS cho hàng, cột và vùng bố cục.

## Boundary / Ranh giới

### Nó là gì

CSS Grid dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới layout hai chiều trong CSS cho hàng, cột và vùng bố cục.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của CSS Grid là hiểu boundary, input/output, state và failure mode riêng của layout hai chiều trong CSS cho hàng, cột và vùng bố cục.

## Project Role / Vai trò trong dự án

CSS Grid giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- CSS Grid decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- CSS Grid ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai CSS Grid làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu CSS Grid nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CSS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng CSS Grid
- [[Responsive Design]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng CSS Grid

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- CSS Grid
- CSS grid
- display grid
- layout lưới
- grid

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
