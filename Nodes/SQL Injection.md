# SQL Injection

Aliases: SQLi, lỗi SQL injection

Type: Security

## Context / Ngữ cảnh

SQL Injection xuất hiện khi input không tin cậy được ghép vào SQL query và database diễn giải input đó như một phần của câu lệnh SQL. Nó thường gặp ở login/search/filter/sort/report/admin query, raw SQL trong repository/ORM, dynamic query builder và legacy code nối chuỗi query.

## Boundary / Ranh giới

### Nó là gì

SQL Injection là lỗi cho phép attacker thay đổi ý nghĩa SQL query bằng cách chèn syntax như quote, comment, boolean condition, UNION, subquery hoặc stacked statement nếu database/driver cho phép. Impact có thể là đọc/sửa/xóa dữ liệu, bypass login, leak secret, phá integrity hoặc trong vài môi trường dẫn tới RCE.

### Nó không phải là gì

SQL Injection không được phòng thủ chủ yếu bằng blocklist input. Cách chính là parameterized query/prepared statement, ORM/query builder dùng đúng, stored procedure an toàn và least privilege ở database user. Input validation có ích nhưng không thay thế parameter binding.

## Core Mechanism / Cơ chế lõi

Query an toàn tách SQL code khỏi data value. Prepared statement gửi query template và parameter riêng để database không parse parameter thành SQL syntax. Lỗi thường xảy ra khi code nối chuỗi raw SQL, tự build `WHERE/ORDER BY` từ input, hoặc dùng ORM escape hatch không bind parameter đúng.

## Project Role / Vai trò trong dự án

SQL Injection là node cần mở khi review endpoint có filter/search/sort, repository raw query, report builder, admin query hoặc dynamic SQL. Nó giúp team kiểm tra data access layer có bind parameter, allowlist column/order và DB role có quyền tối thiểu không.

## Output / Artifact nên có

- Query safety checklist: prepared statement, parameter binding, no string concatenation
- Dynamic SQL rule: allowlist column/table/order, không bind identifier bằng value parameter giả
- Test case cho quote/comment/boolean/UNION payload ở input quan trọng
- DB least privilege note: app user không có quyền vượt nhu cầu
- Logging rule: log query template/error đủ debug nhưng không lộ secret/PII

## Decision Checklist / Câu hỏi kiểm tra

- Input này có đi vào SQL query không?
- Query dùng prepared statement/parameter binding thật không?
- Dynamic identifier như column/sort/table có allowlist không?
- ORM có đang dùng raw SQL hoặc string interpolation không?
- DB user có quyền quá rộng như DROP/ALTER/superuser không?
- Error response có leak SQL syntax, table name hoặc stack trace không?
- Có test injection cho endpoint/filter/query này không?

## Failure Modes / Cách nó gây lỗi

- Login query nối chuỗi cho phép bypass bằng boolean condition.
- Search/filter ghép `%${input}%` vào SQL raw thay vì bind parameter.
- Sort column lấy trực tiếp từ query string và ghép vào `ORDER BY`.
- ORM dùng raw query escape hatch nhưng quên parameter binding.
- DB error trả thẳng cho client làm lộ schema/table/query.
- App DB user có quyền quá rộng nên injection impact lớn hơn cần thiết.

## Khi nào chưa cần hoặc dễ over-engineer

- Code không chạm SQL/database thì không cần control SQLi ở path đó.
- Không nên tự viết escaping SQL nếu driver/ORM đã hỗ trợ binding đúng.
- Không nên coi validation numeric/string là đủ nếu query vẫn ghép chuỗi.

## Gồm những gì

- [[Input Validation]]
- [[SQL]]

## Nối mạnh

- [[Input Validation]] vì input đi vào query vẫn cần validate shape/range nhưng không thay binding.
- [[Repository]] vì raw SQL/query thường nằm ở data access layer.
- [[ORM]] vì ORM có thể an toàn hoặc nguy hiểm tùy cách dùng raw query.
- [[Least Privilege]] vì DB account quyền thấp giảm blast radius khi SQLi xảy ra.
- [[Query Plan]] vì dynamic query/filter/sort thường liên quan performance và security cùng lúc.

## Liên quan rộng

- Application security
- Database security
- Secure coding
- Backend review

## Keywords / Từ khóa tìm kiếm

- SQL Injection
- SQLi
- lỗi SQL injection
- parameterized query
- prepared statement
- SQL parameter binding
- raw SQL injection
- dynamic SQL
- ORDER BY injection
- UNION injection
- boolean based injection
- SQL error leak
- SQL injection prevention
- SQL injection debugging

## Source trace

- OWASP SQL Injection Prevention Cheat Sheet
- OWASP Query Parameterization Cheat Sheet
