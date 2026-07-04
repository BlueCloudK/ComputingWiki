# Repeatable Read

Aliases: repeatable read isolation, đọc lặp lại

Type: Database Systems

## Context / Ngữ cảnh

Repeatable Read xuất hiện khi transaction cần view ổn định hơn Read Committed, đặc biệt khi nhiều statement trong cùng transaction phải đọc cùng dữ liệu mà không bị thay đổi bởi commit từ transaction khác. Nó thường liên quan tới report, consistency check, update workflow và concurrency bug.

## Boundary / Ranh giới

### Nó là gì

Repeatable Read là isolation level đảm bảo row đã đọc trong transaction không thay đổi khi đọc lại trong cùng transaction. Trong nhiều database dùng MVCC, transaction nhìn một snapshot ổn định tại thời điểm transaction bắt đầu, nhưng chi tiết phantom read và conflict behavior phụ thuộc database implementation.

### Nó không phải là gì

Repeatable Read không luôn đồng nghĩa Serializable. Nó không tự chứng minh mọi invariant đa-row đều an toàn trong mọi database. Một số anomaly như write skew có thể vẫn xảy ra tùy implementation. Nếu nghiệp vụ cần serial order tuyệt đối, cần cân nhắc Serializable, explicit lock hoặc constraint.

## Core Mechanism / Cơ chế lõi

Database tạo snapshot cho transaction hoặc bảo vệ row đã đọc để lần đọc sau thấy dữ liệu nhất quán hơn. Transaction khác vẫn có thể commit thay đổi, nhưng transaction hiện tại không nhất thiết nhìn thấy thay đổi đó. Với write conflict, database có thể block, abort hoặc yêu cầu retry tùy engine và isolation semantics.

## Project Role / Vai trò trong dự án

Repeatable Read là node cần mở khi transaction nhiều bước cần đọc dữ liệu nhất quán, report cần snapshot ổn định, hoặc Read Committed gây non-repeatable read. Nó giúp team chọn giữa isolation mạnh hơn, explicit lock, atomic update, constraint hoặc thiết kế lại workflow để tránh giữ transaction quá lâu.

## Output / Artifact nên có

- Isolation decision note cho transaction cần snapshot ổn định
- Concurrency test cho non-repeatable read, phantom/write skew nếu use case nhạy cảm
- Retry policy cho serialization/write conflict nếu database có thể abort transaction
- Transaction duration budget để tránh giữ snapshot/lock quá lâu
- Notes về behavior cụ thể của database đang dùng: PostgreSQL, MySQL/InnoDB, SQL Server...

## Decision Checklist / Câu hỏi kiểm tra

- Transaction có cần đọc lại cùng dữ liệu và thấy kết quả ổn định không?
- Use case có invariant đa-row hoặc predicate-based check không?
- Database implementation của Repeatable Read có chặn phantom/write skew theo cách team mong đợi không?
- Transaction có thể kéo dài lâu và giữ snapshot/lock gây bloat/contention không?
- Khi transaction bị abort do conflict, app có retry an toàn không?
- Có thể dùng unique/check constraint hoặc atomic update thay vì isolation cao hơn không?
- Report/snapshot query có cần tách khỏi write transaction không?

## Failure Modes / Cách nó gây lỗi

- Developer tưởng Repeatable Read là Serializable và bỏ sót write skew/invariant race.
- Transaction dài giữ snapshot lâu làm MVCC cleanup khó hơn hoặc tăng storage/bloat.
- Conflict xảy ra dưới tải cao nhưng app không retry nên user thấy lỗi ngẫu nhiên.
- Isolation mạnh hơn làm lock/wait tăng và giảm throughput nếu dùng không đúng chỗ.
- Behavior khác nhau giữa PostgreSQL/MySQL làm test môi trường này pass nhưng môi trường khác lỗi.
- Report đọc snapshot cũ quá lâu và không phản ánh dữ liệu mới như user mong đợi.

## Khi nào chưa cần hoặc dễ over-engineer

- CRUD ngắn, một statement hoặc đã có constraint/atomic update thường không cần Repeatable Read.
- Không nên tăng isolation toàn hệ thống nếu chỉ vài transaction cần view ổn định.
- Không nên dùng transaction dài để tạo report lớn nếu snapshot/staleness có thể xử lý bằng read replica hoặc job riêng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Isolation Level]] vì Repeatable Read là một isolation level mạnh hơn Read Committed.
- [[Read Committed]] vì đây là mức thường được so sánh khi cần view ổn định hơn.
- [[ACID]] vì Repeatable Read liên quan tới Isolation trong ACID.
- [[Database Transaction]] vì behavior chỉ có ý nghĩa trong phạm vi transaction.
- [[Database Lock]] vì conflict/lock behavior phụ thuộc engine và isolation.

## Liên quan rộng

- MVCC
- Concurrency control
- Data correctness
- Reporting snapshot

## Keywords / Từ khóa tìm kiếm

- Repeatable Read
- repeatable read isolation
- đọc lặp lại
- transaction snapshot
- snapshot isolation
- non-repeatable read
- phantom read
- write skew
- MVCC
- serializable isolation
- transaction retry
- isolation anomaly
- repeatable read debugging

## Source trace

- PostgreSQL transaction isolation documentation
- MySQL InnoDB transaction isolation documentation
- Database System Concepts
