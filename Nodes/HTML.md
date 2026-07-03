# HTML

Aliases: HyperText Markup Language, ngôn ngữ đánh dấu HTML

Type: Web Development

## Context / Ngữ cảnh

HTML xuất hiện khi cần mô tả cấu trúc nội dung web để browser xây DOM và accessibility tree.

## Boundary / Ranh giới

### Nó là gì

HTML là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của HTML là element, attribute, semantic tag, form control và document structure.

## Project Role / Vai trò trong dự án

HTML giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- HTML decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới HTML
- Failure note ghi rõ HTML ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- HTML đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của HTML không?
- Khi HTML fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của HTML làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên HTML nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu HTML nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh HTML trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Frontend architecture
- Browser debugging
- User experience
- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- HTML
- HyperText Markup Language
- ngôn ngữ đánh dấu HTML
- html debugging
- html design
- web development
- frontend debugging
- phát triển web
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- MDN HTML documentation
