# Web Performance Metric

Aliases: Web Performance Metric, web performance metric, frontend performance, đo hiệu năng web

Type: Web Development

## Context / Ngữ cảnh

Web Performance Metric là node bổ sung cho ComputingWiki về metric đo tốc độ, độ phản hồi và ổn định visual của web.

## Boundary / Ranh giới

### Nó là gì

Web Performance Metric dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới metric đo tốc độ, độ phản hồi và ổn định visual của web.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Web Performance Metric là hiểu boundary, input/output, state và failure mode riêng của metric đo tốc độ, độ phản hồi và ổn định visual của web.

## Project Role / Vai trò trong dự án

Web Performance Metric giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Web Performance Metric decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Web Performance Metric ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Web Performance Metric làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Web Performance Metric nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Core Web Vitals]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Web Performance Metric

## Liên quan rộng

- Performance
- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Web Performance Metric
- web performance metric
- frontend performance
- đo hiệu năng web
- performance
- metric

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
