# Cache Control

Aliases: Cache Control, Cache-Control, cache header, điều khiển cache

Type: Web Development

## Context / Ngữ cảnh

Cache Control là node bổ sung cho ComputingWiki về HTTP header chỉ định response được cache thế nào và trong bao lâu.

## Boundary / Ranh giới

### Nó là gì

Cache Control dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới HTTP header chỉ định response được cache thế nào và trong bao lâu.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Cache Control là hiểu boundary, input/output, state và failure mode riêng của HTTP header chỉ định response được cache thế nào và trong bao lâu.

## Project Role / Vai trò trong dự án

Cache Control giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Cache Control decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Cache Control ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Cache Control làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Cache Control nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTP Cache]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Cache Control

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Cache Control
- Cache-Control
- cache header
- điều khiển cache
- cache
- control

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
