# SameSite Cookie

Aliases: SameSite Cookie, SameSite, SameSite cookie, cookie chống CSRF

Type: Web Development

## Context / Ngữ cảnh

SameSite Cookie là node bổ sung cho ComputingWiki về thuộc tính cookie giới hạn gửi cookie trong request cross-site.

## Boundary / Ranh giới

### Nó là gì

SameSite Cookie dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới thuộc tính cookie giới hạn gửi cookie trong request cross-site.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của SameSite Cookie là hiểu boundary, input/output, state và failure mode riêng của thuộc tính cookie giới hạn gửi cookie trong request cross-site.

## Project Role / Vai trò trong dự án

SameSite Cookie giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- SameSite Cookie decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- SameSite Cookie ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai SameSite Cookie làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu SameSite Cookie nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cookie]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng SameSite Cookie
- [[CSRF]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng SameSite Cookie

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- SameSite Cookie
- SameSite
- SameSite cookie
- cookie chống CSRF
- samesite
- cookie

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
