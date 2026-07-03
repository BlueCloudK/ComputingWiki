# Compositing

Aliases: Compositing, compositing, layer compositing, ghép layer

Type: Web Development

## Context / Ngữ cảnh

Compositing là node bổ sung cho ComputingWiki về bước ghép nhiều layer đã paint để tạo frame cuối.

## Boundary / Ranh giới

### Nó là gì

Compositing dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới bước ghép nhiều layer đã paint để tạo frame cuối.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Compositing là hiểu boundary, input/output, state và failure mode riêng của bước ghép nhiều layer đã paint để tạo frame cuối.

## Project Role / Vai trò trong dự án

Compositing giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Compositing decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Compositing ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Compositing làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Compositing nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Paint]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Compositing

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Compositing
- compositing
- layer compositing
- ghép layer

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
