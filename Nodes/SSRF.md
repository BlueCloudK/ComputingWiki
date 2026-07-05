# SSRF

Aliases: Server-Side Request Forgery, giả mạo request phía server

Type: Security

## Context / Ngữ cảnh

SSRF xuất hiện khi attacker có thể điều khiển server gửi HTTP/network request tới URL hoặc host do attacker chọn. Nó thường gặp ở feature fetch URL, webhook tester, image import, PDF generator, link preview, proxy endpoint, cloud metadata access, internal admin API hoặc agent/tool có khả năng gọi network.

## Boundary / Ranh giới

### Nó là gì

SSRF là lỗi cho phép attacker dùng server như một proxy để truy cập resource mà attacker không truy cập trực tiếp được: localhost, private IP, cloud metadata endpoint, internal service, admin panel hoặc database/API nội bộ. Impact phụ thuộc network reachability và credential gắn với server.

### Nó không phải là gì

SSRF không chỉ là validate URL string. DNS rebinding, redirect, IPv6, encoded IP, private range, protocol scheme và proxy behavior đều có thể bypass check đơn giản. SSRF cũng không chỉ là lỗi backend web; agent/tool, serverless function và worker queue có egress network đều có thể bị ảnh hưởng.

## Core Mechanism / Cơ chế lõi

App nhận URL/host từ input rồi server-side client gửi request. Nếu không có allowlist và egress control, attacker trỏ URL tới internal address hoặc dùng redirect/DNS trick để đổi đích. Defense gồm allowlist host/scheme, block private/link-local ranges sau DNS resolve, disable unsafe redirects, metadata endpoint protection, network egress policy và response filtering.

## Project Role / Vai trò trong dự án

SSRF là node cần mở khi app có “fetch from URL”, import ảnh/file từ link, preview link, webhook callback, crawler, AI agent/browser tool hoặc service gọi URL do user cấu hình. Nó giúp team kiểm soát server được gọi đi đâu và internal network nào không bao giờ được chạm tới.

## Output / Artifact nên có

- URL fetch policy: allowed schemes, host allowlist, port allowlist, max redirects
- DNS/IP validation rule: block localhost, private IP, link-local, metadata IP, internal DNS
- Egress network policy/firewall/service mesh rule nếu production hỗ trợ
- Timeout/size limit/response handling cho fetched content
- Test case cho localhost, private IP, IPv6, encoded IP, redirect, DNS rebinding và metadata endpoint

## Decision Checklist / Câu hỏi kiểm tra

- User/third-party có thể điều khiển URL/host/path nào không?
- Server có network access tới private service hoặc cloud metadata không?
- Allowlist host/scheme có rõ không hay chỉ blocklist?
- Có validate IP sau DNS resolve và sau redirect không?
- Redirect có thể đổi từ public host sang internal host không?
- Response từ internal request có bị trả lại cho attacker không?
- Có egress policy để chặn kể cả khi app validation fail không?

## Failure Modes / Cách nó gây lỗi

- Link preview fetch `http://169.254.169.254/` và lộ cloud metadata/token.
- URL validator chỉ block `127.0.0.1` nhưng bỏ sót IPv6, decimal/octal IP hoặc DNS rebinding.
- App cho follow redirect từ allowed domain sang private IP.
- Internal admin API không auth vì nghĩ chỉ private network truy cập được, nhưng SSRF gọi được.
- Server fetch file rất lớn hoặc slow endpoint gây resource exhaustion.
- AI/browser tool được phép truy cập URL tùy ý và chạm nội bộ không kiểm soát.

## Khi nào chưa cần hoặc dễ over-engineer

- App không có server-side URL fetch hoặc egress network không đáng kể thì SSRF risk thấp.
- Không nên chỉ dựa vào regex URL; cần network-level guard nếu impact cao.
- Không nên allow arbitrary URL fetch trong production nếu allowlist source là đủ cho use case.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Input Validation]] vì URL/host từ user là input không tin cậy cần canonicalize/allowlist.
- [[Network Segmentation]] vì egress policy/segmentation giảm blast radius khi SSRF xảy ra.
- [[Secret]] vì SSRF thường nhằm lấy metadata token/API credential.
- [[Resource Exhaustion]] vì URL fetch có thể bị dùng để kéo file lớn/slow response.
- [[AI Agent]] vì agent/tool có network access có thể tạo SSRF-like risk.

## Liên quan rộng

- Cloud metadata security
- Egress control
- Internal service exposure
- URL parsing safety

## Keywords / Từ khóa tìm kiếm

- SSRF
- Server-Side Request Forgery
- giả mạo request phía server
- server side URL fetch
- cloud metadata endpoint
- 169.254.169.254
- localhost SSRF
- private IP bypass
- DNS rebinding
- redirect SSRF
- egress allowlist
- metadata token leak
- SSRF prevention
- SSRF debugging

## Source trace

- OWASP SSRF Prevention Cheat Sheet
