# Same Origin Policy

Aliases: SOP, same-origin policy, chính sách cùng origin

Type: Web Security / Browser

## Context / Ngữ cảnh

Same Origin Policy là luật bảo mật nền của browser giới hạn script từ một origin đọc hoặc thao tác dữ liệu của origin khác.

## Boundary / Ranh giới

### Nó là gì

Nó là browser security boundary dựa trên scheme, host và port. Nó quyết định trang web nào được đọc DOM, storage, cookie hoặc response của trang khác.

### Nó không phải là gì

Nó không phải cơ chế authentication và không tự bảo vệ API nếu backend vẫn cho phép request nguy hiểm đi qua.

## Core Mechanism / Cơ chế lõi

Browser so sánh origin của document/script với origin của tài nguyên đích. Nếu khác origin, browser chặn một số quyền đọc/truy cập trừ khi cơ chế như CORS cho phép.

## Project Role / Vai trò trong dự án

Same Origin Policy giúp debug lỗi CORS, cookie, iframe, browser storage và các boundary giữa frontend, backend và third-party domain.

## Output / Artifact nên có

- Origin matrix cho frontend, API và third-party domain
- CORS/cookie decision note nếu phải vượt boundary
- Browser test cho flow login, upload, API call hoặc embedded page

## Decision Checklist / Câu hỏi kiểm tra

- Frontend và API có cùng scheme, host, port không?
- Flow này cần đọc response cross-origin hay chỉ gửi request?
- Cookie có bị ảnh hưởng bởi SameSite, domain hoặc secure flag không?
- CORS rule có mở quá rộng so với origin cần thiết không?

## Failure Modes / Cách nó gây lỗi

- Debug nhầm backend vì browser chặn response trước khi app đọc được
- Mở CORS wildcard kèm credential làm lộ boundary bảo mật
- Nhầm subdomain là cùng origin trong khi browser coi là khác origin

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần phân tích sâu nếu app chỉ chạy một origin đơn giản
- Dễ over-engineer nếu thêm proxy/CORS layer trước khi xác định đúng origin mismatch

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CORS]] vì CORS là cơ chế nới quyền có kiểm soát trên nền Same Origin Policy
- [[Cookie]] vì cookie domain, SameSite và secure flag thường bị debug cùng origin boundary

## Liên quan rộng

- Browser security
- Frontend integration
- API boundary

## Keywords / Từ khóa tìm kiếm

- Same Origin Policy
- SOP
- same-origin policy
- browser origin
- cross-origin
- scheme host port
- CORS error
- chính sách cùng origin
- lỗi khác origin

## Source trace

- MDN Web Docs / Same-origin policy
- WHATWG HTML / origin
