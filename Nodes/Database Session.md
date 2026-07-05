# Database Session

Aliases: Database Session, DB session

Type: Database Internals

## Context / Ngữ cảnh

Database Session xuất hiện khi client/app mở kết nối logic tới database và giữ trạng thái như transaction, prepared statement, temp table, setting hoặc lock trong phạm vi session.

## Boundary / Ranh giới

### Nó là gì

Database Session là context làm việc giữa client connection và database backend, nơi database theo dõi state của connection đó trong thời gian nó sống.

### Nó không phải là gì

Database Session không giống user login session của web app. Nó là session ở tầng database connection/runtime.

## Core Mechanism / Cơ chế lõi

Client lấy connection từ pool hoặc mở mới. Database tạo session/backend process/thread, nhận query, giữ transaction state, setting, cursor, temp object và release khi connection đóng hoặc reset.

## Project Role / Vai trò trong dự án

Dùng node này khi debug connection pool, idle transaction, session setting leak, lock giữ lâu, temp table, prepared statement hoặc query behavior khác nhau giữa request.

## Output / Artifact nên có

- Session/connection list
- Current transaction state
- Session settings
- Locks held by session
- Pool reset/cleanup rule

## Decision Checklist / Câu hỏi kiểm tra

- Session này đến từ app/pool nào?
- Có transaction đang mở không?
- Session giữ lock hoặc temp object gì?
- Setting/session variable có leak qua request không?
- Pool có reset session trước khi reuse không?

## Failure Modes / Cách nó gây lỗi

- Idle in transaction giữ lock và version cũ.
- Session setting leak làm request sau chạy khác.
- Connection pool reuse session bẩn.
- Prepared statement/temp table tích tụ.
- App quên close/release connection làm pool cạn.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ ít connection có thể chỉ cần connection pooling cơ bản.
- Không nên debug session sâu nếu lỗi thật nằm ở query plan hoặc network.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Connection Pooling]] vì pool quản lý lifecycle database session/connection.
- [[Transaction]] vì transaction state nằm trong session.
- [[Database Lock]] vì session có thể giữ lock.
- [[Temporary Table]] vì temp table thường scoped theo session.

## Liên quan rộng

- Connection lifecycle
- Session state
- Idle transaction

## Keywords / Từ khóa tìm kiếm

- Database Session
- DB session
- database connection session
- idle in transaction
- session settings
- connection pool
- database session debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
