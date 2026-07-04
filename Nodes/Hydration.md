# Hydration

Aliases: Hydration, hydration, React hydration, gắn JS vào HTML

Type: Web Development

## Context / Ngữ cảnh

Hydration xuất hiện khi HTML đã được render sẵn từ server hoặc static generation, rồi browser tải JavaScript để gắn event handler, state và logic tương tác vào markup đó. Nó là cầu nối giữa SSR/SSG HTML ban đầu và app client-side có thể tương tác.

## Boundary / Ranh giới

### Nó là gì

Hydration là quá trình framework ở browser đọc DOM/HTML có sẵn, khớp nó với component tree phía client, rồi attach event listeners và state. Sau hydration, UI không chỉ là HTML tĩnh nữa mà trở thành app có thể xử lý click, form, route transition và state update.

### Nó không phải là gì

Hydration không phải render server và cũng không phải CSR thuần. SSR tạo HTML; hydration làm HTML đó sống ở browser. Nếu HTML server và render client không giống nhau, hydration có thể warning, replace DOM, mất state hoặc gây UI flicker.

## Core Mechanism / Cơ chế lõi

Server render HTML theo data/state tại thời điểm request/build. Browser nhận HTML, tải JS bundle, framework chạy lại component tree ở client, so sánh/khớp markup và attach event. Mismatch thường đến từ time/random, locale/timezone, auth state, browser-only API, feature flag khác nhau hoặc data cache khác giữa server và client.

## Project Role / Vai trò trong dự án

Hydration là node cần mở khi app SSR có warning mismatch, UI nhấp nháy sau load, button không click được ban đầu, state auth đổi sau client boot hoặc performance interactive chậm. Nó giúp team kiểm tra server/client boundary, deterministic render, browser-only code và hydration cost.

## Output / Artifact nên có

- Hydration checklist cho route/page SSR: deterministic markup, server data, client state
- Client-only component boundary cho code dùng `window`, `document`, localStorage hoặc browser API
- Test case cho locale/timezone, auth state, random id, date formatting và feature flag
- Metrics: hydration time, JS execution time, interaction delay, hydration error/warning count
- Fallback strategy: loading shell, dynamic import, partial hydration/islands nếu framework hỗ trợ

## Decision Checklist / Câu hỏi kiểm tra

- HTML server và render client có dùng cùng data/state không?
- Component có dùng time/random/locale/browser API làm markup khác nhau không?
- Auth/session state có được biết ở server hay chỉ biết sau client boot?
- Có component nào nên client-only thay vì hydrate từ server HTML không?
- Hydration JS có quá lớn làm trang nhìn thấy nhưng chưa tương tác được không?
- Warning hydration mismatch có được xem là lỗi cần sửa hay bị bỏ qua?
- Cache SSR có làm client hydrate với dữ liệu khác HTML ban đầu không?

## Failure Modes / Cách nó gây lỗi

- Hydration mismatch do server và client render khác nhau.
- UI flicker vì server render anonymous state rồi client đổi sang logged-in state.
- Button/form không hoạt động cho tới khi JS bundle tải và hydration xong.
- Browser-only API chạy trong server render làm SSR crash hoặc markup fallback sai.
- Hydration quá nặng làm Time to Interactive chậm dù HTML hiện sớm.
- Framework phải replace DOM vì mismatch, làm mất input state hoặc gây layout shift.

## Khi nào chưa cần hoặc dễ over-engineer

- CSR thuần không có SSR/SSG HTML cần hydrate thì không cần đào sâu hydration.
- Trang static ít tương tác có thể không cần hydrate toàn bộ app.
- Không nên tối ưu partial hydration/islands trước khi đo hydration cost thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[SSR]] vì hydration thường theo sau server-side rendering.
- [[CSR]] vì sau hydration, app tiếp tục chạy như client-side app.
- [[SPA]] vì nhiều framework SPA kết hợp SSR rồi hydrate client.
- [[JavaScript]] vì hydration phụ thuộc vào JS bundle chạy trong browser.
- [[Stale Cache]] vì dữ liệu/cache lệch giữa server và client có thể tạo mismatch.

## Liên quan rộng

- Frontend performance
- Browser runtime
- Rendering strategy
- User experience

## Keywords / Từ khóa tìm kiếm

- Hydration
- hydration
- React hydration
- gắn JS vào HTML
- hydration mismatch
- server client mismatch
- attach event listeners
- Time to Interactive
- partial hydration
- islands architecture
- client only component
- browser only API
- SSR hydration
- hydration debugging

## Source trace

- React hydration documentation
- Next.js documentation
- web.dev rendering documentation
