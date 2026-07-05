# Frontend Framework

Aliases: UI framework, web framework frontend, framework giao diện

Type: Web Development

## Context / Ngữ cảnh

Frontend Framework xuất hiện khi web app cần tổ chức UI thành component, quản lý state, routing, rendering, build và test ở quy mô lớn hơn một vài trang tĩnh. Ví dụ phổ biến gồm React, Vue, Angular, Svelte hoặc meta-framework như Next/Nuxt/SvelteKit.

## Boundary / Ranh giới

### Nó là gì

Frontend Framework là abstraction giúp xây UI theo component model, state update, render tree, event handling, routing và data fetching pattern. Nó quyết định cách code frontend được chia nhỏ, cách UI phản ứng với state, cách route/page render và cách build bundle chạy trong browser.

### Nó không phải là gì

Frontend Framework không phải design system, CSS framework, backend framework hoặc toàn bộ kiến trúc sản phẩm. Chọn framework không tự giải quyết UX, API contract, state ownership, performance, accessibility hoặc security. Framework cũng không thay thế hiểu browser/runtime cơ bản.

## Core Mechanism / Cơ chế lõi

App được chia thành component. Component nhận props/input, giữ hoặc đọc state, render UI, xử lý event và gọi API/data source. Framework/runtime cập nhật render tree khi state đổi, router map URL sang screen, build tool đóng gói code, và một số framework hỗ trợ SSR/hydration để tối ưu SEO/performance.

## Project Role / Vai trò trong dự án

Frontend Framework là node cần mở khi bắt đầu app web, debug state/render/routing, chọn CSR/SSR/SPA, hoặc chia responsibility giữa frontend/backend. Nó giúp team quyết định component tree, state boundary, routing map, data fetching strategy và test level.

## Output / Artifact nên có

- Framework decision note: lý do chọn, team familiarity, SSR/CSR need, ecosystem
- Component tree và routing map cho screen chính
- State ownership map: local, shared/global, server cache, URL state
- Data fetching/API contract pattern
- Build/test config: dev server, bundler, unit/component/e2e test

## Decision Checklist / Câu hỏi kiểm tra

- App là SPA, SSR, static site hay hybrid?
- UI có đủ phức tạp để cần framework không?
- State nằm ở component local, global store, server cache hay URL?
- SEO/first load/hydration có quan trọng không?
- Framework có phù hợp team skill, ecosystem và deploy target không?
- Component boundary có rõ hay mọi thứ gom thành page lớn?
- Bundle size, rerender và API waterfall có được đo không?

## Failure Modes / Cách nó gây lỗi

- Chọn framework/tool quá nặng cho app đơn giản.
- State rải rác làm UI stale, race hoặc khó debug.
- Component quá lớn, nhiều responsibility và side effect lẫn trong render.
- Hydration mismatch giữa SSR và client.
- Routing/data fetching lẫn lộn làm deep link, loading/error state hỏng.
- Bundle quá lớn hoặc rerender không kiểm soát làm UX chậm.

## Khi nào chưa cần hoặc dễ over-engineer

- Landing page tĩnh hoặc form rất nhỏ có thể dùng HTML/CSS/JS đơn giản.
- Không nên chọn framework chỉ vì trend nếu team chưa cần component/state/routing phức tạp.
- Không nên thêm global state/meta-framework trước khi biết failure mode thật.

## Gồm những gì

- [[State Management]]
- [[Component]]

## Nối mạnh

- [[SPA]] vì nhiều frontend framework được dùng để xây single-page app.
- [[SSR]] vì một số framework/meta-framework hỗ trợ server-side rendering.
- [[CSR]] vì client-side rendering là mode phổ biến của frontend framework.
- [[State Management]] vì framework quyết định state update/render behavior.
- [[Component]] vì component model là đơn vị cấu trúc chính của UI framework.

## Liên quan rộng

- Frontend architecture
- Browser runtime
- User experience
- Build tooling

## Keywords / Từ khóa tìm kiếm

- Frontend Framework
- UI framework
- web framework frontend
- framework giao diện
- React
- Vue
- Angular
- Svelte
- component model
- render tree
- frontend routing
- frontend state
- hydration
- frontend framework debugging

## Source trace

- React documentation
- Vue documentation
- Angular documentation
- Svelte documentation
