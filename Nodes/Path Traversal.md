# Path Traversal

Aliases: Directory Traversal, traversal path

Type: Security

## Context / Ngữ cảnh

Path Traversal xuất hiện khi application nhận input liên quan tới file path, filename, upload/download path, template path hoặc static asset path và dùng input đó để đọc/ghi file trên filesystem. Nó thường gặp ở download endpoint, file preview, log viewer, image serving, archive extraction và plugin/template loader.

## Boundary / Ranh giới

### Nó là gì

Path Traversal là lỗi cho phép attacker dùng chuỗi như `../`, encoded path, symlink hoặc path absolute để vượt khỏi thư mục được phép và truy cập file ngoài boundary. Mục tiêu thường là đọc secret/config/source code hoặc ghi file vào vị trí nhạy cảm.

### Nó không phải là gì

Path Traversal không phải mọi lỗi file upload/download. Nếu vấn đề là file type độc hại, executable upload hoặc storage permission thì cần gọi đúng node khác. Path Traversal tập trung vào việc user-controlled path phá base directory/scope mà hệ thống định ra.

## Core Mechanism / Cơ chế lõi

Ứng dụng nhận path từ user, nối với base directory, rồi filesystem resolve path thật. Nếu không normalize/canonicalize và kiểm tra path resolved vẫn nằm dưới base directory, attacker có thể dùng `../`, URL encoding, unicode/alternate separator, symlink hoặc absolute path để thoát thư mục.

## Project Role / Vai trò trong dự án

Path Traversal là node cần mở khi thiết kế file API, upload/download service, static file server hoặc bất kỳ chỗ nào nhận filename từ user. Nó giúp team review base directory enforcement, allowlist file id, storage key, permission và test case path nguy hiểm.

## Output / Artifact nên có

- File access policy: base directory, allowed file types, allowed operation read/write
- Mapping file id/storage key thay vì tin raw path từ user
- Path normalization/canonicalization check và base directory enforcement
- Test case cho `../`, encoded traversal, absolute path, symlink và Windows/Unix separator
- Log/alert cho blocked traversal attempt trên endpoint file

## Decision Checklist / Câu hỏi kiểm tra

- Endpoint có nhận filename/path trực tiếp từ user không?
- Có dùng file id/storage key thay vì raw path không?
- Path sau khi canonicalize có được kiểm tra vẫn nằm trong base directory không?
- Có xử lý URL encoded path, double encoding, separator khác nhau và symlink không?
- Quyền filesystem của process có bị giới hạn theo least privilege không?
- File download/upload có test traversal case cho Linux và Windows path không?
- Error response có lộ path thật của server không?

## Failure Modes / Cách nó gây lỗi

- Attacker đọc file nhạy cảm như config, secret, source code hoặc system file.
- Endpoint download cho phép `../` thoát khỏi thư mục upload của user.
- Archive extraction ghi file ra ngoài thư mục đích qua path trong zip/tar.
- Symlink trong thư mục allowed trỏ tới file ngoài scope nhưng app chỉ check string prefix.
- Normalize path sai do encoded separator hoặc khác biệt Windows/Unix.
- Process chạy quyền quá rộng nên traversal thành data breach nghiêm trọng.

## Khi nào chưa cần hoặc dễ over-engineer

- Nếu app không nhận bất kỳ file path/user filename nào và không phục vụ file động, risk này thấp hơn.
- Không nên cho user chọn raw server path nếu có thể dùng opaque file id hoặc object storage key.
- Không nên tự viết path sanitizer phức tạp nếu framework/storage layer đã có primitive an toàn hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[File Upload Vulnerability]] vì upload/extract path sai có thể dẫn tới traversal hoặc ghi file ngoài scope.
- [[Access Control]] vì file access phải kiểm tra user có quyền với file đó không.
- [[Input Validation]] vì user-controlled path cần validate/canonicalize nghiêm ngặt.
- [[Least Privilege]] vì quyền filesystem giới hạn giúp giảm impact khi traversal xảy ra.

## Liên quan rộng

- Application security
- File storage design
- Backend review
- Secure download endpoint

## Keywords / Từ khóa tìm kiếm

- Path Traversal
- Directory Traversal
- traversal path
- dot dot slash
- ../ attack
- file path traversal
- canonical path
- path normalization
- base directory check
- arbitrary file read
- arbitrary file write
- zip slip
- symlink traversal
- secure file download
- path traversal testing

## Source trace

- OWASP Path Traversal
- OWASP Testing Guide
