# Security Engineering Path

## Mục tiêu

Path này giúp người đọc đi từ asset, identity, input boundary tới attack pattern và control thực tế trong application.

## Khi nào dùng path này

- Khi review security cho web/backend/API.
- Khi thiết kế auth, session, permission hoặc secret handling.
- Khi muốn hiểu attack path thay vì chỉ checklist chung.

## 1. Nhìn hệ thống như attack surface

- [[Security]] — bản đồ vùng lớn của security.
- [[Threat Modeling]] — xác định asset, actor, trust boundary và abuse case.
- [[Attack Surface]] — phần hệ thống attacker có thể tương tác.
- [[Least Privilege]] — giảm quyền để failure ít lan rộng.
- [[Audit Log]] — ghi dấu hành động nhạy cảm để điều tra.

## 2. Identity và access

- [[Authentication]] — xác minh danh tính.
- [[Authorization]] — kiểm soát quyền truy cập.
- [[Session Management]] — quản lý lifecycle của phiên.
- [[JWT]] — token format hay dùng trong API.
- [[MFA]] — giảm rủi ro khi password bị lộ.
- [[Token Revocation]] — vô hiệu hóa token trước khi hết hạn.

## 3. Input và output boundary

- [[Input Validation]] — chặn input sai hoặc nguy hiểm.
- [[Output Encoding]] — tránh dữ liệu thành executable content.
- [[XSS]] — script injection trên browser.
- [[SQL Injection]] — input làm thay đổi query SQL.
- [[Path Traversal]] — truy cập file ngoài vùng cho phép.
- [[File Upload Security]] — kiểm soát upload file.

## 4. Web/API attack patterns

- [[CSRF]] — lợi dụng browser gửi request có credential.
- [[CSRF Token]] — control chống CSRF cho state-changing request.
- [[SSRF]] — server bị ép gọi tới resource attacker chọn.
- [[IDOR]] — access object bằng ID mà thiếu authorization.
- [[RCE]] — attacker chạy code/lệnh trên server.
- [[CORS Misconfiguration]] — origin không đáng tin đọc response nhạy cảm.

## 5. Secret, crypto và transport

- [[Secret]] — dữ liệu nhạy như key/token/password.
- [[Password Storage]] — lưu password bằng hash phù hợp.
- [[Hashing]] — digest một chiều cho integrity/password use case.
- [[Salting]] — chống rainbow table cho password hash.
- [[TLS]] — bảo vệ kết nối bằng transport encryption.
- [[Encryption at Rest]] — bảo vệ dữ liệu khi lưu.
- [[Key Management]] — quản lý lifecycle của key.

## 6. Secure delivery

- [[Dependency Scanning]] — phát hiện dependency có lỗ hổng.
- [[Supply Chain Security]] — bảo vệ dependency, build và release.
- [[SBOM]] — inventory thành phần trong artifact.
- [[SAST]] — scan mã nguồn tĩnh.
- [[DAST]] — test app đang chạy.
- [[Security Monitoring]] — theo dõi signal bảo mật trong production.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Attack Surface
- Session hijacking
- Broken access control
- Secrets scanning
- Secure SDLC

## Related paths

- [[Backend Engineering Path]]
- [[API Design Path]]
- [[Web Application Path]]
- [[Cloud Infrastructure Path]]
