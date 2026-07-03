# Progressive Enhancement

Aliases: Progressive Enhancement, progressive enhancement, graceful degradation, nâng cấp tiến bộ

Type: Web Development

## Context / Ngữ cảnh

Progressive Enhancement là node bổ sung cho ComputingWiki về cách xây web hoạt động từ nền tảng cơ bản rồi tăng capability khi browser hỗ trợ.

## Boundary / Ranh giới

### Nó là gì

Progressive Enhancement dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cách xây web hoạt động từ nền tảng cơ bản rồi tăng capability khi browser hỗ trợ.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Progressive Enhancement là hiểu boundary, input/output, state và failure mode riêng của cách xây web hoạt động từ nền tảng cơ bản rồi tăng capability khi browser hỗ trợ.

## Project Role / Vai trò trong dự án

Progressive Enhancement giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Progressive Enhancement decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Progressive Enhancement ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Progressive Enhancement làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Progressive Enhancement nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Web Accessibility]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Progressive Enhancement

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Progressive Enhancement
- progressive enhancement
- graceful degradation
- nâng cấp tiến bộ
- progressive
- enhancement

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
