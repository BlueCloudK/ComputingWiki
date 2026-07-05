# State Management

Aliases: State Management, state management

Type: Frontend Framework

## Context / Ngữ cảnh

State Management xuất hiện khi UI cần nhớ và đồng bộ dữ liệu thay đổi theo tương tác: form input, auth user, selected item, modal state, URL filter, API result, server cache hoặc trạng thái wizard nhiều bước. Khi nhiều component cùng đọc/ghi một state, boundary state bắt đầu quan trọng.

## Boundary / Ranh giới

### Nó là gì

State Management là cách quyết định dữ liệu UI sống ở đâu, ai sở hữu, ai được cập nhật, cập nhật theo event nào và component nào được re-render khi state đổi. State có thể là local component state, lifted state, global store, server cache, URL state hoặc persisted storage.

### Nó không phải là gì

State Management không phải mọi biến trong frontend. Không phải state nào cũng cần global store. Nó cũng không thay thế database/backend source of truth; nhiều state frontend chỉ là bản sao tạm hoặc cache của dữ liệu server.

## Core Mechanism / Cơ chế lõi

UI render từ state. Event hoặc async result tạo action/update. Framework/store cập nhật state, tính derived state nếu có, rồi trigger re-render hoặc notify subscriber. Server state cần cache key, invalidation, refetch, optimistic update và error/loading state; client state cần ownership rõ để tránh duplicate source of truth.

## Project Role / Vai trò trong dự án

State Management là node cần mở khi UI stale, form mất dữ liệu, nhiều component không đồng bộ, global store phình to, API cache không invalidate hoặc rerender quá nhiều. Nó giúp team vẽ state ownership map thay vì thêm library theo cảm giác.

## Output / Artifact nên có

- State ownership map: local, shared/global, server cache, URL, persisted storage
- Store/schema hoặc module boundary nếu dùng global state
- Update flow: action/event → state change → UI effect/API call
- Cache invalidation/refetch rule cho server state
- Test case cho loading/error/empty/stale/race condition

## Decision Checklist / Câu hỏi kiểm tra

- State này thuộc UI tạm, URL, server data hay business workflow?
- Component nào sở hữu state và component nào chỉ đọc?
- Có nhiều source of truth cho cùng dữ liệu không?
- State có cần tồn tại sau reload, share qua URL hoặc sync server không?
- Server cache invalidate khi mutation nào xảy ra?
- Có race condition giữa nhiều request/update không?
- Global store có đang chứa state chỉ dùng ở một component không?

## Failure Modes / Cách nó gây lỗi

- Duplicated source of truth làm UI hiển thị dữ liệu lệch nhau.
- Prop drilling quá sâu làm component khó dùng lại và debug.
- Global state quá rộng khiến thay đổi nhỏ re-render nhiều nơi.
- Server cache stale sau mutation vì thiếu invalidation.
- Optimistic update rollback sai làm UI và server lệch.
- Race giữa request cũ/mới làm UI hiện dữ liệu cũ.
- Persisted state giữ schema cũ sau deploy và làm app crash.

## Khi nào chưa cần hoặc dễ over-engineer

- State chỉ dùng trong một component thì local state thường đủ.
- Không nên thêm Redux/Zustand/Pinia/global store trước khi có shared state thật.
- Không nên đưa server data vào client global store nếu query/cache library đã giải quyết tốt hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Frontend Framework]] vì framework quyết định render/update behavior của state.
- [[Component]] vì state ownership thường gắn với component boundary.
- [[SPA]] vì SPA cần quản lý state giữa route/screen dài hạn.
- [[Stale Cache]] vì server/client cache stale là failure mode state phổ biến.
- [[Cache]] vì server state trong frontend thường là cache của backend data.

## Liên quan rộng

- UI architecture
- Server state
- Client state
- Frontend debugging

## Keywords / Từ khóa tìm kiếm

- State Management
- state management
- frontend state
- client state
- server state
- global store
- local state
- derived state
- state ownership
- stale state
- cache invalidation
- optimistic update
- prop drilling
- state management debugging

## Source trace

- React documentation
- Vue documentation
- Redux style guide
- TanStack Query documentation
