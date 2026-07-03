# JavaScript Engine

Aliases: JavaScript Engine, JavaScript engine, V8, JS runtime

Type: Web Development

## Context / Ngữ cảnh

JavaScript Engine là node bổ sung cho ComputingWiki về runtime thực thi JavaScript bằng parser, interpreter/JIT và garbage collector.

## Boundary / Ranh giới

### Nó là gì

JavaScript Engine dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới runtime thực thi JavaScript bằng parser, interpreter/JIT và garbage collector.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Web Development; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của JavaScript Engine là hiểu boundary, input/output, state và failure mode riêng của runtime thực thi JavaScript bằng parser, interpreter/JIT và garbage collector.

## Project Role / Vai trò trong dự án

JavaScript Engine giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- JavaScript Engine decision hoặc config liên quan
- Test/metric trên browser khi behavior ảnh hưởng UX
- Ghi chú compatibility hoặc fallback nếu có

## Decision Checklist / Câu hỏi kiểm tra

- JavaScript Engine ảnh hưởng render, network hay state trên browser?
- Có cần fallback cho browser/device khác không?
- Behavior này có metric hoặc test dễ kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai JavaScript Engine làm debug nhầm giữa browser, server và network
- Thiếu fallback hoặc metric làm lỗi chỉ lộ trên device/browser thật
- Tối ưu sai chỗ làm UX chậm hoặc layout vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu JavaScript Engine nếu trang rất đơn giản và chưa có constraint UX/performance
- Dễ over-engineer nếu thêm framework/tool trước khi hiểu browser behavior

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng JavaScript Engine
- [[Runtime]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng JavaScript Engine

## Liên quan rộng

- Frontend engineering
- Browser runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- JavaScript Engine
- JavaScript engine
- V8
- JS runtime
- máy chạy JavaScript
- javascript
- engine

## Source trace

- MDN Web Docs
- WHATWG HTML
- web.dev
