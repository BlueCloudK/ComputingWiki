# Relational Algebra

Aliases: relational algebra, đại số quan hệ

Type: Data / Database

## Bản chất

Relational Algebra liên quan tới cách dữ liệu được mô hình hóa, lưu, truy vấn, giữ nhất quán và thay đổi theo thời gian. Trong dự án thật, data issue thường không chỉ là code bug mà là schema, relationship, transaction, migration hoặc query không được nghĩ kỹ. Nó nối với các phần liên quan như [[Relational Model]], [[Query]] và nhóm quyết định quanh relational algebra.

## Dùng trong dự án để làm gì

Relational Algebra ảnh hưởng tới database design, migration, audit/history, performance và khả năng debug dữ liệu sai. Nó giúp chọn model, constraint, index hoặc transaction boundary trước khi dữ liệu thật trở nên khó sửa.

## Khi nào cần quan tâm

- Thiết kế schema/model hoặc thay đổi field/relationship
- Dữ liệu sai, thiếu, trùng, inconsistent hoặc migrate khó
- Query chậm, index thiếu hoặc transaction lock bất thường
- Cần backup, audit trail, history hoặc rollback dữ liệu

## Output / artifact nên có

- Schema/model hoặc migration note rõ thay đổi dữ liệu
- Constraint/index/transaction decision nếu có ảnh hưởng consistency/performance
- Checklist backup, audit hoặc data validation cho dữ liệu quan trọng

## Checklist kiểm tra

- Schema có biểu diễn đúng relationship và cardinality không?
- Migration có plan rollback/backfill và kiểm tra dữ liệu sau chạy không?
- Transaction boundary có đủ giữ consistency không?
- Query chính có index và baseline performance chưa?
- Dữ liệu quan trọng có backup/history/audit đủ truy vết không?

## Lỗi / rủi ro thường gặp

- Schema sai làm code phải vá vòng quanh
- Migration mất dữ liệu hoặc gây downtime
- Transaction/consistency yếu làm dữ liệu lệch giữa service
- Query thiếu index làm production chậm khi data tăng

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần model phức tạp khi dữ liệu nhỏ, ít quan hệ và dễ migrate
- Dễ over-engineer nếu normalize/partition/cache trước khi có query pattern thật

## Gồm những gì

- Chưa tách nhánh

## Liên quan

- [[Relational Model]]
- [[Query]]

## Source trace

- Database Systems Map / Ch02.6
