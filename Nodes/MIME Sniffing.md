# MIME Sniffing

Aliases: MIME Sniffing, MIME sniffing, content sniffing, đoán MIME

Type: Security Attack Pattern

## Context / Ngữ cảnh

MIME Sniffing xuất hiện khi browser hoặc client cố đoán content type thực tế của response thay vì chỉ tin `Content-Type` header. Nó quan trọng trong file upload/download, static asset hosting, object storage, preview file, user-generated content và API trả file.

## Boundary / Ranh giới

### Nó là gì

MIME Sniffing là behavior browser/client phân tích bytes đầu hoặc context để tự suy đoán file là HTML, JavaScript, image, text, JSON hoặc binary. Nếu server khai báo sai content type hoặc cho browser sniff, file tưởng là harmless có thể bị diễn giải như executable content và dẫn tới XSS/download risk.

### Nó không phải là gì

MIME Sniffing không phải malware scan và không chứng minh file an toàn. Nó cũng không chỉ là vấn đề frontend; backend/storage/proxy phải set đúng `Content-Type`, `Content-Disposition` và `X-Content-Type-Options: nosniff` để browser không tự đoán nguy hiểm.

## Core Mechanism / Cơ chế lõi

Server trả response với `Content-Type`. Nếu header thiếu/sai và browser được phép sniff, browser có thể nhìn nội dung để quyết định cách xử lý. Defense gồm xác định MIME bằng allowlist/magic byte khi upload, set `Content-Type` đúng khi serve, dùng `nosniff`, và với file user upload nhạy cảm thì dùng `Content-Disposition: attachment` hoặc serve từ domain tách biệt.

## Project Role / Vai trò trong dự án

MIME Sniffing là node cần mở khi làm file upload security, CDN/object storage static hosting, preview attachment hoặc download API. Nó giúp team tránh tình huống user upload HTML/SVG/script nhưng browser execute khi người khác mở link.

## Output / Artifact nên có

- File serving policy: `Content-Type`, `Content-Disposition`, `nosniff`
- Upload validation rule: extension, declared type, magic byte, allowlist
- Preview/download decision: inline preview hay forced attachment
- Storage/CDN metadata mapping cho content type
- Test case: HTML disguised as image/text, SVG script, wrong content type, missing nosniff

## Decision Checklist / Câu hỏi kiểm tra

- Response file có `Content-Type` đúng và được kiểm soát không?
- Có set `X-Content-Type-Options: nosniff` cho script/style/download path không?
- File user upload có được serve inline trên cùng origin với app không?
- SVG/HTML/PDF có được preview hay buộc download?
- Object storage/CDN có giữ metadata content type đúng sau upload không?
- Browser có thể diễn giải file text/plain/octet-stream thành HTML/script không?
- Có dùng domain/bucket tách biệt cho user-generated content không?

## Failure Modes / Cách nó gây lỗi

- User upload file `.txt` chứa HTML/JS, server serve inline và browser execute.
- SVG upload được preview inline và chứa script/event handler.
- Object storage metadata sai làm file nguy hiểm được trả `text/html`.
- Thiếu `nosniff` khiến browser cố đoán content nguy hiểm.
- CDN cache response với content type sai sau deploy/config change.
- API trả JSON với content type sai làm browser/client xử lý lệch security expectation.

## Khi nào chưa cần hoặc dễ over-engineer

- File chỉ được backend xử lý nội bộ, không bao giờ serve cho browser, risk MIME sniffing thấp hơn.
- Không nên chỉ dựa vào extension để quyết định content type.
- Không nên preview inline file user upload nếu không có sanitizer/sandbox/domain tách biệt rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Security Header]] vì `X-Content-Type-Options: nosniff` là header phòng thủ trực tiếp.
- [[File Upload Security]] vì uploaded file thường là nguồn MIME spoofing/sniffing risk.
- [[XSS]] vì MIME sniffing sai có thể biến file thành script/HTML được execute.
- [[Object Storage]] vì object metadata content type quyết định file được serve ra sao.
- [[CDN]] vì CDN có thể cache hoặc forward content type sai.

## Liên quan rộng

- Browser behavior
- User-generated content
- File download security
- Static asset hosting

## Keywords / Từ khóa tìm kiếm

- MIME Sniffing
- MIME sniffing
- content sniffing
- đoán MIME
- X-Content-Type-Options
- nosniff
- Content-Type
- Content-Disposition
- inline preview
- file download security
- SVG XSS
- MIME spoofing
- browser sniffing
- MIME sniffing debugging

## Source trace

- OWASP Secure Headers Project
- MDN Web Docs / X-Content-Type-Options
