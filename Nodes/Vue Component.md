# Vue Component

Aliases: Vue Component, Vue SFC

Type: Frontend Framework

## Context / Ngữ cảnh

Vue Component xuất hiện khi Vue app cần chia UI thành unit có template, state, props, event, lifecycle và style riêng.

## Boundary / Ranh giới

### Nó là gì

Vue Component là đơn vị UI trong Vue, thường được viết dưới dạng Single File Component với template, script và style để render một phần giao diện.

### Nó không phải là gì

Vue Component không phải nơi nhét mọi logic của app. Business logic, API access và global state nên có boundary rõ để component không phình quá lớn.

## Core Mechanism / Cơ chế lõi

Component nhận props, giữ local reactive state, emit event, dùng computed/watch/lifecycle hook và render template theo reactivity system của Vue.

## Project Role / Vai trò trong dự án

Dùng node này khi debug props/event flow, reactive state, component reuse, lifecycle side effect hoặc tách UI trong Vue/Nuxt app.

## Output / Artifact nên có

- Component props/emits contract
- Local state/computed/watch note
- Slot usage nếu có
- Lifecycle side effect rule
- Component test/story nếu quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Component nhận props gì và emit event gì?
- State này local hay global/store?
- Watch/computed có side effect không?
- Slot có contract rõ không?
- Component có quá nhiều responsibility không?

## Failure Modes / Cách nó gây lỗi

- Mutate props trực tiếp làm data flow rối.
- Watch quá rộng gây side effect khó đoán.
- Component phình thành god component.
- Slot/emit contract không rõ làm parent-child coupling cao.
- Lifecycle hook gọi API không cleanup hoặc race.

## Khi nào chưa cần hoặc dễ over-engineer

- UI nhỏ, chưa reuse có thể giữ component đơn giản.
- Không nên tách component quá sớm nếu boundary props/emits chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Vue]] vì Vue Component là đơn vị UI của Vue.
- [[Component]] vì đây là một dạng component frontend.
- [[State Management]] vì component phải quyết định state local/global.
- [[Nuxt]] vì Nuxt page/layout cũng dựa trên Vue component.

## Liên quan rộng

- Single File Component
- Props emits
- Vue reactivity

## Keywords / Từ khóa tìm kiếm

- Vue Component
- Vue SFC
- props emits
- computed watch
- Vue lifecycle
- Vue component debugging

## Source trace

- Vue documentation
- Nuxt documentation
