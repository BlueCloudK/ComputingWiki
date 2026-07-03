# CSS

Aliases: Cascading Style Sheets, stylesheet, CSS layout

Type: Web Development

## Context / Ngữ cảnh

CSS xuất hiện khi cần kiểm soát layout, typography, responsive behavior và visual state của web page.

## Boundary / Ranh giới

### Nó là gì

CSS là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của CSS là cascade, selector, box model, layout algorithm, media query và custom properties.

## Project Role / Vai trò trong dự án

CSS giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- CSS decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới CSS
- Failure note ghi rõ CSS ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- CSS đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của CSS không?
- Khi CSS fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của CSS làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên CSS nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu CSS nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh CSS trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Frontend architecture
- Browser debugging
- User experience

## Keywords / Từ khóa tìm kiếm

- CSS
- Cascading Style Sheets
- stylesheet
- CSS layout
- css debugging
- css design
- web development
- frontend debugging
- phát triển web

## Source trace

- MDN CSS documentation
