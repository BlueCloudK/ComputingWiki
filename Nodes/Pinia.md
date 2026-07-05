# Pinia

Aliases: Pinia

Type: Frontend Framework

## Context / Ngữ cảnh

Pinia xuất hiện khi Vue app cần quản lý shared state rõ hơn local component state.

## Boundary / Ranh giới

### Nó là gì

Pinia là state management library cho Vue. Nó tổ chức state thành store với state, getter và action.

### Nó không phải là gì

Pinia không phải database và không thay thế server source of truth.

## Core Mechanism / Cơ chế lõi

Component đọc store, gọi action để đổi state hoặc gọi API, rồi UI cập nhật theo reactive state.

## Project Role / Vai trò trong dự án

Dùng node này khi debug shared state, auth state, cart/filter state hoặc state bị stale trong Vue app.

## Output / Artifact nên có

- Store list
- State ownership map
- Action/data fetching rule
- Test cho action quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- State này có thật sự cần shared store không?
- Store có đang chứa server data stale không?
- Action có side effect rõ không?
- Component có phụ thuộc store quá sâu không?

## Failure Modes / Cách nó gây lỗi

- Đưa local state vào global store quá sớm.
- Store phình to thành nơi chứa mọi thứ.
- Server data không invalidate sau mutation.
- Component coupling quá mạnh với store shape.

## Khi nào chưa cần hoặc dễ over-engineer

- State chỉ dùng trong một component thì local state đủ.
- Không nên dùng Pinia chỉ để truyền một prop đơn giản.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Vue]] vì Pinia là state library phổ biến cho Vue.
- [[State Management]] vì Pinia giải quyết shared state.
- [[Component]] vì component đọc/ghi state qua store.
- [[Stale Cache]] vì server data trong store có thể stale.

## Liên quan rộng

- Vue state
- Shared state
- Store pattern

## Keywords / Từ khóa tìm kiếm

- Pinia
- Vue store
- Pinia state
- Pinia action
- shared state
- Pinia debugging

## Source trace

- Pinia documentation
