# Babel

Aliases: Babel

Type: Frameworks and Tools

## Context / Ngữ cảnh

Babel xuất hiện khi JavaScript project cần transform syntax mới, JSX hoặc plugin compile để chạy trên runtime/browser mục tiêu.

## Boundary / Ranh giới

### Nó là gì

Babel là JavaScript compiler/transpiler dựa trên parser, AST, plugin và preset. Nó chuyển source code thành output JavaScript phù hợp target.

### Nó không phải là gì

Babel không phải runtime JavaScript và không phải type checker đầy đủ. Nếu dùng TypeScript, vẫn cần type check riêng nếu muốn bắt lỗi type.

## Core Mechanism / Cơ chế lõi

Babel parse source thành AST, áp plugin/preset transform, rồi emit JavaScript và sourcemap. Config quan trọng gồm target browser/runtime, module format, plugin order và preset.

## Project Role / Vai trò trong dự án

Dùng node này khi debug JSX transform, syntax support, plugin conflict, sourcemap hoặc output build không chạy trên runtime mục tiêu.

## Output / Artifact nên có

- Babel config
- Preset/plugin list
- Target runtime/browser
- Sourcemap decision
- Type check step nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Babel đang transform syntax nào?
- Target runtime là gì?
- Plugin/preset có thứ tự đúng không?
- Có type check riêng không?
- Output module format có khớp bundler/runtime không?

## Failure Modes / Cách nó gây lỗi

- Transform pass nhưng type error không bị bắt.
- Plugin order sai làm output lạ.
- Target sai làm runtime không hiểu syntax.
- Sourcemap lệch làm debug khó.
- ESM/CJS output không khớp consumer.

## Khi nào chưa cần hoặc dễ over-engineer

- Toolchain framework đã xử lý transform thì ít cần chỉnh Babel trực tiếp.
- Không nên thêm plugin nếu chưa có syntax/use case rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì Babel transform JavaScript.
- [[JSX]] vì Babel thường dùng để transform JSX.
- [[Frontend Framework]] vì nhiều frontend toolchain dùng compiler/transform.
- [[SWC]] vì SWC là lựa chọn thay thế trong nhiều pipeline.
- [[CI]] vì build transform cần chạy ổn định trong pipeline.

## Liên quan rộng

- Compiler tooling
- Transpilation
- Build pipeline

## Keywords / Từ khóa tìm kiếm

- Babel
- Babel preset
- Babel plugin
- JavaScript compiler
- JSX transform
- sourcemap
- Babel debugging

## Source trace

- Babel documentation
