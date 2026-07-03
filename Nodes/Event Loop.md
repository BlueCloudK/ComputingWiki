# Event Loop

Aliases: Event Loop, event loop, microtask, task queue

Type: Web Development

## Context / Ngữ cảnh

Event Loop là node bổ sung cho ComputingWiki về cơ chế runtime sắp xếp task, microtask và callback trong JavaScript.

## Boundary / Ranh giới

### Nó là gì

Event Loop dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cơ chế runtime sắp xếp task, microtask và callback trong JavaScript.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Event Loop là hiểu boundary, input/output, state và failure mode riêng của cơ chế runtime sắp xếp task, microtask và callback trong JavaScript.

## Project Role / Vai trò trong dự án

Event Loop giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Event Loop decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Event Loop ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Event Loop làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Event Loop nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Event Loop
- [[Runtime]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Event Loop

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Event Loop
- event loop
- microtask
- task queue
- vòng lặp sự kiện
- event
- loop

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
