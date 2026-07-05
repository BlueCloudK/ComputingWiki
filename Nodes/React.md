# React

Aliases: React, React.js

Type: Frontend Framework

## Context / Ngữ cảnh

React là thư viện UI dùng để xây giao diện bằng component.

## Boundary / Ranh giới

### Nó là gì

React tổ chức UI thành component, props và state.

### Nó không phải là gì

React không phải backend framework hoặc database.

## Core Mechanism / Cơ chế lõi

Component nhận dữ liệu, render UI và cập nhật khi state thay đổi.

## Project Role / Vai trò trong dự án

Dùng node này khi cần hiểu hoặc debug UI component.

## Output / Artifact nên có

- Component tree
- State ownership map
- Test cho flow chính

## Decision Checklist / Câu hỏi kiểm tra

- State nằm ở đâu?
- Component nhận props gì?
- Component có quá lớn không?

## Failure Modes / Cách nó gây lỗi

- State đặt sai chỗ.
- Component quá lớn.
- Render list thiếu key ổn định.

## Khi nào chưa cần hoặc dễ over-engineer

- Trang tĩnh nhỏ chưa cần React.

## Gồm những gì

- [[JSX]]
- [[useRef]]

## Nối mạnh

- [[Frontend Framework]] vì React thuộc nhóm frontend framework/library.
- [[Component]] vì component là đơn vị chính.
- [[State Management]] vì React app phụ thuộc state ownership.

## Liên quan rộng

- UI architecture
- Browser runtime

## Keywords / Từ khóa tìm kiếm

- React
- React.js
- React component
- React state
- React props

## Source trace

- React documentation
