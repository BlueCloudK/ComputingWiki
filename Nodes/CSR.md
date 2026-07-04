# CSR

Aliases: Client Side Rendering, render phía client

Type: Web Development

## Context / Ngữ cảnh

CSR xuất hiện khi browser tải JavaScript bundle rồi tự render UI, fetch data và cập nhật DOM ở phía client. Nó thường là nền của SPA, dashboard, app sau login hoặc phần UI cần tương tác mạnh mà không cần server render HTML đầy đủ cho từng request.

## Boundary / Ranh giới

### Nó là gì

CSR là rendering strategy trong đó HTML ban đầu thường chỉ là app shell hoặc container rỗng, còn UI thật được tạo bởi JavaScript trong browser. Client chịu trách nhiệm routing, state, data fetching, error/loading state và DOM updates sau khi bundle được tải/chạy.

### Nó không phải là gì

CSR không phải lúc nào cũng là SPA, dù SPA thường dùng CSR. CSR cũng không tự làm app nhanh; nếu bundle lớn, API waterfall nhiều hoặc thiết bị yếu, user sẽ thấy blank/loading lâu. CSR không phù hợp mọi trang cần SEO, social preview hoặc first content có sẵn ngay từ server.

## Core Mechanism / Cơ chế lõi

Browser nhận HTML shell, tải JS/CSS assets, execute bundle, initialize app state/router, gọi API và render component vào DOM. Performance phụ thuộc vào bundle size, parse/execute time, network waterfall, caching, code splitting, hydration nếu kết hợp SSR, và khả năng xử lý loading/error trên client.

## Project Role / Vai trò trong dự án

CSR là node cần mở khi quyết định rendering strategy hoặc debug trang trắng, first load chậm, API loading lâu, route sau login, cache asset hoặc bundle version mismatch. Nó giúp team phân biệt vấn đề nằm ở server response, asset loading, JavaScript runtime, API fetch hay state/render logic.

## Output / Artifact nên có

- Rendering decision: route/page nào CSR, route/page nào SSR/SSG
- Bundle/performance budget: JS size, code splitting, lazy load, critical path
- API fetching plan: loading/error/empty state, retry, cancellation
- Static asset cache strategy và cache-busting build hash
- Browser monitoring: JS error, LCP, INP/TTI, API waterfall, blank screen rate

## Decision Checklist / Câu hỏi kiểm tra

- Page này có cần SEO/HTML nội dung ban đầu không?
- User có chấp nhận loading state trước khi API trả dữ liệu không?
- Bundle chính có quá lớn cho thiết bị/network mục tiêu không?
- API fetch có tạo waterfall khiến render chậm không?
- Asset cache có làm user chạy JS cũ với API mới không?
- Có error boundary để tránh một JS error thành màn hình trắng không?
- Có cần chuyển một phần sang SSR/SSG để cải thiện first load không?

## Failure Modes / Cách nó gây lỗi

- JS bundle lỗi hoặc không tải được làm user thấy trang trắng.
- Bundle lớn làm browser parse/execute lâu, đặc biệt trên mobile yếu.
- API waterfall khiến UI chờ nhiều round-trip trước khi hiển thị dữ liệu chính.
- Client-only auth/state làm UI nhấp nháy giữa anonymous/authenticated state.
- Cache asset sai làm frontend version cũ gọi API contract mới.
- Không có fallback/error boundary làm lỗi component phá toàn bộ app.

## Khi nào chưa cần hoặc dễ over-engineer

- Trang content/marketing/blog cần SEO tốt thường không nên dùng CSR thuần.
- UI đơn giản ít tương tác có thể dùng server-rendered HTML hoặc progressive enhancement.
- Không nên đưa toàn bộ app sang CSR nếu chỉ vài widget cần tương tác client.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[SPA]] vì SPA thường dùng CSR làm rendering strategy chính.
- [[SSR]] vì CSR và SSR là hai chiến lược render cần so sánh theo route.
- [[Hydration]] vì app SSR có thể hydrate để tiếp tục chạy logic client.
- [[JavaScript]] vì CSR phụ thuộc vào browser tải/chạy JS bundle.
- [[Stale Cache]] vì asset cache cũ có thể làm CSR app chạy sai version.

## Liên quan rộng

- Frontend performance
- Browser runtime
- Rendering strategy
- Static hosting

## Keywords / Từ khóa tìm kiếm

- CSR
- Client Side Rendering
- render phía client
- client render
- browser rendering
- app shell
- JavaScript bundle
- blank screen
- API waterfall
- code splitting
- lazy loading
- frontend performance
- CSR debugging
- rendering strategy

## Source trace

- web.dev rendering documentation
- MDN browser documentation
