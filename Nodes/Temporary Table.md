# Temporary Table

Aliases: Temporary Table, temp table

Type: Database Internals

## Context / Ngữ cảnh

Temporary Table xuất hiện khi query, procedure hoặc ETL job cần lưu dữ liệu trung gian trong phạm vi session/transaction để xử lý tiếp.

## Boundary / Ranh giới

### Nó là gì

Temporary Table là bảng tạm được tạo để chứa dữ liệu trung gian, thường chỉ sống trong session hoặc transaction tùy database.

### Nó không phải là gì

Temporary Table không phải bảng domain lâu dài. Nếu logic nghiệp vụ cần dữ liệu bền vững, dùng bảng chính thức với schema/migration rõ hơn.

## Core Mechanism / Cơ chế lõi

Database tạo table tạm trong namespace/session riêng, insert dữ liệu trung gian, query/join tiếp, rồi tự drop hoặc được drop thủ công khi hết scope.

## Project Role / Vai trò trong dự án

Dùng node này khi debug report query, batch job, migration script, stored procedure hoặc query plan dùng dữ liệu trung gian lớn.

## Output / Artifact nên có

- Temporary table schema
- Scope/lifetime rule
- Index nếu dữ liệu lớn
- Cleanup/drop rule
- Query plan note

## Decision Checklist / Câu hỏi kiểm tra

- Table tạm sống trong session hay transaction?
- Dữ liệu có lớn tới mức cần index không?
- Có cleanup rõ không?
- Có thể thay bằng CTE/subquery không?
- Concurrent run có đụng tên hoặc lock không?

## Failure Modes / Cách nó gây lỗi

- Temp table quá lớn làm đầy temp storage.
- Thiếu index làm join chậm.
- Scope hiểu sai làm table biến mất sớm hoặc tồn tại lâu.
- Concurrent job đụng tên nếu dùng global temp table.
- Dùng temp table để che query design phức tạp quá mức.

## Khi nào chưa cần hoặc dễ over-engineer

- Query nhỏ có thể dùng CTE/subquery đủ rõ.
- Không nên tạo temp table nếu chỉ lưu vài dòng không tái sử dụng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Query Plan]] vì temp table có thể thay đổi execution plan.
- [[Database Migration]] vì migration script đôi khi dùng temp table để chuyển dữ liệu.
- [[Transaction]] vì scope/lifetime có thể gắn với transaction.
- [[Index]] vì temp table lớn có thể cần index tạm.

## Liên quan rộng

- Intermediate result
- Batch processing
- SQL procedure

## Keywords / Từ khóa tìm kiếm

- Temporary Table
- temp table
- SQL temp table
- temporary table scope
- temp storage
- temporary table debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
