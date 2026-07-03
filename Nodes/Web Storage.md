# Web Storage

Aliases: localStorage, sessionStorage, lưu trữ browser

Type: Web Development

## Context / Ngữ cảnh

Web Storage xuất hiện khi browser cần lưu preference, session state hoặc cache nhỏ theo origin.

## Boundary / Ranh giới

### Nó là gì

Web Storage là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Web Storage là origin-scoped key-value storage, persistence, quota và security boundary.

## Project Role / Vai trò trong dự án

Web Storage giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Web Storage decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Web Storage
- Failure note ghi rõ Web Storage ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Web Storage đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Web Storage không?
- Khi Web Storage fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Web Storage làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Web Storage nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Web Storage nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Web Storage trước khi có nhu cầu vận hành hoặc học tập rõ

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

- Web Storage
- localStorage
- sessionStorage
- lưu trữ browser
- web storage debugging
- web storage design
- web development
- frontend debugging
- phát triển web
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- MDN Web Storage API
