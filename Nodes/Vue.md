# Vue

Aliases: Vue, Vue.js

Type: Frontend Framework

## Context / Ngữ cảnh

Vue xuất hiện khi web app cần xây UI bằng component, reactive state và template dễ đọc.

## Boundary / Ranh giới

### Nó là gì

Vue là frontend framework cho JavaScript, tổ chức UI thành component với props, emits, state và template.

### Nó không phải là gì

Vue không phải backend framework, database hoặc design system.

## Core Mechanism / Cơ chế lõi

Component Vue khai báo template, logic và style. Khi reactive state đổi, Vue cập nhật UI tương ứng.

## Project Role / Vai trò trong dự án

Dùng node này khi cần hiểu component Vue, reactivity, router, store hoặc build frontend.

## Output / Artifact nên có

- Component tree
- Props/emits contract
- State ownership map
- Router/page map nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- State là local, store, route hay server data?
- Props/emits có rõ không?
- Component có quá lớn không?
- Có cần Nuxt hay Vue SPA đủ dùng?

## Failure Modes / Cách nó gây lỗi

- Store quá rộng làm state khó kiểm soát.
- Props/emits mơ hồ làm component coupling cao.
- Reactivity hiểu sai làm UI không cập nhật như mong đợi.
- Component quá lớn khó test/refactor.

## Khi nào chưa cần hoặc dễ over-engineer

- Trang tĩnh nhỏ chưa cần Vue.
- Không nên thêm store nếu local state đủ.

## Gồm những gì

- [[Pinia]]
- [[Nuxt]]

## Nối mạnh

- [[Frontend Framework]] vì Vue là framework frontend phổ biến.
- [[Component]] vì component là đơn vị chính trong Vue.
- [[State Management]] vì Vue app thường cần phân biệt local state và store.
- [[Vite]] vì Vite là toolchain phổ biến cho Vue.

## Liên quan rộng

- UI architecture
- Reactive state
- Frontend routing

## Keywords / Từ khóa tìm kiếm

- Vue
- Vue.js
- Vue component
- Vue reactivity
- Vue Router
- Pinia
- Vue debugging

## Source trace

- Vue documentation
