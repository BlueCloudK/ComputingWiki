# SSR

Aliases: Server Side Rendering, render phía server

Type: Web Development

## Context / Ngữ cảnh

SSR xuất hiện khi web app cần render HTML ở server trước khi gửi về browser để cải thiện first load, SEO, social preview, data-fetching boundary hoặc performance trên thiết bị yếu. Nó thường gặp trong Next.js/Nuxt/SvelteKit/Razor Pages hoặc framework có server render pipeline.

## Boundary / Ranh giới

### Nó là gì

SSR là cách server chạy render logic, lấy dữ liệu cần thiết, tạo HTML ban đầu và gửi cho client. Sau đó browser có thể hydrate để biến HTML tĩnh thành app tương tác. SSR tạo boundary rõ giữa code chạy server và code chạy browser.

### Nó không phải là gì

SSR không tự làm web app nhanh hoặc SEO tốt nếu data fetch chậm, cache sai, hydration lỗi hoặc HTML vẫn thiếu nội dung quan trọng. SSR cũng không giống static generation hoàn toàn; SSR thường chạy theo request hoặc theo cơ chế cache/revalidate, nên phải quan tâm latency, request-specific data và server cost.

## Core Mechanism / Cơ chế lõi

Request vào server route, server fetch data, render component/page thành HTML, gửi HTML cho browser, rồi browser tải JavaScript và hydrate event handler/state. Các điểm nhạy cảm gồm server-only code, client-only API như `window`, hydration mismatch, cache boundary, auth/session data, streaming và error handling khi data fetch fail.

## Project Role / Vai trò trong dự án

SSR là node cần mở khi trang cần SEO/first contentful paint tốt, hoặc khi bug chỉ xảy ra giữa server render và client hydrate. Nó giúp team quyết định page nào SSR, page nào CSR/static, data nào cache được, data nào user-specific, và metric nào đo server render latency.

## Output / Artifact nên có

- Rendering decision per route/page: SSR, CSR, SSG, ISR hoặc hybrid
- Data fetching plan: server-only data, user-specific data, cache/revalidate rule
- Hydration test/checklist cho state, locale/timezone, random id và browser-only API
- Metrics: TTFB, FCP/LCP, server render time, hydration time, error rate
- Fallback/error boundary cho data fetch hoặc server render failure

## Decision Checklist / Câu hỏi kiểm tra

- Page này cần SEO/social preview hoặc first load nhanh hơn CSR không?
- Data có user-specific/private không, có được cache shared không?
- Server render có dùng API chỉ tồn tại ở browser như `window`, `localStorage` không?
- HTML server và render client có thể mismatch vì time/random/locale/auth state không?
- TTFB có tăng quá cao vì fetch data chậm không?
- Hydration cost có làm trang tương tác chậm không?
- Error/fallback khi server data fetch fail là gì?

## Failure Modes / Cách nó gây lỗi

- Hydration mismatch làm UI nhấp nháy, warning hoặc event/state sai.
- Dùng `window`/`document` trong server render làm request fail.
- Cache SSR sai làm user này thấy dữ liệu user khác hoặc dữ liệu cũ.
- Data fetch chậm làm TTFB cao dù HTML được render server-side.
- Server render crash làm toàn trang 500 thay vì fallback ở client.
- Bundle/hydration quá nặng làm first HTML có nhưng user chưa tương tác được lâu.

## Khi nào chưa cần hoặc dễ over-engineer

- App nội bộ sau login, ít cần SEO và chấp nhận loading client có thể dùng CSR đơn giản hơn.
- Không nên SSR mọi page nếu phần lớn nội dung user-specific, dynamic và khó cache.
- Không nên chọn SSR chỉ vì framework hỗ trợ; cần đo trade-off TTFB, complexity và hydration cost.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CSR]] vì SSR thường được so sánh với client-side rendering.
- [[SPA]] vì SPA route/CSR có trade-off khác SSR.
- [[Hydration]] vì hydration là bước nối HTML server với app client tương tác.
- [[Cache]] vì SSR performance và privacy phụ thuộc cache boundary đúng.
- [[Route]] vì SSR thường được quyết định theo từng route/page.

## Liên quan rộng

- Web performance
- SEO
- Frontend architecture
- Data fetching

## Keywords / Từ khóa tìm kiếm

- SSR
- Server Side Rendering
- render phía server
- server render
- hydration
- hydration mismatch
- TTFB
- FCP
- LCP
- SEO rendering
- data fetching server side
- user specific cache
- Next.js SSR
- SSR debugging
- rendering strategy

## Source trace

- Next.js documentation
- web.dev rendering documentation
