# Nuxt

Aliases: Nuxt, Nuxt.js

Type: Frontend Framework

## Context / Ngữ cảnh

Nuxt xuất hiện khi Vue app cần routing, rendering mode, server integration và project convention rõ hơn Vue thuần.

## Boundary / Ranh giới

### Nó là gì

Nuxt là meta-framework dựa trên Vue, hỗ trợ file-based routing, layouts, server/client rendering, data loading, runtime config và deployment preset.

### Nó không phải là gì

Nuxt không phải database hoặc toàn bộ backend business layer, dù có thể có server route/API route.

## Core Mechanism / Cơ chế lõi

Nuxt đọc file structure để tạo route, page, layout và build output. Data loading, runtime config, plugin và middleware quyết định behavior server/client của app.

## Project Role / Vai trò trong dự án

Dùng node này khi debug routing, SSR/CSR, data loading, middleware, runtime config, deployment target hoặc hydration trong Vue ecosystem.

## Output / Artifact nên có

- Route/page map
- Rendering mode decision
- Data loading convention
- Runtime config note
- Deploy target note

## Decision Checklist / Câu hỏi kiểm tra

- Route này render ở server hay client?
- Data loading chạy ở đâu?
- Runtime config có phân biệt public/private không?
- Middleware có redirect hoặc auth đúng không?
- Deploy target có hỗ trợ feature đang dùng không?

## Failure Modes / Cách nó gây lỗi

- Server/client render khác nhau gây hydration issue.
- Runtime config bị nhầm public/private boundary.
- Route middleware redirect sai.
- Data loading trùng hoặc stale.
- Build target không khớp hosting.

## Khi nào chưa cần hoặc dễ over-engineer

- Vue SPA đơn giản có thể chưa cần Nuxt.
- Không nên dùng meta-framework nếu static/client app đơn giản đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Vue]] vì Nuxt được xây trên Vue.
- [[SSR]] vì Nuxt thường dùng server-side rendering.
- [[CSR]] vì Nuxt vẫn có behavior phía client.
- [[Hydration]] vì Nuxt page có thể hydrate trên client.
- [[Frontend Framework]] vì Nuxt là meta-framework frontend.

## Liên quan rộng

- Vue ecosystem
- Routing
- Rendering mode
- Deployment

## Keywords / Từ khóa tìm kiếm

- Nuxt
- Nuxt.js
- Vue meta-framework
- Nuxt routing
- Nuxt SSR
- runtime config
- Nuxt debugging

## Source trace

- Nuxt documentation
- Vue documentation
