# Global State

Aliases: Global State, application state

Type: Frontend Framework

## Context / Ngữ cảnh

Global State xuất hiện khi nhiều component/screen trong frontend cần cùng đọc hoặc cập nhật một phần state chung như user session, theme, cart, feature flag hoặc app-wide UI state.

## Boundary / Ranh giới

### Nó là gì

Global State là state được chia sẻ ngoài phạm vi một component/local subtree, thường được quản lý bằng store, context, signal hoặc state management library.

### Nó không phải là gì

Global State không phải nơi đổ mọi dữ liệu. Server data/cache, form local state và UI state tạm thời nên có boundary riêng nếu không global store sẽ phình và khó debug.

## Core Mechanism / Cơ chế lõi

State được đặt ở store/provider/singleton cao hơn component cần dùng. Component subscribe/observe phần state liên quan và rerender khi state đó đổi. Mutation nên đi qua action/event rõ để trace được flow.

## Project Role / Vai trò trong dự án

Dùng node này khi debug state bị stale, component rerender quá nhiều, user session lệch, data bị share sai scope hoặc app cần quyết định giữa local/server/global state.

## Output / Artifact nên có

- State ownership map
- Store/module boundary
- Mutation/action convention
- Subscription/render impact note
- Test cho flow state quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- State này có thật sự cần global không?
- Ai sở hữu state và ai được mutate?
- State là client UI state hay server state?
- Component nào subscribe phần state này?
- Mutation có trace/debug được không?

## Failure Modes / Cách nó gây lỗi

- Đưa quá nhiều state vào global làm dependency ngầm khắp app.
- Server data và client UI state bị trộn.
- Mutation không rõ source làm debug khó.
- Store update quá rộng làm nhiều component rerender.
- State không reset đúng khi logout/chuyển user.

## Khi nào chưa cần hoặc dễ over-engineer

- State chỉ dùng trong một component/subtree thì local state đủ.
- Không nên thêm state library nếu context/local state đơn giản đã giải quyết được.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[State Management]] vì global state là bài toán chính của state management.
- [[Component]] vì component subscribe và render theo state.
- [[React]] vì React app thường gặp quyết định local/global state.
- [[MobX]] vì MobX là một cách quản lý global/reactive state.
- [[Redux]] vì Redux là một cách quản lý global state có action flow rõ.

## Liên quan rộng

- Client state
- Store architecture
- UI consistency

## Keywords / Từ khóa tìm kiếm

- Global State
- application state
- frontend state
- global store
- client state
- state ownership
- global state debugging

## Source trace

- React documentation
- Redux documentation
- MobX documentation
