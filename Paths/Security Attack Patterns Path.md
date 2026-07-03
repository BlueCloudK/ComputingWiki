# Security Attack Patterns Path

## Mục tiêu

Path này giúp người đọc đi qua attack patterns theo thứ tự review phòng thủ: asset, identity, input, session, data, cloud, supply chain và response.

## Khi nào dùng path này

- Khi review security cho web/API/backend.
- Khi viết threat model hoặc abuse case.
- Khi muốn tạo regression test và monitoring cho security failure mode.

## 1. Asset và boundary

- [[Asset Inventory]] — biết tài sản nào cần bảo vệ.
- [[Threat Actor]] — xác định ai có thể lạm dụng hệ thống.
- [[Entry Point]] — biết input/route/integration nào mở ra attack path.
- [[Trust Boundary]] — thấy nơi mức tin cậy thay đổi.
- [[Abuse Case]] — mô tả cách feature có thể bị lạm dụng.

## 2. Identity và access

- [[Authentication Bypass]] — lỗi bỏ qua login/auth.
- [[Broken Access Control]] — lỗi quyền phổ biến nhất trong app.
- [[IDOR]] — truy cập object bằng ID khi thiếu authorization.
- [[Privilege Escalation]] — quyền thấp thành quyền cao.
- [[Session Hijacking]] — chiếm session/token user.

## 3. Input và injection

- [[Cross Site Scripting]] — script chạy trong browser user.
- [[SQL Injection]] — input làm sai query database.
- [[NoSQL Injection]] — injection vào query NoSQL.
- [[OS Command Injection]] — input đi vào command OS.
- [[Server Side Template Injection]] — template server bị lạm dụng.
- [[Path Traversal]] — thoát khỏi directory boundary.

## 4. Web/API abuse

- [[CSRF]] — browser gửi credential theo request ngoài ý định.
- [[SSRF]] — server bị ép gọi endpoint attacker chọn.
- [[Open Redirect]] — redirect tới destination không tin cậy.
- [[Rate Limit Bypass]] — né giới hạn request.
- [[Business Logic Abuse]] — flow hợp lệ bị dùng sai mục đích.

## 5. Cloud, container và supply chain

- [[Secret Exposure]] — secret/token/key bị lộ.
- [[Dependency Confusion]] — package manager cài nhầm package độc.
- [[Container Escape]] — vượt boundary container.
- [[Kubernetes Misconfiguration]] — cluster/object config sai.
- [[Cloud IAM Misconfiguration]] — cloud permission quá rộng hoặc trust sai.

## 6. Detection và response

- [[Security Monitoring]] — theo dõi signal bảo mật.
- [[Security Alert Triage]] — phân loại alert.
- [[Indicator of Compromise]] — dấu hiệu có thể đã bị compromise.
- [[Containment]] — giới hạn blast radius.
- [[Eradication]] — loại bỏ foothold/nguyên nhân.
- [[Recovery]] — khôi phục về trạng thái an toàn.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- WAF rule tuning
- Fraud detection
- Session anomaly detection
- Cloud security posture management
- Security chaos testing

## Related paths

- [[Security Engineering Path]]
- [[API Design Path]]
- [[Backend Engineering Path]]
- [[Linux Server Admin Path]]
