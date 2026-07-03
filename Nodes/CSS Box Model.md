# CSS Box Model

Aliases: CSS Box Model, box model, CSS box model, mô hình hộp CSS

Type: Web Development

## Context / Ngữ cảnh

CSS Box Model là node bổ sung cho ComputingWiki về mô hình content, padding, border và margin để tính kích thước element.

## Boundary / Ranh giới

### Nó là gì

CSS Box Model dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới mô hình content, padding, border và margin để tính kích thước element.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của CSS Box Model là hiểu boundary, input/output, state và failure mode riêng của mô hình content, padding, border và margin để tính kích thước element.

## Project Role / Vai trò trong dự án

CSS Box Model giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- CSS Box Model decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- CSS Box Model ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai CSS Box Model làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu CSS Box Model nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CSS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng CSS Box Model
- [[Layout Engine]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng CSS Box Model

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- CSS Box Model
- box model
- CSS box model
- mô hình hộp CSS
- model

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
