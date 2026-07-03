# PWA

Aliases: PWA, progressive web app, ứng dụng web tiến bộ

Type: Web Development

## Context / Ngữ cảnh

PWA là node bổ sung cho ComputingWiki về web app dùng service worker, manifest và capability browser để gần giống app native.

## Boundary / Ranh giới

### Nó là gì

PWA dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới web app dùng service worker, manifest và capability browser để gần giống app native.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của PWA là hiểu boundary, input/output, state và failure mode riêng của web app dùng service worker, manifest và capability browser để gần giống app native.

## Project Role / Vai trò trong dự án

PWA giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- PWA decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- PWA ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai PWA làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu PWA nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Service Worker]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng PWA
- [[Web Manifest]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng PWA

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- PWA
- progressive web app
- ứng dụng web tiến bộ

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
