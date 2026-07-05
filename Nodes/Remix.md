# Remix

Aliases: Remix, Remix Run

Type: Frontend Framework

## Context / Ngữ cảnh

Remix xuất hiện khi React app cần routing, server-side data loading, form/action flow và progressive enhancement rõ ràng.

## Boundary / Ranh giới

### Nó là gì

Remix là web framework dựa trên React, tập trung vào nested routes, loaders, actions, server/client data flow và web platform primitives.

### Nó không phải là gì

Remix không phải chỉ là React router đơn giản. Nó định nghĩa cả cách load data, mutate data, handle form và render route boundary.

## Core Mechanism / Cơ chế lõi

Route file định nghĩa UI component, loader để đọc data và action để xử lý mutation. Framework điều phối request/response, nested route data, error boundary và client navigation.

## Project Role / Vai trò trong dự án

Dùng node này khi debug route data, form submission, server/client boundary, nested layout, error boundary hoặc deployment adapter của React app.

## Output / Artifact nên có

- Route map
- Loader/action contract
- Error boundary decision
- Data mutation flow
- Deployment adapter note

## Decision Checklist / Câu hỏi kiểm tra

- Data được load ở route nào?
- Mutation đi qua action nào?
- Error boundary có bắt đúng scope không?
- Route nesting có làm data reload dư không?
- Server/client code có bị trộn sai boundary không?

## Failure Modes / Cách nó gây lỗi

- Loader/action trả data shape không khớp component.
- Server-only code bị import sang client bundle.
- Nested route reload hoặc cache behavior khó hiểu.
- Form/action thiếu validation hoặc error state.
- Deployment adapter không khớp runtime.

## Khi nào chưa cần hoặc dễ over-engineer

- React SPA đơn giản có thể dùng router/client data fetching nhẹ hơn.
- Không nên dùng full-stack framework nếu app chỉ là static UI nhỏ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[React]] vì Remix dùng React component model.
- [[SSR]] vì Remix thường render trên server.
- [[Route]] vì routing là cơ chế lõi của Remix.
- [[Validation]] vì action/form mutation cần validate input.
- [[Frontend Framework]] vì Remix là framework frontend/full-stack web.

## Liên quan rộng

- Web platform
- Nested routing
- Server data loading

## Keywords / Từ khóa tìm kiếm

- Remix
- Remix Run
- React framework
- Remix loader
- Remix action
- nested routes
- Remix debugging

## Source trace

- Remix documentation
- React documentation
