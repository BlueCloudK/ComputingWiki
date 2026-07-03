# Fetch API

Aliases: Fetch API, fetch, fetch API, gửi request frontend

Type: Web Development

## Context / Ngữ cảnh

Fetch API là node bổ sung cho ComputingWiki về API browser dùng để gửi HTTP request bất đồng bộ từ frontend.

## Boundary / Ranh giới

### Nó là gì

Fetch API dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới API browser dùng để gửi HTTP request bất đồng bộ từ frontend.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Fetch API là hiểu boundary, input/output, state và failure mode riêng của API browser dùng để gửi HTTP request bất đồng bộ từ frontend.

## Project Role / Vai trò trong dự án

Fetch API giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Fetch API decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Fetch API ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Fetch API làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Fetch API nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTP Client]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Fetch API
- [[API Contract]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Fetch API

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Fetch API
- fetch
- fetch API
- gửi request frontend

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
