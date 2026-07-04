# Read Committed

Aliases: read committed isolation, cô lập read committed

Type: Database Systems

## Context / Ngữ cảnh

Read Committed xuất hiện khi database transaction cần tránh dirty read nhưng vẫn cho phép mỗi statement nhìn snapshot mới nhất của dữ liệu đã commit. Đây là isolation level phổ biến/default trong nhiều database và thường dùng cho workload backend thông thường.

## Boundary / Ranh giới

### Nó là gì

Read Committed là isolation level trong đó một statement chỉ đọc dữ liệu đã được commit trước khi statement đó bắt đầu chạy. Nếu cùng transaction chạy hai SELECT ở hai thời điểm khác nhau, chúng có thể thấy kết quả khác nhau nếu transaction khác commit ở giữa.

### Nó không phải là gì

Read Committed không đảm bảo transaction có một view ổn định xuyên suốt toàn bộ transaction. Nó không ngăn non-repeatable read, phantom read hoặc một số race condition nghiệp vụ. Nếu use case cần snapshot ổn định hoặc invariant phức tạp, cần cân nhắc Repeatable Read, Serializable, lock rõ ràng hoặc constraint.

## Core Mechanism / Cơ chế lõi

Ở database dùng MVCC, mỗi statement trong Read Committed lấy snapshot dữ liệu committed tại thời điểm statement bắt đầu. Update/delete có thể phải chờ row đang bị transaction khác lock. Sau khi lock được giải phóng, database kiểm tra lại row version/condition theo rule của implementation.

## Project Role / Vai trò trong dự án

Read Committed là node cần mở khi debug race condition, double-submit, lost update, dữ liệu đọc lần hai khác lần một hoặc transaction tưởng “đã khóa logic” nhưng thực ra mỗi query nhìn một snapshot khác. Nó giúp team quyết định nơi cần lock, constraint hoặc isolation mạnh hơn.

## Output / Artifact nên có

- Isolation decision note cho transaction quan trọng
- Test case concurrency cho non-repeatable read, lost update hoặc check-then-act race
- Query/transaction boundary: statement nào đọc, statement nào ghi, thời điểm commit
- Lock/constraint/idempotency strategy nếu use case cần bảo vệ invariant
- Retry strategy cho conflict nếu chuyển sang isolation cao hơn

## Decision Checklist / Câu hỏi kiểm tra

- Transaction có cần view ổn định xuyên suốt nhiều statement không?
- Có pattern check-then-act dựa trên dữ liệu có thể đổi giữa hai statement không?
- Có thể dùng constraint hoặc atomic update thay vì đọc rồi ghi không?
- Lost update có thể xảy ra nếu hai request sửa cùng row không?
- Use case này có chấp nhận non-repeatable read/phantom read không?
- Có cần `SELECT ... FOR UPDATE` hoặc isolation cao hơn không?
- Test concurrency có mô phỏng hai transaction chạy song song không?

## Failure Modes / Cách nó gây lỗi

- Một transaction đọc cùng điều kiện hai lần và thấy kết quả khác nhau.
- Check tồn kho/số dư rồi update sau đó bị transaction khác thay đổi dữ liệu ở giữa.
- Hai request đọc cùng giá trị cũ rồi ghi đè nhau, gây lost update nếu không có atomic update/lock.
- Báo cáo tạm thời thấy dữ liệu không nhất quán giữa nhiều query trong cùng transaction.
- Developer tưởng `BEGIN` tạo snapshot cố định nhưng Read Committed chỉ snapshot theo statement.
- Fix bằng cách tăng isolation nhưng không xử lý retry/lock wait làm lỗi production khác xuất hiện.

## Khi nào chưa cần hoặc dễ over-engineer

- CRUD đơn giản với constraint rõ và ít race condition thường dùng Read Committed là đủ.
- Không nên tăng toàn hệ thống lên Serializable nếu chỉ một vài transaction cần bảo vệ invariant.
- Nhiều race condition nên xử lý bằng atomic query, unique constraint hoặc explicit lock thay vì chỉ tăng isolation mù.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Isolation Level]] vì Read Committed là một isolation level phổ biến.
- [[ACID]] vì Read Committed liên quan trực tiếp tới phần Isolation trong ACID.
- [[Database Transaction]] vì behavior của Read Committed chỉ có ý nghĩa trong transaction/statement.
- [[Database Lock]] vì write conflict trong Read Committed vẫn liên quan tới lock/wait.
- [[Repeatable Read]] vì Repeatable Read là mức mạnh hơn cho view ổn định hơn.

## Liên quan rộng

- Concurrency control
- Data correctness
- MVCC
- Backend race condition

## Keywords / Từ khóa tìm kiếm

- Read Committed
- read committed isolation
- cô lập read committed
- statement snapshot
- dirty read
- non-repeatable read
- phantom read
- lost update
- MVCC
- transaction isolation
- SELECT FOR UPDATE
- check then act race
- read committed debugging

## Source trace

- PostgreSQL transaction isolation documentation
- Database System Concepts
