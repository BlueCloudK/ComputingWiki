# Secure Cookie

Aliases: Secure Cookie, Secure cookie, HttpOnly cookie, cookie bảo mật

Type: Web Development

## Context / Ngữ cảnh

Secure Cookie là node bổ sung cho ComputingWiki về cookie chỉ được gửi qua HTTPS để giảm rò rỉ trên kết nối không mã hóa.

## Boundary / Ranh giới

### Nó là gì

Secure Cookie dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cookie chỉ được gửi qua HTTPS để giảm rò rỉ trên kết nối không mã hóa.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Secure Cookie là hiểu boundary, input/output, state và failure mode riêng của cookie chỉ được gửi qua HTTPS để giảm rò rỉ trên kết nối không mã hóa.

## Project Role / Vai trò trong dự án

Secure Cookie giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Secure Cookie decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Secure Cookie ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Secure Cookie làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Secure Cookie nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cookie]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Secure Cookie
- [[HTTPS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Secure Cookie

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Secure Cookie
- Secure cookie
- HttpOnly cookie
- cookie bảo mật
- secure
- cookie

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
