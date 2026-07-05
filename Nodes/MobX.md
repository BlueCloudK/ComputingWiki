# MobX

Aliases: MobX

Type: Frontend Framework

## Context / Ngữ cảnh

MobX xuất hiện khi frontend app cần state management theo hướng reactive observable, nơi UI tự cập nhật khi state được quan sát thay đổi.

## Boundary / Ranh giới

### Nó là gì

MobX là state management library dựa trên observable state, computed value và action. Component tự phản ứng với phần state mà nó đọc.

### Nó không phải là gì

MobX không phải database và không phải mọi app React đều cần. Nó cũng khác Redux ở chỗ không bắt buộc action/reducer flow tường minh như Redux.

## Core Mechanism / Cơ chế lõi

State được đánh dấu observable. Component hoặc reaction đọc state sẽ trở thành observer. Khi action thay đổi state, MobX tự tính dependency và trigger update những observer liên quan.

## Project Role / Vai trò trong dự án

Dùng node này khi debug UI không update, update quá nhiều, state mutation khó trace hoặc app cần reactive shared state.

## Output / Artifact nên có

- Store/domain state structure
- Observable/computed/action convention
- Observer boundary
- Debug rule cho reaction/update
- Test cho state behavior quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- State nào là observable?
- Component nào đang observe state?
- Computed value có pure không?
- Action có gom mutation rõ không?
- Có cần trace reaction khi debug không?

## Failure Modes / Cách nó gây lỗi

- Mutation ngoài action làm flow khó trace.
- Observable quá rộng làm update khó đoán.
- Component không observe đúng nên UI không update.
- Computed có side effect làm behavior rối.
- State implicit quá nhiều khiến debug khó hơn Redux-style flow.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ với local state hoặc server state cache đơn giản chưa cần MobX.
- Không nên dùng MobX nếu team cần event/action log tường minh hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[State Management]] vì MobX là thư viện quản lý state.
- [[React]] vì MobX thường dùng cùng React component.
- [[Component]] vì component observe state để rerender.
- [[RxJS]] vì cả hai đều liên quan tư duy reactive, dù cơ chế khác nhau.

## Liên quan rộng

- Reactive state
- Observable model
- Frontend architecture

## Keywords / Từ khóa tìm kiếm

- MobX
- observable state
- computed value
- action
- reaction
- observer component
- MobX debugging

## Source trace

- MobX documentation
- React documentation
