# File Upload Security

Aliases: File Upload Security, file upload security, secure file upload, bảo mật upload file

Type: Security

## Context / Ngữ cảnh

File Upload Security xuất hiện khi user, partner hoặc system khác có thể gửi file vào application. Upload file là boundary rủi ro cao vì file có thể chứa malware, script, payload parser, path abuse, oversized content, spoofed MIME type hoặc dữ liệu nhạy cảm cần access control.

## Boundary / Ranh giới

### Nó là gì

File Upload Security là tập control để nhận, kiểm tra, lưu, xử lý và phục vụ file upload an toàn. Nó bao gồm allowlist file type, size limit, magic-byte/MIME check, filename sanitization, storage ngoài webroot, malware scan nếu cần, permission check, signed URL và xử lý parser/thumbnail/conversion an toàn.

### Nó không phải là gì

File Upload Security không chỉ là kiểm tra extension. Extension, `Content-Type` header và filename đều có thể bị giả mạo. Nó cũng không chỉ là input validation; file sau khi lưu/xử lý/phục vụ vẫn có thể gây XSS, RCE, path traversal, data leak hoặc resource exhaustion.

## Core Mechanism / Cơ chế lõi

Backend nhận file, enforce auth/authorization, kiểm tra size/count/type bằng allowlist, đổi tên file sang id an toàn, lưu ở storage tách biệt, quét hoặc xử lý trong sandbox nếu cần, ghi metadata, rồi phục vụ qua signed URL/proxy có permission. File không nên được execute như code và không nên lưu theo path do user điều khiển.

## Project Role / Vai trò trong dự án

File Upload Security là node cần mở khi làm avatar, document upload, import CSV/PDF, image processing, video conversion, object storage hoặc attachment system. Nó giúp team review toàn bộ lifecycle: upload → validate → store → process → serve → delete.

## Output / Artifact nên có

- Upload policy: allowed types, max size/count, storage bucket/path, retention
- Validation rule: magic byte/MIME/extension match, filename handling, parser limit
- Processing boundary: antivirus, sandbox, timeout, resource limit, queue
- Access control: owner/tenant permission, signed URL, private/public object rule
- Test case: double extension, MIME spoof, oversized file, traversal filename, executable payload

## Decision Checklist / Câu hỏi kiểm tra

- Ai được upload và ai được download file này?
- File type nào thật sự cần allow, và kiểm tra bằng gì ngoài extension?
- File lưu ở đâu, có nằm ngoài webroot/execution path không?
- Filename/path có do user điều khiển không?
- File có được parse/convert/thumbnail không, và process có sandbox/timeout không?
- Download/preview có thể gây XSS hoặc MIME sniffing không?
- File có chứa PII/secret và cần retention/delete policy không?

## Failure Modes / Cách nó gây lỗi

- Upload `.php`, `.jsp`, script hoặc polyglot rồi server execute như code.
- Filename `../../...` hoặc path trick dẫn tới path traversal/arbitrary write.
- MIME/extension spoof làm app preview file nguy hiểm như HTML/SVG/script.
- Image/PDF parser có vulnerability và bị payload file kích hoạt RCE.
- File quá lớn hoặc zip bomb làm cạn disk/CPU/memory.
- Object storage public nhầm làm lộ file riêng tư giữa user/tenant.

## Khi nào chưa cần hoặc dễ over-engineer

- App không nhận file từ user/third-party thì chưa cần control upload riêng.
- Upload nội bộ ít rủi ro có thể bắt đầu với allowlist, size limit và private storage trước.
- Không nên tự viết malware scanner/parser nếu provider/service đáng tin đã có.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Path Traversal]] vì filename/path upload có thể phá storage boundary.
- [[Input Validation]] vì file metadata/type/size/count đều là input không tin cậy.
- [[RCE]] vì parser hoặc executable upload có thể dẫn tới code execution.
- [[Object Storage]] vì upload thường được lưu và phục vụ qua object storage.
- [[MIME Sniffing]] vì browser có thể diễn giải file sai content-type khi preview/download.

## Liên quan rộng

- Malware scanning
- File processing
- Object storage security
- User-generated content

## Keywords / Từ khóa tìm kiếm

- File Upload Security
- file upload security
- secure file upload
- bảo mật upload file
- unrestricted file upload
- malicious file upload
- MIME spoofing
- magic byte validation
- double extension
- zip bomb
- file upload RCE
- signed URL
- object storage upload
- upload security debugging

## Source trace

- OWASP File Upload Cheat Sheet
- OWASP Unrestricted File Upload references
