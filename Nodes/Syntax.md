# Syntax

Aliases: grammar, cú pháp

Type: Computer Foundation

## Context / Ngữ cảnh

Syntax xuất hiện khi source code cần có hình dạng hợp lệ để compiler hoặc interpreter đọc được. Nó là lớp đầu tiên khiến code "đúng dạng" trước khi xét code có nghĩa đúng hay không.

## Boundary / Ranh giới

### Nó là gì

Syntax là luật cấu trúc của chương trình: token, keyword, expression, statement, block và cách chúng được sắp xếp hợp lệ.

### Nó không phải là gì

Nó không phải là semantics. Code đúng syntax vẫn có thể sai nghĩa, sai type, sai logic hoặc gây lỗi runtime.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là parsing source text thành cấu trúc mà toolchain hiểu được. Syntax error xảy ra khi text không khớp grammar của language.

## Project Role / Vai trò trong dự án

Syntax ảnh hưởng readability, formatter, linting và lỗi build rất sớm. Khi debug, syntax giúp phân biệt lỗi "máy không đọc được code" với lỗi behavior sau khi code đã được đọc.

## Output / Artifact nên có

- Code hợp lệ theo grammar của language
- Formatter/linter rule nếu syntax style ảnh hưởng readability
- Note về syntax edge case dễ gây hiểu nhầm

## Decision Checklist / Câu hỏi kiểm tra

- Code có parse được theo grammar của language không?
- Syntax này đang biểu diễn expression, declaration hay control flow?
- Formatter có làm rõ cấu trúc không?
- Có syntax sugar nào che logic quan trọng không?
- Lỗi hiện tại là syntax error hay semantic/type error?

## Failure Modes / Cách nó gây lỗi

- Nhầm syntax sugar với behavior thật
- Fix syntax nhưng bỏ qua semantic bug
- Code parse được nhưng format làm người đọc hiểu sai precedence/scope
- Tooling khác version grammar gây lỗi build lệch môi trường

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần phân tích grammar nếu chỉ đọc code bình thường
- Dễ over-engineer nếu tranh luận syntax style thay vì behavior hoặc maintainability

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Programming Language]] vì syntax là mặt chữ của language
- [[Compiler]] vì compiler phải parse syntax trước khi kiểm tra sâu hơn
- [[Interpreter]] vì interpreter cũng cần đọc syntax hoặc representation tương đương
- [[Semantics]] vì syntax hợp lệ mới là đầu vào để xét nghĩa

## Liên quan rộng

- Parser
- Formatter
- Linter

## Source trace

- Computer Foundations Map Ch09
- Crafting Interpreters
