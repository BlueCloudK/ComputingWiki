# Lost Update

Aliases: Lost Update, lost update anomaly

Type: Database Internals

## Context / Ngữ cảnh

Lost Update xuất hiện khi hai transaction hoặc request cùng đọc một giá trị cũ, cùng tính toán thay đổi, rồi update sau ghi đè update trước mà không phát hiện conflict.

## Boundary / Ranh giới

### Nó là gì

Lost Update là concurrency anomaly trong đó một thay đổi hợp lệ bị mất vì write sau ghi đè write trước dựa trên state đã stale.

### Nó không phải là gì

Lost Update không chỉ là lỗi UI submit hai lần. Gốc vấn đề là read-modify-write không được bảo vệ bằng lock, isolation, version check hoặc atomic update.

## Core Mechanism / Cơ chế lõi

Transaction A và B đọc cùng version của row. A update và commit. B vẫn dùng value cũ để tính update rồi commit sau, khiến kết quả của A bị ghi đè hoặc không còn phản ánh trong state cuối.

## Project Role / Vai trò trong dự án

Dùng node này khi debug số dư, tồn kho, counter, quota, booking, form edit hoặc bất kỳ dữ liệu nào có nhiều writer đồng thời.

## Output / Artifact nên có

- Timeline hai transaction/request
- Isolation level hiện tại
- Update statement / write path
- Lock/version/constraint strategy
- Test concurrent update

## Decision Checklist / Câu hỏi kiểm tra

- Có read-modify-write trên cùng row/resource không?
- Nhiều request có thể update cùng lúc không?
- Update có atomic ở database không?
- Có optimistic version check hoặc lock không?
- Test có mô phỏng concurrent writer không?

## Failure Modes / Cách nó gây lỗi

- Counter bị hụt khi nhiều request tăng cùng lúc.
- Form edit sau ghi đè field người khác vừa sửa.
- Inventory/booking bị sai vì update stale.
- Isolation level thấp không phát hiện conflict.
- Retry không kiểm tra version làm ghi đè tiếp.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu chỉ có một writer hoặc update độc lập có thể chưa cần cơ chế conflict phức tạp.
- Không nên dùng lock nặng nếu atomic update hoặc optimistic concurrency đủ giải quyết.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Transaction]] vì lost update xảy ra trong tương tác transaction/write path.
- [[Isolation Level]] vì isolation quyết định conflict có bị phát hiện/chặn không.
- [[Read Phenomena]] vì lost update là một hiện tượng concurrency cần nhận diện.
- [[Database Lock]] vì lock có thể ngăn write ghi đè nhau.

## Liên quan rộng

- Optimistic concurrency control
- Atomic update
- Version column

## Keywords / Từ khóa tìm kiếm

- Lost Update
- lost update anomaly
- concurrent update
- stale write
- optimistic locking
- read modify write
- lost update debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
- Designing Data-Intensive Applications
