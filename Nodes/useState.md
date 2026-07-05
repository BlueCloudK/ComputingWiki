# useState

Aliases: useState

Type: Frontend Framework

## Context / Ngữ cảnh

useState xuất hiện trong React khi function component cần giữ local state giữa các lần render, ví dụ input value, toggle, selected item hoặc UI state nhỏ.

## Boundary / Ranh giới

### Nó là gì

useState là React Hook cho phép component khai báo một state value và setter để yêu cầu React render lại khi state đổi.

### Nó không phải là gì

useState không phải global store và không phải nơi giữ server cache dài hạn. Nếu state cần share rộng hoặc fetch/cache từ server, cần xem boundary khác.

## Core Mechanism / Cơ chế lõi

React lưu state theo thứ tự hook trong component. Khi gọi setter, React schedule update và render lại component với state mới. Nếu state mới phụ thuộc state cũ, nên dùng functional update.

## Project Role / Vai trò trong dự án

Dùng node này khi debug local UI state, stale state, rerender, form input, toggle logic hoặc khi quyết định state nên nằm local, parent hay global store.

## Output / Artifact nên có

- State purpose
- Initial value
- Setter/update rule
- Derived-vs-stored decision
- Test cho interaction quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- State này có thật sự cần lưu không hay derive được từ props/data?
- State thuộc component này hay parent?
- Update có phụ thuộc state cũ không?
- State object/array có update immutable không?
- State reset khi props/user/context đổi chưa?

## Failure Modes / Cách nó gây lỗi

- Lưu state có thể derive làm lệch dữ liệu.
- Dùng state cũ trong closure làm update sai.
- Mutate object/array trực tiếp khiến React không nhận update đúng.
- Đưa state quá cao làm nhiều component rerender.
- Dùng useState cho server data/cache làm invalidation rối.

## Khi nào chưa cần hoặc dễ over-engineer

- Value tính được trực tiếp từ props/data thì không cần state riêng.
- Không nên đưa mọi thứ vào state chỉ vì muốn đọc lại sau render.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[React Hook]] vì useState là một hook cơ bản.
- [[React]] vì useState thuộc React component model.
- [[Component]] vì state local gắn với component render.
- [[Global State]] vì nhiều lỗi đến từ đặt state local/global sai boundary.

## Liên quan rộng

- Local state
- Functional update
- Derived state

## Keywords / Từ khóa tìm kiếm

- useState
- React useState
- local state
- state setter
- functional update
- derived state
- useState debugging

## Source trace

- React documentation
