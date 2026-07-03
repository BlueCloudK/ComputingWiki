# Lexer

Aliases: lexical analyzer, scanner, bộ phân tích từ vựng

Type: Compiler / Interpreter

## Context / Ngữ cảnh

Lexer là bước đầu trong nhiều compiler/interpreter, chuyển source text thành chuỗi token để parser xử lý tiếp.

## Boundary / Ranh giới

### Nó là gì

Lexer nhận ký tự thô và nhận diện token như identifier, keyword, operator, literal, comment hoặc whitespace theo rule của ngôn ngữ.

### Nó không phải là gì

Nó không hiểu toàn bộ cấu trúc chương trình và không quyết định semantic như type, scope hoặc control flow.

## Core Mechanism / Cơ chế lõi

Lexer đọc source theo state machine hoặc regex-like rules, gom ký tự thành token, giữ vị trí dòng/cột và báo lỗi nếu gặp ký tự không hợp lệ.

## Project Role / Vai trò trong dự án

Node này giúp hiểu lỗi syntax sớm, formatter/linter, highlighter, parser bug và cách language tooling tách text thành unit có nghĩa.

## Output / Artifact nên có

- Token stream
- Token type list cho language
- Lexical error kèm source location

## Decision Checklist / Câu hỏi kiểm tra

- Token boundary có xử lý string, comment và escape đúng không?
- Keyword được phân biệt với identifier ở bước nào?
- Lexer có giữ source location đủ để báo lỗi tốt không?
- Whitespace có meaningful với language này không?

## Failure Modes / Cách nó gây lỗi

- Escape/string literal bị cắt sai làm parser báo lỗi lệch chỗ
- Comment hoặc whitespace meaningful bị bỏ nhầm
- Token location sai làm diagnostic khó debug

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần lexer riêng nếu chỉ parse format rất nhỏ bằng parser/library có sẵn
- Dễ over-engineer nếu viết full lexer cho DSL chưa ổn định về syntax

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Parser]] vì parser tiêu thụ token stream từ lexer
- [[Syntax]] vì lexical rule là phần thấp của syntax

## Liên quan rộng

- Compiler pipeline
- Language tooling
- Static analysis

## Keywords / Từ khóa tìm kiếm

- Lexer
- lexical analyzer
- scanner
- tokenization
- token stream
- lexical analysis
- bộ phân tích từ vựng
- tách token

## Source trace

- Crafting Interpreters / Scanning
- Engineering a Compiler / Lexical Analysis
