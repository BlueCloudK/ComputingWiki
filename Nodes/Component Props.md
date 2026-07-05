# Component Props

Aliases: Component Props, props

Type: Frontend Framework

## Context / Ngữ cảnh

Component Props xuất hiện khi parent component cần truyền dữ liệu, callback hoặc configuration xuống child component trong UI tree.

## Boundary / Ranh giới

### Nó là gì

Component Props là input contract của component: dữ liệu và callback mà component nhận từ bên ngoài để render hoặc phát hành động lên parent.

### Nó không phải là gì

Props không phải global state và không nên bị child mutate trực tiếp. Nếu dữ liệu cần thay đổi, component nên emit callback/action hoặc dùng state boundary rõ.

## Core Mechanism / Cơ chế lõi

Parent truyền prop vào child. Child đọc prop để render hoặc gọi callback khi user action xảy ra. Khi prop đổi, framework render/update component theo reactivity/model của nó.

## Project Role / Vai trò trong dự án

Dùng node này khi debug data flow parent-child, component reuse, props drilling, callback contract, controlled/uncontrolled component hoặc props gây rerender dư.

## Output / Artifact nên có

- Props interface/schema
- Required/optional/default value
- Callback contract
- Controlled/uncontrolled decision
- Component test/story nếu quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Prop này là data, config hay callback?
- Prop có required/default rõ không?
- Child có mutate prop không?
- Prop drilling có quá sâu không?
- Callback có tên và payload rõ không?

## Failure Modes / Cách nó gây lỗi

- Prop contract mơ hồ làm component khó reuse.
- Child mutate prop trực tiếp làm data flow rối.
- Props object/function tạo mới liên tục gây rerender dư.
- Controlled/uncontrolled state bị trộn.
- Callback payload không rõ làm parent xử lý sai.

## Khi nào chưa cần hoặc dễ over-engineer

- Component chỉ dùng nội bộ một nơi có thể giữ props đơn giản.
- Không nên tạo props API quá tổng quát trước khi có reuse thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Component]] vì props là input contract của component.
- [[React]] vì props là cơ chế chính trong React component.
- [[Vue Component]] vì Vue component cũng có props/emits contract.
- [[Global State]] vì props drilling quá sâu có thể báo hiệu cần state boundary khác.

## Liên quan rộng

- Parent-child data flow
- Controlled component
- Callback props

## Keywords / Từ khóa tìm kiếm

- Component Props
- props
- props contract
- callback prop
- props drilling
- controlled component
- component props debugging

## Source trace

- React documentation
- Vue documentation
