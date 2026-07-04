# SPA

Aliases: Single Page Application, ứng dụng một trang

Type: Web Development

## Context / Ngữ cảnh

SPA xuất hiện khi web app tải một HTML/app shell ban đầu rồi dùng JavaScript để điều hướng, gọi API và cập nhật UI ở browser mà không reload toàn bộ trang. Nó thường dùng cho dashboard, admin panel, SaaS app, internal tool hoặc app có nhiều trạng thái tương tác phía client.

## Boundary / Ranh giới

### Nó là gì

SPA là kiến trúc web trong đó client-side app giữ phần lớn state/UI routing và giao tiếp với backend qua API. Browser tải bundle, router client map URL sang page/component, app gọi API để lấy dữ liệu, rồi render/update DOM theo state hiện tại.

### Nó không phải là gì

SPA không tự đồng nghĩa với frontend hiện đại hoặc performance tốt. Nếu bundle lớn, API chậm, cache sai, route fallback thiếu hoặc state management rối, SPA có thể first load chậm và khó debug. SPA cũng không thay thế API contract, auth flow hoặc server-side access control.

## Core Mechanism / Cơ chế lõi

SPA bắt đầu từ app shell, tải JavaScript/CSS bundle, initialize router/state, gọi API, render UI và điều hướng bằng History API hoặc hash route. Các boundary quan trọng gồm client-side routing, API fetching, auth token/session, browser cache, code splitting, error boundary và server fallback cho deep link.

## Project Role / Vai trò trong dự án

SPA là node cần mở khi thiết kế frontend/backend split, deploy static frontend, debug refresh route 404, API CORS/auth lỗi, bundle load chậm hoặc state client lệch dữ liệu server. Nó giúp team phân biệt lỗi nằm ở browser route, server fallback, API endpoint, auth/session hay static asset deployment.

## Output / Artifact nên có

- Frontend route map: URL → page/component → required API calls
- API contract list cho SPA/backend boundary
- Auth/session/token storage decision
- Build/deploy config: base path, asset URL, cache policy, fallback to index.html
- Performance budget: bundle size, code splitting, LCP/TTI, API waterfall
- Error/loading/empty-state checklist cho route chính

## Decision Checklist / Câu hỏi kiểm tra

- App có cần SEO/first HTML tốt không, hay SPA sau login là đủ?
- Server/static host có fallback đúng về `index.html` cho client routes không?
- API calls có contract, error handling và auth refresh rõ không?
- Bundle size/code splitting có phù hợp thiết bị/network user không?
- State client có thể stale hoặc lệch source of truth không?
- Token/session được lưu ở đâu và có rủi ro XSS/CSRF không?
- Deploy asset mới có cache-busting để tránh user tải bundle cũ không?

## Failure Modes / Cách nó gây lỗi

- Refresh deep link `/dashboard/settings` trả 404 vì server không fallback về app shell.
- Bundle quá lớn làm first load chậm dù backend khỏe.
- API waterfall nhiều tầng làm trang tương tác chậm.
- Token lưu sai chỗ làm tăng rủi ro XSS hoặc auth bug.
- Browser/CDN cache giữ asset cũ làm frontend gọi API version mới/sai.
- Client state stale khiến UI hiển thị dữ liệu cũ hoặc ghi đè dữ liệu mới từ server.
- Thiếu error boundary/loading state làm lỗi API biến thành màn hình trắng.

## Khi nào chưa cần hoặc dễ over-engineer

- Website content/marketing cần SEO và ít interaction có thể dùng SSR/SSG hoặc server-rendered pages đơn giản hơn.
- Form/app nhỏ có thể không cần SPA framework lớn nếu progressive enhancement đủ.
- Không nên chọn SPA chỉ vì quen frontend framework nếu user cần first content/SEO và content ít động.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CSR]] vì SPA thường render UI bằng client-side rendering.
- [[Route]] vì SPA phụ thuộc client-side routing và server fallback đúng.
- [[API Contract]] vì SPA/backend giao tiếp chủ yếu qua API contract.
- [[CORS]] vì SPA gọi API cross-origin thường gặp CORS/auth boundary.
- [[Stale Cache]] vì static asset/API cache sai có thể làm SPA chạy bundle hoặc data cũ.

## Liên quan rộng

- Frontend architecture
- Browser runtime
- Static deployment
- User experience

## Keywords / Từ khóa tìm kiếm

- SPA
- Single Page Application
- ứng dụng một trang
- client side routing
- app shell
- static frontend
- deep link 404
- index.html fallback
- API driven frontend
- frontend bundle
- code splitting
- client state
- SPA auth
- SPA deployment
- SPA debugging

## Source trace

- MDN SPA glossary
- web.dev rendering documentation
