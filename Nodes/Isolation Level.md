# Isolation Level

Aliases: transaction isolation, mức cô lập giao dịch

Type: Database Systems

## Context / Ngữ cảnh

Isolation Level xuất hiện khi nhiều transaction chạy song song và team cần biết transaction này có thể nhìn thấy thay đổi của transaction khác đến mức nào. Nó ảnh hưởng trực tiếp tới data correctness, race condition, lock behavior và throughput.

## Boundary / Ranh giới

### Nó là gì

Isolation Level là mức cô lập của transaction: database cho phép hoặc ngăn các hiện tượng như dirty read, non-repeatable read, phantom read, lost update, write skew và serialization anomaly. Các mức phổ biến gồm Read Committed, Repeatable Read và Serializable, nhưng behavior chi tiết phụ thuộc database engine.

### Nó không phải là gì

Isolation Level không phải nút “bật càng cao càng tốt”. Mức cao hơn có thể tăng lock wait, abort/retry hoặc giảm throughput. Nó cũng không thay thế unique constraint, atomic update, idempotency hoặc explicit lock khi invariant nghiệp vụ cần bảo vệ rõ.

## Core Mechanism / Cơ chế lõi

Database dùng MVCC, lock, snapshot, predicate lock hoặc conflict detection để cô lập transaction. Isolation yếu hơn cho concurrency cao hơn nhưng có thể thấy dữ liệu thay đổi giữa statement. Isolation mạnh hơn tạo snapshot ổn định hơn hoặc bắt conflict, nhưng app phải xử lý retry/abort.

## Project Role / Vai trò trong dự án

Isolation Level là node cần mở khi debug oversell, double booking, lost update, báo cáo đọc không nhất quán, deadlock, serialization failure hoặc transaction chậm do lock. Nó giúp team chọn đúng mức cô lập cho từng transaction thay vì đổi global config mù.

## Output / Artifact nên có

- Isolation decision note cho transaction quan trọng
- Concurrency test: hai hoặc nhiều transaction chạy song song với expected result
- Invariant/race condition mapping: lost update, phantom, write skew, non-repeatable read
- Retry policy cho deadlock/serialization failure
- Database-specific note: PostgreSQL/MySQL/SQL Server behavior khác nhau thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Transaction này cần view ổn định xuyên suốt hay chỉ từng statement?
- Race condition nào cần chặn: lost update, phantom, write skew hay dirty read?
- Có thể dùng constraint/atomic update/lock thay vì tăng isolation không?
- Database đang dùng định nghĩa Read Committed/Repeatable Read/Serializable ra sao?
- Nếu transaction bị abort do conflict, app có retry an toàn không?
- Isolation cao hơn có làm lock wait hoặc throughput tệ hơn không?
- Test concurrency có mô phỏng tình huống thật không?

## Failure Modes / Cách nó gây lỗi

- Dùng Read Committed cho workflow check-then-act và gây lost update/oversell.
- Tưởng Repeatable Read là Serializable trong mọi database và bỏ sót write skew.
- Tăng isolation toàn hệ thống làm throughput giảm và deadlock/abort tăng.
- Không retry serialization failure nên user thấy lỗi ngẫu nhiên dưới tải cao.
- Test chỉ chạy tuần tự nên không bắt được anomaly concurrency.
- Behavior khác nhau giữa database engine làm migration DB tạo bug mới.

## Khi nào chưa cần hoặc dễ over-engineer

- CRUD đơn giản một statement với constraint rõ thường không cần isolation đặc biệt.
- Không nên tăng isolation trước khi xác định invariant/race condition cụ thể.
- Không nên dùng transaction dài/isolation cao cho report lớn nếu có thể dùng snapshot/reporting path riêng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Transaction]] vì isolation level chỉ có ý nghĩa trong transaction/concurrency.
- [[Read Committed]] vì đây là mức isolation phổ biến/default trong nhiều database.
- [[Repeatable Read]] vì đây là mức mạnh hơn và hay gây nhầm với Serializable.
- [[ACID]] vì Isolation là một phần của ACID.
- [[Database Lock]] vì lock/conflict behavior phụ thuộc isolation và engine.

## Liên quan rộng

- Database reliability
- Backend concurrency
- Data correctness
- MVCC

## Keywords / Từ khóa tìm kiếm

- Isolation Level
- transaction isolation
- mức cô lập giao dịch
- Read Committed
- Repeatable Read
- Serializable
- dirty read
- non-repeatable read
- phantom read
- lost update
- write skew
- MVCC
- serialization failure
- isolation level debugging

## Source trace

- PostgreSQL transaction isolation documentation
- SQL standard isolation levels
- Database System Concepts
