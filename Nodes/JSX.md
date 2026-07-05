# JSX

Aliases: JSX, JavaScript XML, jsx

Type: Frontend Framework

## Context / Ngữ cảnh

JSX xuất hiện khi frontend dùng cú pháp giống HTML bên trong JavaScript để mô tả UI component. Nó phổ biến trong React và cũng được nhiều toolchain frontend hỗ trợ.

## Boundary / Ranh giới

### Nó là gì

JSX là syntax extension được transform thành JavaScript function call hoặc runtime instruction tạo UI element. Nó giúp đặt markup gần component logic, props và state.

### Nó không phải là gì

JSX không phải HTML thật và không tự chạy trực tiếp trên browser nếu chưa được transform. Nó cũng không phải template engine server-side, dù nhìn giống template.

## Core Mechanism / Cơ chế lõi

Build tool như Babel, SWC, esbuild hoặc framework compiler parse JSX rồi chuyển thành JavaScript. Expression trong `{}` chạy theo JavaScript semantics. Props, children, event handler và conditional rendering đều trở thành data/function call cho framework xử lý.

## Project Role / Vai trò trong dự án

JSX là node cần mở khi debug render lỗi, prop truyền sai, conditional UI, list key hoặc build transform frontend. Nó giúp tách lỗi syntax/compile khỏi lỗi state, component và browser runtime.

## Output / Artifact nên có

- Component code dùng JSX rõ props, children và event
- Build config hỗ trợ JSX transform
- Convention về key, conditional render, fragment và component naming
- Test/component story cho UI behavior quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- File có được build tool transform JSX không?
- Expression trong JSX có làm render khó đoán không?
- List render có key ổn định không?
- Dữ liệu hiển thị có đi qua cơ chế escape/sanitize của framework không?
- Conditional render có cover loading/error/empty state không?

## Failure Modes / Cách nó gây lỗi

- Quên key trong list làm UI state nhảy sai.
- Dùng expression phức tạp làm component khó đọc.
- Nhầm attribute hoặc event name theo framework.
- JSX transform config sai làm build fail.
- Dùng escape hatch render HTML trực tiếp làm tăng risk nếu dữ liệu không sạch.

## Khi nào chưa cần hoặc dễ over-engineer

- Trang tĩnh nhỏ có thể dùng HTML template đơn giản.
- Không nên nhét nhiều business logic trực tiếp trong JSX.
- Không nên dùng render HTML trực tiếp nếu text render bình thường đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[React]] vì JSX là cú pháp rất phổ biến trong React component.
- [[JavaScript]] vì JSX expression vẫn chạy theo JavaScript semantics.
- [[Component]] vì JSX thường mô tả render output của component.
- [[Babel]] vì Babel thường transform JSX trong toolchain.
- [[SWC]] vì SWC cũng thường transform JSX/TSX.

## Liên quan rộng

- UI rendering
- Frontend build
- Template syntax
- Component authoring

## Keywords / Từ khóa tìm kiếm

- JSX
- JavaScript XML
- jsx
- JSX transform
- TSX
- JSX props
- JSX children
- conditional rendering
- list key
- JSX debugging

## Source trace

- React documentation
- Babel JSX documentation
