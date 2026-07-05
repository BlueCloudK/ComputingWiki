# REPL

Aliases: REPL, Read-Eval-Print Loop

Type: Programming Languages Deep

## Context / Ngữ cảnh

REPL xuất hiện khi developer muốn thử code, kiểm tra expression, debug API nhỏ hoặc học behavior ngôn ngữ ngay trong phiên tương tác.

## Boundary / Ranh giới

### Nó là gì

REPL là vòng lặp Read-Eval-Print: đọc input, đánh giá code, in kết quả rồi chờ input tiếp theo.

### Nó không phải là gì

REPL không phải môi trường production và không thay thế test suite. Nó tốt cho thử nhanh nhưng dễ thiếu reproducibility.

## Core Mechanism / Cơ chế lõi

Runtime đọc dòng lệnh hoặc block code, parse/evaluate trong context hiện tại, lưu biến/session state, in result hoặc error, rồi tiếp tục nhận input mới.

## Project Role / Vai trò trong dự án

Dùng node này khi cần thử API/library, kiểm tra semantics, debug data nhỏ hoặc tạo reproduction trước khi viết test chính thức.

## Output / Artifact nên có

- Reproduction snippet
- Input/output quan trọng
- Note về runtime/version
- Test case chính thức nếu behavior cần giữ lại

## Decision Checklist / Câu hỏi kiểm tra

- REPL đang chạy runtime/version nào?
- State trong phiên có ảnh hưởng kết quả không?
- Snippet có thể đưa vào test không?
- Kết quả có phụ thuộc environment không?

## Failure Modes / Cách nó gây lỗi

- Tin vào kết quả REPL nhưng production runtime khác.
- Session state cũ làm kết quả lệch.
- Snippet thử nhanh không được chuyển thành test.
- Debug ở REPL bỏ qua config thật của project.

## Khi nào chưa cần hoặc dễ over-engineer

- Logic đã có test rõ thì không cần dựa vào REPL.
- Không nên dùng REPL làm source of truth cho behavior production.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Runtime]] vì REPL chạy trong runtime cụ thể.
- [[Unit Test]] vì snippet ổn định nên chuyển thành test.
- [[CLI Tool]] vì REPL thường là command-line interaction.

## Liên quan rộng

- Interactive programming
- Debugging
- Language semantics

## Keywords / Từ khóa tìm kiếm

- REPL
- Read-Eval-Print Loop
- interactive shell
- runtime session
- code snippet
- REPL debugging

## Source trace

- Crafting Interpreters
- Python documentation
- Node.js documentation
