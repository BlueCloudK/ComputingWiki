# SSR

Aliases: Server Side Rendering, render phía server

Type: Web Development

## Context / Ngữ cảnh

SSR xuất hiện khi cần render HTML ở server để cải thiện first load, SEO hoặc data-fetching boundary.

## Boundary / Ranh giới

### Nó là gì

SSR là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của SSR là server render pipeline, hydration, cache và request-specific data.

## Project Role / Vai trò trong dự án

SSR giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- SSR decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới SSR
- Failure note ghi rõ SSR ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- SSR đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của SSR không?
- Khi SSR fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của SSR làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên SSR nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu SSR nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh SSR trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Frontend architecture
- Browser debugging
- User experience

## Keywords / Từ khóa tìm kiếm

- SSR
- Server Side Rendering
- render phía server
- ssr debugging
- ssr design
- web development
- frontend debugging
- phát triển web

## Source trace

- Next.js docs; web.dev rendering
