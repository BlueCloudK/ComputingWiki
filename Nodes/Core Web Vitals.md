# Core Web Vitals

Aliases: Core Web Vitals, LCP INP CLS, chỉ số web vitals

Type: Web Development

## Context / Ngữ cảnh

Core Web Vitals là node bổ sung cho ComputingWiki về nhóm metric UX của web như LCP, INP và CLS.

## Boundary / Ranh giới

### Nó là gì

Core Web Vitals dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới nhóm metric UX của web như LCP, INP và CLS.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Core Web Vitals là hiểu boundary, input/output, state và failure mode riêng của nhóm metric UX của web như LCP, INP và CLS.

## Project Role / Vai trò trong dự án

Core Web Vitals giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Core Web Vitals decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Core Web Vitals ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Core Web Vitals làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Core Web Vitals nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Web Performance Metric]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Core Web Vitals
- [[Performance]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Core Web Vitals

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Core Web Vitals
- LCP INP CLS
- chỉ số web vitals
- core
- vitals

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
