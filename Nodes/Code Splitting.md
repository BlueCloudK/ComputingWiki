# Code Splitting

Aliases: Code Splitting, code splitting, lazy load chunk, chia bundle

Type: Web Development

## Context / Ngữ cảnh

Code Splitting là node bổ sung cho ComputingWiki về kỹ thuật chia bundle để chỉ tải phần code cần cho route/feature hiện tại.

## Boundary / Ranh giới

### Nó là gì

Code Splitting dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới kỹ thuật chia bundle để chỉ tải phần code cần cho route/feature hiện tại.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Code Splitting là hiểu boundary, input/output, state và failure mode riêng của kỹ thuật chia bundle để chỉ tải phần code cần cho route/feature hiện tại.

## Project Role / Vai trò trong dự án

Code Splitting giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Code Splitting decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Code Splitting ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Code Splitting làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Code Splitting nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Bundle]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Code Splitting
- [[Performance Budget]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Code Splitting

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Code Splitting
- code splitting
- lazy load chunk
- chia bundle
- code
- splitting

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
