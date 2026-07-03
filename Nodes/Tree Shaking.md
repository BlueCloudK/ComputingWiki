# Tree Shaking

Aliases: Tree Shaking, tree shaking, dead code elimination, loại code thừa

Type: Web Development

## Context / Ngữ cảnh

Tree Shaking là node bổ sung cho ComputingWiki về kỹ thuật loại bỏ code không dùng khỏi bundle khi build.

## Boundary / Ranh giới

### Nó là gì

Tree Shaking dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới kỹ thuật loại bỏ code không dùng khỏi bundle khi build.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Tree Shaking là hiểu boundary, input/output, state và failure mode riêng của kỹ thuật loại bỏ code không dùng khỏi bundle khi build.

## Project Role / Vai trò trong dự án

Tree Shaking giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Tree Shaking decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Tree Shaking ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Tree Shaking làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Tree Shaking nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Bundle]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Tree Shaking

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Tree Shaking
- tree shaking
- dead code elimination
- loại code thừa
- tree
- shaking

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
