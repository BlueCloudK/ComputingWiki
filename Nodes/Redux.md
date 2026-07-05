# Redux

Aliases: Redux

Type: Frontend Framework

## Context / Ngữ cảnh

Redux xuất hiện khi frontend app cần shared state có luồng cập nhật rõ và dễ kiểm tra.

## Boundary / Ranh giới

### Nó là gì

Redux là thư viện quản lý state dựa trên store và reducer.

### Nó không phải là gì

Redux không phải database và không phải app nào cũng cần dùng.

## Core Mechanism / Cơ chế lõi

UI gửi mô tả thay đổi tới store. Reducer tạo state mới từ state cũ và mô tả thay đổi đó. Component đọc phần state cần dùng để render.

## Project Role / Vai trò trong dự án

Dùng node này khi debug shared state, reducer logic hoặc UI hiển thị dữ liệu không đồng bộ.

## Output / Artifact nên có

- Store structure
- Reducer convention
- State ownership map
- Test cho logic state quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- State này có thật sự global không?
- Reducer có dễ test không?
- Component có phụ thuộc store shape quá nhiều không?
- Server data có nên nằm ở cache riêng không?

## Failure Modes / Cách nó gây lỗi

- Đưa quá nhiều local state vào global store.
- Store shape leak vào mọi component.
- State server bị stale vì thiếu invalidation.
- Flow cập nhật quá vòng vèo khó debug.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ hoặc state local nhiều hơn shared thì chưa cần Redux.
- Không nên dùng Redux chỉ vì thói quen.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[State Management]] vì Redux thuộc nhóm quản lý state.
- [[React]] vì Redux thường dùng cùng React.
- [[Component]] vì component đọc state từ store.
- [[Stale Cache]] vì server data trong store có thể stale.

## Liên quan rộng

- Global state
- Reducer pattern
- Frontend architecture

## Keywords / Từ khóa tìm kiếm

- Redux
- Redux store
- reducer
- selector
- global state
- Redux debugging

## Source trace

- Redux documentation
