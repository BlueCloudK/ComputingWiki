# Responsive Design

Aliases: Responsive Design, responsive design, mobile responsive, thiết kế đáp ứng

Type: Web Development

## Context / Ngữ cảnh

Responsive Design là node bổ sung cho ComputingWiki về thiết kế giao diện thích ứng nhiều kích thước màn hình và input mode.

## Boundary / Ranh giới

### Nó là gì

Responsive Design dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới thiết kế giao diện thích ứng nhiều kích thước màn hình và input mode.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Responsive Design là hiểu boundary, input/output, state và failure mode riêng của thiết kế giao diện thích ứng nhiều kích thước màn hình và input mode.

## Project Role / Vai trò trong dự án

Responsive Design giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Responsive Design decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Responsive Design ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Responsive Design làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Responsive Design nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Media Query]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Responsive Design
- [[CSS Grid]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Responsive Design

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Responsive Design
- responsive design
- mobile responsive
- thiết kế đáp ứng
- responsive
- design

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
