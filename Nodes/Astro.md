# Astro

Aliases: Astro

Type: Frontend Framework

## Context / Ngữ cảnh

Astro xuất hiện khi site/app cần ưu tiên content, SEO, performance và chỉ hydrate JavaScript cho phần UI thật sự cần tương tác.

## Boundary / Ranh giới

### Nó là gì

Astro là web framework tập trung vào content-driven site, island architecture, static/server rendering và tích hợp nhiều UI framework như React/Vue/Svelte.

### Nó không phải là gì

Astro không phải SPA framework mặc định. Nó không giả định toàn bộ page phải chạy JavaScript trên client.

## Core Mechanism / Cơ chế lõi

Astro build page từ component/content, render HTML trước và chỉ hydrate island tương tác theo directive. Site có thể static generate hoặc server render tùy adapter.

## Project Role / Vai trò trong dự án

Dùng node này khi xây docs/blog/marketing site, debug hydration island, content collection, build output hoặc performance/SEO của frontend.

## Output / Artifact nên có

- Page/content structure
- Island hydration decision
- Adapter/deploy target
- Asset/build output note
- SEO/performance checklist

## Decision Checklist / Câu hỏi kiểm tra

- Page này có cần client JavaScript không?
- Component nào cần hydrate?
- Content source/schema nằm ở đâu?
- Build là static hay server-rendered?
- Adapter có khớp hosting không?

## Failure Modes / Cách nó gây lỗi

- Hydrate quá nhiều làm mất lợi thế performance.
- Component client/server boundary sai.
- Content schema lỏng làm build/runtime lỗi.
- Adapter/deploy target không hỗ trợ feature đang dùng.
- SEO/meta thiếu dù content render tốt.

## Khi nào chưa cần hoặc dễ over-engineer

- Dashboard/app tương tác nặng có thể dùng SPA/meta-framework khác phù hợp hơn.
- Không nên dùng island architecture nếu toàn app đều là realtime client UI.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[SSR]] vì Astro có thể render HTML phía server/build time.
- [[Hydration]] vì Astro dùng hydration có chọn lọc cho island.
- [[Frontend Framework]] vì Astro là framework web/frontend.
- [[Vite]] vì Astro toolchain dựa nhiều vào Vite ecosystem.

## Liên quan rộng

- Content site
- Island architecture
- Static site generation
- SEO performance

## Keywords / Từ khóa tìm kiếm

- Astro
- Astro framework
- island architecture
- content collection
- static site generation
- partial hydration
- Astro debugging

## Source trace

- Astro documentation
- Vite documentation
